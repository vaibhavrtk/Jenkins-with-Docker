FROM jenkins/jenkins

USER root

# Install ansible
RUN curl -O https://bootstrap.pypa.io/get-pip.py  && \
    python get-pip.py && \
    pip install ansible --upgrade

# Install Docker
RUN apt-get update && \
    apt-get -y install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common && \
curl -fsSL https://download.docker.com/linux/$(. /etc/os-release; echo $"ID")/gpg > /tmp/dkey; apt-key add /tmp/dkey && \
add-apt-repository \
      "deb [arch=amd64] https://download.docker.com/linux/$(. /etc/os-release; echo $"ID") \
      $(lsb_release -cs) \
      stable" && \
apt-get update &&i \
apt-get -y install docker-ce docker-ce-cli containerd.io
 


# Compose	
RUN curl -L "https://github.com/docker/compose/releases/download/1.26.2/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose && chmod +x /usr/local/bin/docker-compose

#add jenkins user to docker group for jenkins to be able to execute docker commands
RUN usermod -aG docker jenkins

# switch to user jenkins
USER jenkins
