---
title: "Looking for a guide, connecting 1 9.04 &amp; 2 XP's"
date: 2009-07-18
forum: Networking &amp; Wireless
---

### Post by H_a_D_3_z on 2009-07-18
As you can tell from my title, I would like to be able to connect my Laptop 9.04 & my childrens PC's which are XP's.  I would like to be able to see what they are looking at on the net & also to be able to share files, fix their PC's if needed, etc.  I'm am 1 yr vet with Ubuntu, so I am still in the learning process; but not a newb.  I do not have any experience when it comes to networking, so If some one could point me in the right direction I would appreciate it.

My setup as of now is as follows:

1 Laptop Ubuntu 9.04
2 PC's Windows XP
2 Linksys routers both with dd-wrt firmware

9.04 connects to router(A) wirelessly
2 XP's connect to router(B) wired
router(B) connects to router(A) wirelessly

Thanks

---

### Post by enz1m3 on 2009-07-19
Hi, for the file sharing, you can simply enable simple windows share on their laptops and it will be accessible by your ubuntu. If you want to share your ubuntu files with them, install and setup SAMBA.

For the "parenting control" ( ;) ) I'd recommend installing a VNC server like tightVNC on the both XP laptops and then you can connect to them using plain ol' Remote Desktop Viewer from ubuntu.

I'm assuming that you can ping them all :) Otherwise you should have to rethink your network structure :)

---

### Post by swerdna on 2009-07-19
This step-by-step might help: [The Samba LAN Primer for Ubuntu: HowTo Set up an Ubuntu-Windows Home Office LAN/Network]("http://ubuntu.swerdna.org/ubulanprimer.html")

---

### Post by H_a_D_3_z on 2009-07-20
Hey thanks guys, didn't get a chance to hook it up this weekend will try next weekend.  But, thanks again

---

