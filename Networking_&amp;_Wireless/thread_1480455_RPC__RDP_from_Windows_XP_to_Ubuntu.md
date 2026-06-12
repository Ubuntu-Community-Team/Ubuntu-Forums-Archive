---
title: "RPC / RDP from Windows XP to Ubuntu"
date: 2010-05-11
forum: Networking &amp; Wireless
---

### Post by sir_real4127 on 2010-05-11
If this is the wrong place for this, sorry and please direct me to the right place.
 
Anyway, is there any software out there for Windows that will allow me to remote desktop into my Ubuntu system? I have a Windows laptop for work and would love to be able to remote into my Linux box while on my home wireless network.
 
Thanks in advance

---

### Post by johnson.d on 2010-05-12
You can use anyone of the following options.

1) VNC
2) FreeNX

VNC: If both the machines are on a LAN network you can go for a VNC server. You can enable remote access on a Ubuntu machine by using the following steps: 
Goto Gnome menu -> System -> Preferences -> Remote Desktop

Check the box "Allow other users to view your desktop" to enable the server
If you want to control the remote machine you can check the box "Allow other users to control your desktop". You can also choose the security options by checking the appropriate boxes.

In the Windows client you need to install a VNC client.You can install it from any one of the links below.

[http://www.realvnc.com/products/download.html](http://www.realvnc.com/products/download.html)
[http://www.tightvnc.com/download.html](http://www.tightvnc.com/download.html)

FreeNX : For installing and configuring remote desktop using FreeNX you can use the following link:
[http://cssoss.wordpress.com/2010/05/04/freenx/](http://cssoss.wordpress.com/2010/05/04/freenx/)

---

