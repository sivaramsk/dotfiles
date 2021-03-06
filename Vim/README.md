Vim
===

![Sheharyar's Vim Setup](http://i.imgur.com/kv6O42J.jpg)

[_See all dotfiles_](https://github.com/sheharyarn/dotfiles)


## Installation

### Upgrade Vim

The default `vim` by Apple sucks balls, so we're going to upgrade to the latest Vim.
First, switch over to the system `ruby` if you're using `rvm`:

```bash
rvm use system
```

Use Homebrew to install `vim`:

```bash
brew install vim --with-python3 --with-lua --with-override-system-vi
```

### Install MacVim

```bash
brew install  macvim
brew linkapps macvim
```

### Install [NeoVim](http://neovim.io/)

Let's take advantage of the Dark Features

```bash
# Install NeoVim
brew install neovim/neovim/neovim

# And the python modules (or use pip2 / pip3)
pip install neovim
```

You can also install the unofficial GUIs ([VimR](https://github.com/qvacua/vimr) /
[neovim-dot-app](https://github.com/rogual/neovim-dot-app)):

```bash
brew install rogual/neovim-dot-app/neovim-dot-app --HEAD
brew linkapps neovim-dot-app
```

<br>


## Configuration

Once everything is installed, symlink the vim dotfiles and create the required directories:

```bash
mv ~/.config/nvim ~/.config/nvim_backup
mkdir -p ~/.vim/swap ~/.vim/backups ~/.config/nvim ~/.SpaceVim.d/

ln -s ~/.dotfiles/Vim/main.vim      ~/.vimrc
ln -s ~/.dotfiles/Vim/main.vim      ~/.config/nvim/init.vim
ln -s ~/.dotfiles/Vim/spacevim.vim  ~/.SpaceVim.d/init.vim
```

<br>


## Plugins

I use _Vim-Plug_ for Plugin Management (Previously Dein & Vundle).

1. Install [Vim-Plug](https://github.com/junegunn/vim-plug)

2. Make sure your `vimrc` dotfiles are set up

3. The plugins would be auto-installed on start but you can do it manually too:

    ```bash
    nvim :PlugInstall
    ```

_(If you're using Spacevim, use its built-in plugin management system)_

<br>


### Plugins that require extra work:

 - [**Airline**](https://github.com/bling/vim-airline/)

    If you are using `vim-airline`, you need to use fonts that have been patched for
    powerline in your terminal. Here are a few patched fonts that I use in my OSX
    [Terminal Themes](https://github.com/sheharyarn/dotfiles/tree/master/OSX/Terminal):

      - [Menlo for Powerline](https://github.com/abertsch/Menlo-for-Powerline)
      - [Powerline Patched Font-Pack](https://github.com/powerline/fonts/)
      - [Nerd Patched Font-Pack](https://github.com/ryanoasis/nerd-fonts) for extra symbols

    If you don't find your desired font patched with the Powerline Icons,
    [you'll have to patch it manually](https://github.com/Lokaltog/vim-powerline/tree/develop/fontpatcher).


## Check Helath

Once you're done installing everything run `:checkhealth` to make sure all other required dependencies are installed correctly and Vim is working correctly


<br>


### SpaceVim

If you want to use SpaceVim instead of manually managing your plugins and configs, you can do that.
These dotfiles work perfectly with SpaceVim:

```bash
curl -sLf https://spacevim.org/install.sh | bash -s -- -h
```

After it is installed, make sure to enable SpaceVim at the top of `main.vim`:

```vim
let g:spacevim_enabled = 1
```

