FROM centos:7

RUN yum -y install openssh-server

RUN useradd shahid && \
    echo "shahid:1234" | chpasswd && \
    mkdir /home/shahid/.ssh && \
    chmod 700 /home/remote_user/.ssh
	
COPY remote-key.pub /home/shahid/.ssh/authorized_keys

RUN chown shahid:shahid   -R /home/shahid && \
    chmod 600 /home/shahid/.ssh/authorized_keys

RUN ssh-keygen -A

RUN yum install mysql -y

RUN yum -y install epel-release && \
    yum -y install python-pip && \
    pip install --upgrade pip && \
    pip install awscli --upgrade


CMD /usr/sbin/sshd -D

