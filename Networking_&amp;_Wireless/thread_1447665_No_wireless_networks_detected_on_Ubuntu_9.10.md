---
title: "No wireless networks detected on Ubuntu 9.10"
date: 2010-04-05
forum: Networking &amp; Wireless
---

### Post by darkhairhermy on 2010-04-05
I'm dual-booting Ubuntu 9.10 (upgraded from 9.04) and Windows 7 on my Dell Inspiron 1525 laptop.

Ubuntu doesn't recognize any wireless network (both in 9.04 and 9.10); my Windows OS works perfectly well with wireless, as does my wired Internet connection with Ubuntu and Windows.

I've had this problem on previous installations of Ubuntu (I've removed and re-installed it several times) but I can't locate the solution anywhere.  I've tried numerous fixes that I've found online, but none of them have worked.

System>Administration>Hardware Drivers tells me that the Broadcom STA Wireless driver is activated and currently in use.  I've tried using ndiswrapper according to several tutorials, but nothing has worked.

---

### Post by bkratz on 2010-04-05
> **darkhairhermy said:**
> I'm dual-booting Ubuntu 9.10 (upgraded from 9.04) and Windows 7 on my Dell Inspiron 1525 laptop.

Ubuntu doesn't recognize any wireless network (both in 9.04 and 9.10); my Windows OS works perfectly well with wireless, as does my wired Internet connection with Ubuntu and Windows.

I've had this problem on previous installations of Ubuntu (I've removed and re-installed it several times) but I can't locate the solution anywhere.  I've tried numerous fixes that I've found online, but none of them have worked.

System>Administration>Hardware Drivers tells me that the Broadcom STA Wireless driver is activated and currently in use.  I've tried using ndiswrapper according to several tutorials, but nothing has worked.

First go to the terminal and enter in

```
lspci | grep Network
```

If your comes back with the following

Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)


See these two postings:

[http://ubuntuforums.org/showpost.php?p=9079384&postcount=2](http://ubuntuforums.org/showpost.php?p=9079384&postcount=2)

[https://bugs.launchpad.net/jockey/+bug/441492](https://bugs.launchpad.net/jockey/+bug/441492)

---

### Post by darkhairhermy on 2010-04-05
I input that and got:
```
Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
```

---

### Post by bkratz on 2010-04-05
> **darkhairhermy said:**
> I input that and got:
```
Broadcom Corporation BCM4328 802.11a/b/g/n (rev 03)
```

Read the readme file here first, yours is specifically mentioned


[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

---

### Post by darkhairhermy on 2010-04-07
> **bkratz said:**
> Read the readme file here first, yours is specifically mentioned


[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

I started following the instructions in the Readme; I got several errors but apparently something worked because I've got wireless access now.  Thanks for the help!

---

