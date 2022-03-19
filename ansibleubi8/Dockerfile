FROM redhat/ubi8:latest

RUN yum check-update
RUN yum install -y openssh-server
RUN yum install -y gcc libffi-devel python3
RUN yum install -y python3-pip
RUN yum install -y wget
RUN yum install -y sudo
RUN yum install -y iputils
RUN yum install -y less
RUN yum install -y vim-enhanced
RUN yum install -y initscripts

RUN pip3 install --upgrade pip
RUN pip3 install --upgrade virtualenv
RUN pip3 install pywinrm
RUN pip3 install requests
# 20220319.1708. Automation platform should install it by default: RUN pip3 install ansible

RUN mkdir /home/ansible
RUN useradd -ms /bin/bash ansible
RUN passwd -d ansible
RUN usermod -aG wheel ansible
RUN echo '%sudo ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers

RUN mkdir -p /etc/rc.d/sshd 
WORKDIR /etc/rd.d/sshd
RUN ssh-keygen -A

ENTRYPOINT ["/usr/sbin/sshd","-D"]
