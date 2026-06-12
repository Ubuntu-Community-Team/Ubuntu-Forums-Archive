---
title: "networking server and desktop"
date: 2009-01-05
forum: Networking &amp; Wireless
---

### Post by poysama on 2009-01-05
Hello. Where can I find tutorials for networking ubuntu server and desktop editions?

Is it okay to network ubuntu server 8.04 to an 8.10 desktop?

Is networking more or less the same for all Linux distros?

---

### Post by bukwirm on 2009-01-05
1. What are you trying to do specifically? [(general server information)]("https://help.ubuntu.com/8.04/serverguide/C/index.html")
2. Yes
3. There are some differences - configuration files are located in different places, for example. The underlying system is the same, though (I believe).

---

### Post by poysama on 2009-01-05
> **bukwirm said:**
> 1. What are you trying to do specifically? [(general server information)]("https://help.ubuntu.com/8.04/serverguide/C/index.html")
2. Yes

I'm want to connect (network) the desktop to my server. You see, I have this Asterisk program on a server and I want my desktop to access the GUI of the program since server doesnt have X and it is better without it I think.

Edit:
nvm..I think the guide tells me all ^^..Thanks

---

### Post by bukwirm on 2009-01-05
You should be able to simply install an ssh server on the server (*openssh-server* is the package), then enable X forwarding in the ssh-server configuration file (*/etc/ssh/sshd_config* in Debian-based distros) and restart the ssh-server (*/etc/init.d/ssh restart* in Debian-based distros). Then connect to the server from your desktop via ssh with X forwarding (ssh -X *username*@*servername*)

It works for me, at least. I haven't tried with Asterisk specifically, though.

---

### Post by poysama on 2009-01-05
> **bukwirm said:**
> You should be able to simply install an ssh server on the server (*openssh-server* is the package), then enable X forwarding in the ssh-server configuration file (*/etc/ssh/sshd_config* in Debian-based distros) and restart the ssh-server (*/etc/init.d/ssh restart* in Debian-based distros). Then connect to the server from your desktop via ssh with X forwarding (ssh -X *username*@*servername*)

It works for me, at least. I haven't tried with Astrix specifically, though.

Woah..Thanks! =) This will help me a lot.

---

### Post by Iowan on 2009-01-06
Networking is basically the same. A couple of guides for you:
[http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html]("http://www.debianadmin.com/ubuntu-networking-for-basic-and-advanced-users.html")
[https://help.ubuntu.com/7.10/server/C/network-configuration.html]("https://help.ubuntu.com/7.10/server/C/network-configuration.html")

---

