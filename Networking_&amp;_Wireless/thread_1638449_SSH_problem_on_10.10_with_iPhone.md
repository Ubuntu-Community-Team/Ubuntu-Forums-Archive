---
title: "SSH problem on 10.10 with iPhone"
date: 2010-12-05
forum: Networking &amp; Wireless
---

### Post by Fd0_CR on 2010-12-05
Hi, I'm having trouble when connecting through SSH on terminal with my iPhone 3GS. I have OpenSSH 5.2p1-8 installed on the phone and when trying to connect it says to me "ssh_exchange_identification: Connection closed by remote host". Any help would be great, thanks.


**My problem:**

fernando@Fenix:~$ ssh [EMAIL="root@xxx.xxx.x.xxx"]root@xxx.xxx.x.xxx[/EMAIL] -vvv
OpenSSH_5.5p1 Debian-4ubuntu4, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to xxx.xxx.x.xxx [xxx.xxx.x.xxx] port 22.
debug1: Connection established.
debug1: identity file /home/fernando/.ssh/id_rsa type -1
debug1: identity file /home/fernando/.ssh/id_rsa-cert type -1
debug1: identity file /home/fernando/.ssh/id_dsa type -1
debug1: identity file /home/fernando/.ssh/id_dsa-cert type -1
ssh_exchange_identification: Connection closed by remote host

---

