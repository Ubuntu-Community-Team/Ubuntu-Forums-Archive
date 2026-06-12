---
title: "Sharing disk drives over home network AND internet"
date: 2013-01-04
forum: Networking &amp; Wireless
---

### Post by nwngeek212 on 2013-01-04
Hi all. I'm a college student with a less-than-adequate hard drive on my laptop. I do however have an ubuntu server set up (in ubuntu desktop 12.10) that has 1 TB internal disk space and a 2 TB external hard drive mounted. 

What I want to do is be able to access the hard drive from any computer on my home network and also be able to access them from college (or anywhere else in the world). The only server will be this ubuntu machine, but the clients could be Linux, OS X or Windows. An added bonus (but not necessity) would be the ability to mount the drive not only from my laptop but also from any of the public University computers.

I know that there may be a way to do this using SSH, but what I want to be able to do is use the "Map network drive" feature on Windows and the "Connect to Server" feature on OS X/Linux to mount both the internal and external drives to my computers, and unmount with a click. In other words, I'm looking for a GUI solution. Any help?

---

### Post by 2F4U on 2013-01-05
> The only server will be this ubuntu machine, but the clients could be Linux, OS X or Windows.

For the home network, you should look into Samba.This is a common way to share content among Linux, Mac OSX and Windows.

[https://help.ubuntu.com/12.10/serverguide/samba-fileserver.html](https://help.ubuntu.com/12.10/serverguide/samba-fileserver.html)

---

### Post by bab1 on 2013-01-05
> **2F4U said:**
> For the home network, you should look into Samba.This is a common way to share content among Linux, Mac OSX and Windows.

[https://help.ubuntu.com/12.10/serverguide/samba-fileserver.html](https://help.ubuntu.com/12.10/serverguide/samba-fileserver.html)

If you have Windows clients you will need to use Samba for sure.  To use Samba over the internet you will need to set up a VPN.  Samba doesn't play well on the Internet.  See [**_[COLOR="Blue"]OpenVPN[/COLOR]_**]("http://openvpn.net/index.php/open-source/overview.html").

---

