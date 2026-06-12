---
title: "problem with network connection"
date: 2010-05-27
forum: Networking &amp; Wireless
---

### Post by petermg on 2010-05-27
I was trying to install a WIFI card in my Lucid PC, well didn't work, I will open another thread on that, but prior to this I was tethering via my PDA's usb connection and it was working.

For some reason now my Lucid box won't see the connection until I enter
"sudo modprobe rndis_host"

Then Lucid sees the connection, gets a local IP, and I can surf.  Which is exactly how I'm online right now.  

Does anyone know how I can re-ad this module to the kernel so that I don't have to manually load it every time?  

I am totally befuddled as to how this happened...

---

### Post by purelinuxuser on 2010-05-27
> **petermg said:**
> For some reason now my Lucid box won't see the connection until I enter
"sudo modprobe rndis_host"

Then Lucid sees the connection, gets a local IP, and I can surf.  Which is exactly how I'm online right now.  

Does anyone know how I can re-ad this module to the kernel so that I don't have to manually load it every time?  

Just add
```
rndis_host
```
to /etc/modules ;)

---

### Post by petermg on 2010-05-27
Thanks!!!!!!!!!!!!!!!!

---

### Post by purelinuxuser on 2010-05-27
> **petermg said:**
> Thanks!!!!!!!!!!!!!!!!

You're welcome :P and don't forget to mark this thread [SOLVED]!

---

