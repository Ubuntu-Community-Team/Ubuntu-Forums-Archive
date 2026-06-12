---
title: "SSH connection not working"
date: 2012-01-14
forum: Networking &amp; Wireless
---

### Post by wyverndany on 2012-01-14
Hi I have installed ssh-server in my laptop at home and want to be able to ssh from my other laptop whihc I use at work. 
I have gone through the tutorials including the ubuntu documentation for ssh configuration. 
I'm using the default sshd_config file using port 22 to first test the connection.

I was able to connect to my own computer using :

>> ssh localhost

It worked correctly, but when I try to losg from other computer I can't...

I also noticed that I can't ssh to other computers from this laptop, I tried to ssh into a university cluster and I couldn't.

I disaveled my firewall to test all this and I'm not using any router.

Any ideas what might be the problem ?? by the way i'm using ubuntu 10.04.

Thanks

---

### Post by papibe on 2012-01-14
Try connect using the verbose option, and then post the messages you get:
```
ssh -vvv your_laptop
```
Regards.

---

### Post by wyverndany on 2012-01-14
Sorry... I forgot to mention that I tested the connection on a local network.

---

### Post by wyverndany on 2012-01-14
Ok here is the info when I try to ssh INTO my laptop:

$ ssh -vvv [email]wyverndany@xxx.xxx[/email].x.x
OpenSSH_5.3p1 Debian-3ubuntu7, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug2: ssh_connect: needpriv 0
debug1: Connecting to xxx.xxx.x.x [xxx.xxx.x.x] port 22.
debug1: connect to address xxx.xxx.x.x port 22: Connection timed out
ssh: connect to host xxx.xxx.x.x port 22: Connection timed out


and when I try to ssh from my laptop into the cluster I mentioned:

$ ssh -vvv rodrigd@10.68.208.1
OpenSSH_5.3p1 Debian-3ubuntu7, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 10.68.208.1 [10.68.208.1] port 22.
debug1: connect to address 10.68.208.1 port 22: Connection timed out
ssh: connect to host 10.68.208.1 port 22: Connection timed out

---

### Post by Sonicgoo on 2012-01-14
I have the similar issue over Christmas I set up ssh on my parents computer so that I can help them with computer issues. everything was working fine until a few days ago now I get this.


sonic@sonicgoo:~$ ssh -vvv -p 9968  cardwell@96.60.238.150
OpenSSH_5.8p1 Debian-1ubuntu3, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 96.60.238.150 [96.60.238.150] port 9968.
debug1: connect to address 96.60.238.150 port 9968: Connection timed out
ssh: connect to host 96.60.238.150 port 9968: Connection timed out

---

### Post by wyverndany on 2012-01-16
Hi, I just found out the source of the problem...
Apparently the network, which is managed by the university must be configured specifically to allow ssh through the ports. So that was blocking the connection.

Thanks

---

### Post by Sonicgoo on 2012-01-21
My issue was that the computer I was logging into was a dual boot and had been in windows for about a week. 

My issue has been solved

---

