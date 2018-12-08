# Installed packages and tools

## System utils
* `htop`: A more informative, colorful version of `top`.
* `xsel`: Nifty CL utility to copy piped output to clipboard.
* `synaptic`: Synaptic package manager.

```bash
sudo apt-get install htop
sudo apt-get install xsel
sudo apt-get install synaptic
```

## Code utils
* `silversearcher-ag`: A fast code search tool (read: fast `grep`).
* `bazel`: Simple, easy build management (install instructions on website).
* `docker`: Portable runtimes environment ala containers.
* `golang`: Irresistible gopher.
* `pip3`: Package manager for Python 3.
* `Vundle`: Vim plugin manager. Installation instructions on website. Plugins installed/used via Vundle are listed below.
  - `vim-codefmt`: A code formatter for various languages, supporting the :FormatCode command.
* `yapf`: Yet another Python Formatter (a dependency for `vim-codefmt`).
* `buildifier`: A formatter for BUILD files (a dependency for `vim-codefmt`).
* `hugo`: Static site generator; useful for github pages.

```bash
sudo apt-get install silversearcher-ag
sudo apt-get install docker
sudo apt-get install golang
sudo apt-get install python3-pip
sudo apt-get install python3-yapf # Does not appear to help vim-codefmt
sudo apt-get install yapf3 # Works with vim-codefmt after symlink /usr/bin/yapf -> /usr/bin/yapf3

sudo snap install docker
snap install hugo --channel=extended

sudo pip3 install yapf # Does not appear to help vim-codefmt

go get github.com/bazelbuild/buildtools/buildifier
```

## Python libraries
* `matplotlib`: Matplotlib for Python3.
* `absl-py`: Abseil Python libraries from Google.

```bash
sudo apt-get install python3-matplotlib

sudo pip3 install absl-py
```

## Miscellaneous notes

### `.bazelrc` setup

```bash
build --python_path="/usr/bin/python3"
```

### `.bash_library` setup

```bash
function add_to_path_if_missing() {
    if [ ! -z "$1" ]; then
        PATH_TO_ADD=$1
        if [[ ":$PATH:" != *":$PATH_TO_ADD:"* ]]; then
            PATH="$PATH_TO_ADD:${PATH}"
        fi
    fi
}
```

### `.bash_aliases` setup

```bash
alias s="source ~/.bashrc"
alias f="cd ~/code/fiddle"
alias p="python3"
alias bb="bazel build -c opt"
alias bt="bazel test -c opt"
```

### `.bashrc_user` setup

```bash
source ~/.bash_library

# For go code.
add_to_path_if_missing $HOME/go/bin
```

**NOTE: the following section needs to be added to your ~/.bashrc** 

```bash
if [ -f ~/.bashrc_user ]; then
    . ~/.bashrc_user
fi
```
