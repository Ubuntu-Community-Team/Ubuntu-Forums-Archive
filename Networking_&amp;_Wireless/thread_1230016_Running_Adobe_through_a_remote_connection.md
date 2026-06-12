---
title: "Running Adobe through a remote connection?"
date: 2009-08-02
forum: Networking &amp; Wireless
---

### Post by MasterNetra on 2009-08-02
I was wondering if it is possible to run adobe products through a remote desktop connection to a desktop PC with WinXP. With the computer thats connecting being a labtop with Ubuntu (Jaunty in this case)? Or through some connection at all over the net?

---

### Post by pytheas22 on 2009-08-02
Yes, you should be able to do this relatively easily.  If the Windows machine is sharing its desktop using RDP (Windows' built-in "desktop sharing" software), simply go to Applications>Internet>Terminal Server Client and put in the information to connect.

If the Windows computer is using a different kind of software to share its desktop, you will need to find an appropriate client in order to connect.

Note also that some Adobe products can run on Ubuntu directly using [wine]("https://wiki.ubuntu.com/Wine"), or using a Windows virtual machine like [VirtualBox]("https://help.ubuntu.com/community/VirtualBox").

---

