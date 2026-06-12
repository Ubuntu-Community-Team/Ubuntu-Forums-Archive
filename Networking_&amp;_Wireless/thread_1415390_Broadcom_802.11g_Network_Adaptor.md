---
title: "Broadcom 802.11g Network Adaptor"
date: 2010-02-24
forum: Networking &amp; Wireless
---

### Post by michael@cgl on 2010-02-24
Hi

I have a Broadcom 802.11g wireless network adapter. 

Could you tell me how I install this in Ubuntu .

Im an absolute beginner, but I have worked with windows for years (unfortunately)

Michael

---

### Post by Greenwidth on 2010-02-24
You need to find which Broadcom card it is, paste the following into a terminal:
```
lspci | grep 802
```
Should give you a listing like:
07:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

BCMxxxx is what you're after.
See this HowTo for installing most ones:
[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by Apollo87 on 2010-02-24
Try installing this and then rebooting:

```
sudo apt-get install bcmwl-kernel-source
```

---

### Post by tuffm on 2011-08-12
Try this:

```
sudo apt-get install b43-fwcutter
```

---

