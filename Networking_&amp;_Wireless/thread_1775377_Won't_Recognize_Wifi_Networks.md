---
title: "Won't Recognize Wifi Networks"
date: 2011-06-04
forum: Networking &amp; Wireless
---

### Post by exaltedfish on 2011-06-04
Hey all, I've been converting an old  Ibook G4 over to Linux as a sort of reclamation project, and all has been going well except for the wireless internet. I've installed ubuntu Hardy (8.04) on it, and went through the whole process of getting the b43 firmware so I could install the Broadcom driver,  which as far as I can tell was successful. However, using both  Network Manager and now Wicd my comp doesn't detect any of the wifi networks. I don't think it's a range issue because I used to get wifi just fine on this computer when I was still running OSX on it. What else could be the problem? 

Thanks,

---

### Post by manzdagratiano on 2011-06-04
Depending on which Broadcom card you have you should install either the b43 driver or the broadcom STA driver; I have a Broadcom 4312 and use the Broadcom STA driver, and b43 does not work with mine. Look at the following page for support:

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

It is available in the repos.

---

### Post by IWantFroyo on 2011-06-04
In natty, you run "lspci", search "b43" or "broadcom" in Synaptic, and install the corresponding firmware.

I really have no idea about hardy. If my suggestion doesn't work, I'm out of ideas.

---

### Post by nm_geo on 2011-06-04
> **exaltedfish said:**
> Hey all, I've been converting an old  Ibook G4 over to Linux as a sort of reclamation project, and all has been going well except for the wireless internet. I've installed ubuntu Hardy (8.04) on it, and went through the whole process of getting the b43 firmware so I could install the Broadcom driver,  which as far as I can tell was successful. However, using both  Network Manager and now Wicd my comp doesn't detect any of the wifi networks. I don't think it's a range issue because I used to get wifi just fine on this computer when I was still running OSX on it. What else could be the problem? 

Thanks,

i would recommend installing Lucid 10.04 because Hardy is no longer supported. Run this in the terminal just for information.

```
lspci -nn
```

---

### Post by exaltedfish on 2011-06-04
> **nm_geo said:**
> i would recommend installing Lucid 10.04 because Hardy is no longer supported. Run this in the terminal just for information.

```
lspci -nn
```

This computer has the BCM 4318 Airforce card, and would 10.04 work on a PPC? I've tried upgrading to it once before and wound up messing everything up.

---

