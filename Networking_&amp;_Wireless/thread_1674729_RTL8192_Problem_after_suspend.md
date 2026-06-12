---
title: "RTL8192 Problem after suspend"
date: 2011-01-24
forum: Networking &amp; Wireless
---

### Post by numus on 2011-01-24
Anyone ever solve the wifi after suspend problem? I have a Samsung n130 running Ubuntu 10.10 and after a suspend, the wifi just decides to not work anymore. Havent found a solution yet

---

### Post by numus on 2011-01-25
The wake issue has never been resolved?

---

### Post by walt.smith1960 on 2011-01-25
I've not had a problem with USB RTL8192SU adapters.  What I have seen happen after waking from suspend is Network Manager deselects "enable networking" or "enable wireless"for no apparent reason. Right click the Network manager applet and make sure those two boxes are checked.  Other than that I have no idea, sorry.

---

### Post by numus on 2011-01-25
When it wakes up from suspend it nm-tool has
Driver rtl819xE state: unavalible

---

### Post by walt.smith1960 on 2011-01-26
That's a different adapter than mine. I assume yours is a PCIe.  I wonder if you need to reload or unload then reload the module?  If you do ```
lsmod
``` to list the modules loaded, do you see any reference to RTL81???

---

### Post by numus on 2011-01-27
> **walt.smith1960 said:**
> That's a different adapter than mine. I assume yours is a PCIe.  I wonder if you need to reload or unload then reload the module?  If you do ```
lsmod
``` to list the modules loaded, do you see any reference to RTL81???

r8192_pci

---

### Post by walt.smith1960 on 2011-01-27
I'm not very knowledgeable about the inner workings of Ubuntu.  People who have had problems similar to yours found that one or more modules was either not unloading on suspend or was not reloading on wake.  Perhaps someone better versed can chip in here.  Chili555, you out there?

Edit:  here's a thead which may be tangentially related (or not) 
[http://ohioloco.ubuntuforums.org/showthread.php?t=1394281](http://ohioloco.ubuntuforums.org/showthread.php?t=1394281)

---

### Post by numus on 2011-02-03
Any update on the wake issue?

---

### Post by numus on 2011-04-04
Anyone have any other ideas?
Lately when i connect to my home wifi (atheros based router) ubuntu totally locks up. It doesn't do it when i connect to other networks.

---

### Post by mamamia88 on 2011-10-29
Thought I would throw this out there for anyone who has this problem.  [http://ubuntuforums.org/showthread.php?t=1689148&page=3](http://ubuntuforums.org/showthread.php?t=1689148&page=3) I followed post 22 and it works after suspend now.   BTW I'm on a samsung n130 with a rtl8192e running 11.10 with 3.0.0-13 kernel.

---

