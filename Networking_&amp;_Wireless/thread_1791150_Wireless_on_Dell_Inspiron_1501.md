---
title: "Wireless on Dell Inspiron 1501"
date: 2011-06-26
forum: Networking &amp; Wireless
---

### Post by buckyo25 on 2011-06-26
Hi, I have search and read the other posts about this topic but when following the solution I seem to get stuck. Im using 11.04 natty which has me very confused

I have:
Dell Inspiron 1501
kernal 2.6.38-8-generic
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)

When going to additional drivers, it knows i need my WL drivers but returns this error:
SystemError: Binary package bcmwl-kernel-source has no trusted origin, rejecting

Please help me get my wireless up and running.. im totally confused...

---

### Post by bkratz on 2011-06-26
> **buckyo25 said:**
> Hi, I have search and read the other posts about this topic but when following the solution I seem to get stuck. Im using 11.04 natty which has me very confused

I have:
Dell Inspiron 1501
kernal 2.6.38-8-generic
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)

When going to additional drivers, it knows i need my WL drivers but returns this error:
SystemError: Binary package bcmwl-kernel-source has no trusted origin, rejecting

Please help me get my wireless up and running.. im totally confused...

Most are finding that the BCM4311 works better with the b43 driver in 11.04.  See this thread for additional information.

[http://ubuntuforums.org/showthread.php?t=1741865](http://ubuntuforums.org/showthread.php?t=1741865)

Also this---       [http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

---

### Post by buckyo25 on 2011-06-26
Thanks! Ill have a look at that tomorrow, see how i get on, probably have more questions tho   :D

---

### Post by Rifester on 2011-06-26
[http://tech.martijnedens.nl/2011/05/10/broadcom-43xx-chipset-and-ubuntu-11-04-natty-narwahl/](http://tech.martijnedens.nl/2011/05/10/broadcom-43xx-chipset-and-ubuntu-11-04-natty-narwahl/)

I have the same computer... This fixed me up.

---

### Post by nm_geo on 2011-06-26
> **buckyo25 said:**
> Hi, I have search and read the other posts about this topic but when following the solution I seem to get stuck. Im using 11.04 natty which has me very confused

I have:
Dell Inspiron 1501
kernal 2.6.38-8-generic
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
08:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)

When going to additional drivers, it knows i need my WL drivers but returns this error:
SystemError: Binary package bcmwl-kernel-source has no trusted origin, rejecting

Please help me get my wireless up and running.. im totally confused...

+1 on the b43-fwcutter and firmware-b43-installer... They generally work well with your wireless chip-set.  Hiya Rifester

---

### Post by Rifester on 2011-06-26
Hi NM-GEO!  Glad to see you helping others fix their Broadcom issues (as usual)!   ;)
You rock my friend!

---

### Post by nm_geo on 2011-06-26
> **Rifester said:**
> Hi NM-GEO!  Glad to see you helping others fix their Broadcom issues (as usual)!   ;)
You rock my friend!
Thanks I feel the same about you ROCK ON :guitar:

---

