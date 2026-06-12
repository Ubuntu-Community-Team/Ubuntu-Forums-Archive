---
title: "Problems with PuTTy and SSH in UB 11.10"
date: 2012-05-12
forum: Networking &amp; Wireless
---

### Post by Zordrac Stormhammer on 2012-05-12
Hello.

Background:
I have recently been introduced to Ubuntu. My work requires that I use software written for the Linux environment. Since I work from a different box (with Win 7 on it), I was advised to use PuTTy (with OpenSSH Server on the Linux box) to open an SSH connection and run my programs remotely using Xming.

Problem:
I tried using PuTTy and I got to the point where it asks me for a login name and then a password. After I enter the password, it tells me "Access Denied". What have I done wrong? What did I not do? What do I have to do to get this fixed? (To clarify, I already tried the GSSAPI thing and it did not solve the problem)

Any Help will be appreciated.

Zordrac

---

### Post by steeldriver on 2012-05-12
Thanks for the tip about GSSAPI, I wasn't aware of that and it has been bugging me (although in my case it happily accepts the password after telling me 'Access denied')

I'm no expert but I *do* use a similar setup from PuTTY on XP at home to a Linux box at work (although that's a Fedora box I think). I use SSH tunneling to get a graphical login with a Windows VNC client (in my case UltraVNC)

I can also PuTTY from XP to a default installation of openssh on Xubuntu 11.10 on my home LAN, so I don't think there is anything about the default openssh / 11.10 setup that should hinder you 

Since you get a connection OK, it would seem to be an authentication issue rather than a networking (ports / firewalls) issue - you could try installing plink (part of the full PuTTY package, if you use the Windows installer) and running it in verbose mode (plink -v) to debug the connection

---

### Post by Zordrac Stormhammer on 2012-05-12
Hello.

I will try your suggestion in a few hours. Currently re-installing the entire Ubuntu 11.10.

---

### Post by Ashtray2 on 2012-05-13
If you haven't already, make sure you're connecting on the port that the IT department has designated for SSH.

You're probably trying to login to the wrong directory.  So for your hostname, are you putting [email]Zordrac@mycompany.com[/email]  or are you just putting mycompany.com.

The people in charge of that server should have hooked you up with exact instructions.  Are you sure they even granted you access over SSH?

---

### Post by Ashtray2 on 2012-05-13
Ok, now I'm confused.  Are you creating an Ubuntu SSH server or are you using Ubuntu to connect to the remote server.

---

