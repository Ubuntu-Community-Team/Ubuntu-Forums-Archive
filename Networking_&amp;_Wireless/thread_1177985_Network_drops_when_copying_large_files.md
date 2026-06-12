---
title: "Network drops when copying large files"
date: 2009-06-04
forum: Networking &amp; Wireless
---

### Post by retrovelo on 2009-06-04
I am experiencing network drops when copying large files to and from my Ubuntu server from PCs via Samba shares. 

For the most part the Ubuntu machine runs solid. It streams music and video, acts as a LAMP dev server, all without a hitch. Typically there's no problem accessing shares or services on the machine. Just rock solid.

That however changes when I try to truck around a bunch of larger files (copies involving 500mb or more). The network chugs along for a bit and then dies. When this happens I can no longer ping from the Windows machines (meaning it's not just Samba ... TPC/IP goes away).

Most of the time the server runs headless, so it's a drag when the network dies. Sadly I often end up holding down the power button and forcing a reboot.  

One aspect I found interesting: sometimes the network will come back if tap a key or two on the keyboard (I leave a mouse and keyboard attached to the box, just no monitor). Weird, huh?

I'm running Ubuntu 8.10 on the server and have the problem with both a Vista desktop and XP laptop.  

Any help troubleshooting is appreciated.

---

### Post by nandemonai on 2009-06-04
Check out "/var/log/messages"

---

