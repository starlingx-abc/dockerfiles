FROM ubuntu:18.04

ENV LC_CTYPE="en_US.UTF-8" LANG="en_US.UTF-8" LC_ALL="en_US.UTF-8" LANGUAGE="en_US:en" \
    DISPLAY=:0 \
    DEBIAN_FRONTEND=noninteractive

RUN apt-get update \
    && apt-get install -y locales ca-certificates openssh-server \
        sudo expect screen wget curl vim git net-tools inetutils-ping bridge-utils iptables \
        python3 python3-dev python3-pip python3-psycopg2 \
    && locale-gen en_US.UTF-8 \
    && update-ca-certificates \
    && sed 's/.*PasswordAuthentication.*/PasswordAuthentication yes/g' -i /etc/ssh/sshd_config \
    && sed 's/.*PermitRootLogin.*/PermitRootLogin yes/g' -i /etc/ssh/sshd_config

RUN pip3 install --upgrade \
    pip \
    kubernetes \
    bcrypt \
    flask flask_login flask_migrate flask_wtf flask_sqlalchemy \
    gunicorn

EXPOSE 22
