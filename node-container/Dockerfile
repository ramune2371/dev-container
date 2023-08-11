FROM ubuntu:latest

RUN apt update
RUN apt install -y vim curl git

# install nodejs for coc.nvim
RUN curl -fsSL https://deb.nodesource.com/setup_lts.x | bash -
RUN apt  install -y nodejs
RUN npm install -g prettier eslint typescript

# install vim plugin management tool
RUN curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim

# copy vim settings files
COPY ./vimrc /root/.vimrc
COPY ./init.vim /root/init.vim

# install the vim plugin
RUN vim +":PlugInstall" +":qa"

# install the coc nvim extensions
RUN vim -s /root/init.vim
