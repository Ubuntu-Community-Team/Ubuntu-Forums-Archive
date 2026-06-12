---
title: "How to debug terminal lag."
date: 2009-08-26
forum: Networking &amp; Wireless
---

### Post by astifter on 2009-08-26
Okay, this is a problem where I do not even know what to google for:

I have Ubuntu 9.04, fully patched, not much customisation. I run wmii as my window manager. 

I connect to my university via vpnc and ssh into a server and sometimes there is a terrible lag on the connection, it works fine most of the time. How do I debug this?

The commands I use:
sudo vpnc
xterm -s -u8 -sl 25000 -sb -rightbar -si -sk
ssh [..to server..]

Versions of commands:
xterm -v: XTerm(241)
ssh -v:  OpenSSH_5.1p1 Debian-5ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
vpnc --version: vpnc version 0.5.3
<edit>
Server side sshd version:
sshd -v: OpenSSH_5.1p1 Debian-5, OpenSSL 0.9.8g 19 Oct 2007
</edit>

Thanks, Andi

PS: Linux user since 2002, bash knowledge available :-)

---

