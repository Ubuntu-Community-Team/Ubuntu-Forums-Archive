---
title: "Remote Desktop problem"
date: 2011-01-12
forum: Networking &amp; Wireless
---

### Post by abhicool.indya on 2011-01-12
Hi,

I need to remote access a PC(running winxp) from my laptop(running ubuntu 10.10) over internet. How to go about it?

tia,
Abhishek (is new to Linux)

---

### Post by cipherboy_loc on 2011-01-12
Look into VNC. GNOME + Ubuntu has Vinagre (a VNC viewer) installed by default, and RealVNC is a good VNC server for Windows. Port forward (!!UNSAFE!!) the Window computer's VNC port (5900) if you really need "over the internet". If you are on the same network, you don't need to do this.

If you need more security, look into tunneling VNC over SSH.

Cipherboy

---

