---
title: "[SOLVED] ssh help"
date: 2008-12-14
forum: Networking &amp; Wireless
---

### Post by nothingspecial on 2008-12-14
I`ve stuck my pc under the stairs to make room for the christmas tree and will now use it as a home server/workhorse. Theres a couple of things I`d like to do/don`t really understand about ssh.

1. How do I log in with x without having to use sudo to start a graphical app? Or does it matter? What I mean is, as a good ubuntu user I don`t like starting things as root if I don`t have to, so am I starting the app on the host as root or am I just using root to start it -------- I hope I make sense.


2. How do I start the app then leave it running while I log out of the secure shell, turn my laptop off and go wash the car?

Example, I want to do a batch conversion from Flac to mp3. I want to log in to the box under the stairs, start it going, log out then come back the next day without all my tunes being owned by root.

Thanks

---

### Post by HermanAB on 2008-12-14
To get SSH access, install the openssh-server package.  After that, you can leave the server in runlevel 3.

You can run X applications over SSH like this:
ssh -X -C -c blowfish user@server "gedit /etc/fstab"

You can of course set those parameters in /etc/ssh in a config file so they are the default.

Cheers,

Herman

---

### Post by nothingspecial on 2008-12-14
> **HermanAB said:**
> To get SSH access, install the openssh-server package.  After that, you can leave the server in runlevel 3.

You can run X applications over SSH like this:
ssh -X -C -c blowfish user@server "gedit /etc/fstab"

You can of course set those parameters in /etc/ssh in a config file so they are the default.

Cheers,

Herman 

Thanks for the reply.  :p

Am I adding ssh -X -C -c blowfish user@server to my /etc/fstab?
Typing it works so thanks.
I`ve looked at both ssh_config and sshd_config and can`t work out what to do. 

A little more help please

---

### Post by kevdog on 2008-12-14
Lets break this down for you

-X -C -c blowfish

-X equals Forward X11 connections

-C equals Compress everything

-c equals use the blowfish cipher = I think this is the default, however this line is not absolutely necessary.  You could theoretically use any cipher included in the ssh suite.

---

### Post by nothingspecial on 2008-12-14
sorted.

---

