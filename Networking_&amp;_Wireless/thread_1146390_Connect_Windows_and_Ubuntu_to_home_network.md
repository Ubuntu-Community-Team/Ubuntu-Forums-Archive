---
title: "Connect Windows and Ubuntu to home network"
date: 2009-05-02
forum: Networking &amp; Wireless
---

### Post by helstreak on 2009-05-02
I have a windows xp machine and an Ubuntu 8.04 machine.  They are both hardwired to the wireless router.  I would like to connect these two machines so I may view the files on each.  Also, if possible I would like to be able to control one computer via the other computer.

Thank you for your help :)

EDIT:
I've installed putty on my windows computer but I can't seem to get it to connect with the Ubuntu computer.  Does anyone know of a good tutorial?

---

### Post by freebeer on 2009-05-02
Probably you'll be interested in Samba to share files on the Ubuntu machine.

For remote access, I use VNCviewer on the Windows machines and enable remote desktop on the Ubuntu machines.  (System -> Preferences -> Remote Desktop)

For remote access to the Windows boxes, you'll have to install (perhaps) and enable it on those machines, too.  9.04 already comes with Remote Desktop Viewer (Applications -> Internet -> Remote Desktop Viewer)

Hope that helps some.

---

