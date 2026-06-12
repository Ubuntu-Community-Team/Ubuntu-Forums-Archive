---
title: "WPA2 E +TLS + certificates"
date: 2010-05-07
forum: Networking &amp; Wireless
---

### Post by Arizon_Dread on 2010-05-07
Hello!

Trying to connect to a WPA2 Enterprise with TLS encryption and certificates (CA and personal key) but cannot click 'connect' since it's disabled. It works with another user. What to do?

The problem is the following:
At work, I need to connect to a WPA2 Enterprise network with a TLS authentication mode. So I specify the connection types, identity, CA-certificate and the private key which I know is correct(I managed to connect with another user), at last I type the password which I used to export the private key. 

The problem is that the connect-button is grayed out, disabled, so I cannot click it. 

I created a new user and tried specifying the same credentials and it worked on the first try! I suspect it has something to do with my old settings somewhere in my home-directory since it worked with another user. I read online (lost the link though) that if I removed .gconf .gconfd .gnome2 .gnome2-private, it'd be reset. I tried renaming all the stated folders to foldername_old, and it looked like it defaulted, my panel-shortcuts were gone and so forth. 

I tried the network login procedure again and it didn't work. 

Does anyone have a clue to the real problem? or maybe an idea how I could default all my network stuff, without destroying my other settings, specified in the home-dir?

I use a Lenovo Thinkpad T61p, Ubuntu 10.04 (just upgraded yesterday from 9.04 via 9.10)

Thanks in advance.

---

### Post by Arizon_Dread on 2010-05-10
Bump, put some more info in the first post

---

