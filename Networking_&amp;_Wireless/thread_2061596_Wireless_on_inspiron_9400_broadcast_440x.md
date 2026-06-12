---
title: "Wireless on inspiron 9400 broadcast 440x"
date: 2012-09-22
forum: Networking &amp; Wireless
---

### Post by bacchus1903 on 2012-09-22
Hi

I move all my PC to ubuntu, but I have problem with a Dell Inspiron 9400, the broadcast 440x adapter do not work, I search the web and forums, but nothing work ;-(
I try g43 drivers with no succes (they work on my inspiron 5150)

Can you give me some idea how to make it work

Thanks in advance

Jules:sad:

---

### Post by Hadaka on 2012-09-23
Hi, please post the output of..

```
lspci -nnk | grep -iA2 0280 
```

thanks.

---

### Post by bacchus1903 on 2012-09-23
Hi 
Here is the response

anh-9400@ubuntu:~$ lspci -nnk | grep -iA2 0280
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Kernel driver in use: b43-pci-bridge

Thanks  :popcorn:soon ...

---

### Post by bkratz on 2012-09-23
> **bacchus1903 said:**
> Hi 
Here is the response

anh-9400@ubuntu:~$ lspci -nnk | grep -iA2 0280
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Kernel driver in use: b43-pci-bridge

Thanks  :popcorn:soon ...



Post two should get you going

[http://ubuntuforums.org/showthread.php?t=1997880](http://ubuntuforums.org/showthread.php?t=1997880)

---

### Post by daslinkard on 2012-09-23
> **bacchus1903 said:**
> 
anh-9400@ubuntu:~$ lspci -nnk | grep -iA2 0280
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
    Kernel driver in use: b43-pci-bridge

These following sudo commands should do the trick for you...

```
sudo apt-get remove --purge bcmwl-kernel-source
``` 
```
sudo apt-get install linux-firmware-nonfree
```

---

### Post by bacchus1903 on 2012-09-23
Thanks

With the 2 code lines, and a restart my wireless is working
I can finally remove the leash ... hooop I mean the lan cable.

:guitar:

---

### Post by bkratz on 2012-09-23
Glad to hear you got it going---enjoy!

---

### Post by daslinkard on 2012-09-23
Glad this got you back in business....anytime you need anything we are here for you in the forum.  Also, please mark this thread as solved!  Thanks!

---

### Post by Norman1950 on 2013-01-23
Sorry to bring this old thread back up, but it saved me! After a couple of weeks of trying what everyone else says works, this finally worked for me!

---

