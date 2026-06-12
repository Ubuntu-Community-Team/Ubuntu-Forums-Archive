---
title: "ssh unrecognized service"
date: 2012-06-21
forum: Networking &amp; Wireless
---

### Post by professor-g on 2012-06-21
Having troubles with ssh for a machine on an internal network

CAN ping out from machine
CAN ssh out from machine

CAN ping machine from outside.
CANNOT ssh into machine from outside.
> ssh: connect to host 192.168.0.46 port 22: Connection refused

Tried changing the port in /etc/ssh/ssh_config.
Doesnt help.

Tried getting status of ssh and (re)starting it.
Doesnt help:
```
sudo service ssh status
```> ssh: unrecognized service

Also tried (just in case!):
```
sudo service sshd status
```> sshd: unrecognized service

I notice that ssh does not exist in /etc/init.d

Please advise.
Thanks,

G.

---

### Post by steeldriver on 2012-06-21
Hi, sorry I thought that was obvious from your other thread:

```
$ dpkg -l | grep ssh
ii  openssh-client                   1:5.9p1-5ubuntu1            secure shell (SSH) client, for secure access to remote machine
```means you only have the client portion of ssh installed (which doesn't run as a service)

Once you get the server installed as well, dpkg -l will show an additional line like

```
ii  openssh-server                      1:5.8p1-7ubuntu1                         secure shell (SSH) server, for  secure access **from** remote machines

```(emphasis mine) and the ssh service will start running.

---

### Post by professor-g on 2012-06-21
> **steeldriver said:**
> Hi, sorry I thought that was obvious from your other thread:
```
$ dpkg -l | grep ssh
ii  openssh-client                   1:5.9p1-5ubuntu1            secure shell (SSH) client, for secure access to remote machine
```means you only have the client portion of ssh installed (which doesn't run as a service)

Perhaps - but I still dont have a solution to why I cannot 'start' ssh.
AND - IF it is not running, how then can I ssh into another machine - but not back into the box in question.
Any ideas?

G.

---

### Post by ajgreeny on 2012-06-21
When you run the ```
sudo service ssh start
``` command it actually starts the openssh-server not the client, so if you don't have the server package installed you will get nowhere.

The openssh-client simply starts with the command you use to connect ```
ssh user@address
``` you do not need to, nor can you start it as a service prior to using it.

---

