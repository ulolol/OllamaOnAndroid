# OllamaOnAndroid
Steps to get Ollama up and running on Android Environments


# Ollama on Android using Termux

This guide provides instructions on how to build and run Ollama from source on Termux.

## Prerequisites

-   A Termux environment set up and ready to use.

## Install Dependencies

Before building Ollama, you need to install the necessary dependencies. Run the following commands in your Termux terminal:

```bash
pkg upgrade
pkg install git cmake golang
```

## Build Ollama from Source

1.  **Clone the Ollama repository:**

    ```bash
    git clone --depth 1 https://github.com/ollama/ollama.git
    ```

    This command clones the Ollama repository directly from GitHub.

2.  **Navigate to the Ollama directory:**

    ```bash
    cd ollama
    ```

    This changes the current directory to the newly cloned Ollama directory.

3.  **Generate necessary files and build the Ollama binary:**

    ```bash
    go generate ./...
    go build .
    ```

    The `go generate ./...` command generates necessary dependencies, and `go build .` builds the Ollama binary .

4.  **Run Ollama:**

    ```bash
    ./ollama serve &
    ./ollama run phi
    ```

    The `./ollama serve &` command starts the Ollama server in the background, and the second command starts the "phi" model . You can substitute "phi" with another model if needed.

## Cleanup

After the build, you may want to remove the `go` directory that was created in your home directory. This folder contains go dependencies and build files. If so, you can execute following commands:

```bash
chmod -R 700 ~/go
rm -r ~/go
```

## Move Ollama Binary to Bin (Optional)

By default, Termux does not include `~/.local/bin` in its `PATH`. If you want to be able to run Ollama directly in your terminal, you may want to move the binary to `/data/data/com.termux/files/usr/bin/` (which it is in `PATH`).

1.  **Copy the Ollama binary:**

    ```bash
    cp ollama/ollama /data/data/com.termux/files/usr/bin/
    ```

    This command copies the compiled Ollama binary `ollama` from the `ollama` folder to the `/data/data/com.termux/files/usr/bin/` directory.

Now you can simply run `ollama` in your terminal directly!

## Notes

- Make sure you have enough disk space and Ram on your Termux Environment to run ollama without issues.
- You may need to configure storage location for your model.
- You can customize steps to your needs, removing or adding steps as needed.


# Alternatively, use _proot-distro_  
You can alternatively install proot-distro and use that to install ollama on Termux using the official Ollama Install Script  

```bash
pkg install proot-distro
```

- Next, install any of the supported distro flavours. (Ubuntu is widely supported for Ollama)
  ```bash
  proot-distro list
  proot-distro install <whatever>
  ```
- Login to the distro
  ```bash
  proot-distro login <whatever>
  ```
- Run the official Ollama Install Command
- Serve Ollama
  ```bash
  ollama serve
  ```
- Open a new Tab in Termux and start using Ollama

That's it!!



