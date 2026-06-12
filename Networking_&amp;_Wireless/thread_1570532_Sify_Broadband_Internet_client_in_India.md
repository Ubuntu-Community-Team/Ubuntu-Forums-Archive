---
title: "Sify Broadband Internet client in India"
date: 2010-09-08
forum: Networking &amp; Wireless
---

### Post by narendraD on 2010-09-08
I am a Ubuntu Lucid 64bit gnome user from Hyderabad, India.
Sify Broadband is an Internet service provider in India. Sify broadband uses a simple Ethernet based LAN connection to connect its users to the Internet.

I use Sify Broadband internet (wired) with my Ubuntu 10.04 X86_64bit version.

Sify  provides a Sify client program on Win, Linux and Mac. This program is  the interface between Sify and the customer and is used for logging in  and out. The issue is this program does not work on my machine. So i use a web  browser based login.

The program is available at [http://202.144.65.70:8090/linuxinstall.html](http://202.144.65.70:8090/linuxinstall.html) 
The error that i have got is "sifyconnect: error while loading shared  libraries: libssl.so.4: cannot open shared object file: No such file or  directory"

And i have not tried the Mac client that is basically a Java app, so may work.

I do have libssl.so.4, but still the same error**. **So i tried symlinking with cd /usr/lib
sudo ln -s libssl.so libssl.so.4
sudo ln -s libcrypto.so libcrypto.so.4

But, same error again. 

Can anyone help.

---

### Post by vmath89 on 2011-05-17
HeY!

I too have the same problem. Kindly mail me at [email]vmath89@gmail.com[/email] if you find any solution.

---

