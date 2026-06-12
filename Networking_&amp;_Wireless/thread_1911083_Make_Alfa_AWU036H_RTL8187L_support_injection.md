---
title: "Make Alfa AWU036H RTL8187L support injection"
date: 2012-01-18
forum: Networking &amp; Wireless
---

### Post by IT2UPDATE on 2012-01-18
I have an Alfa AWU036H RTL8187L and I want to make it support injection. Searched on the web and I found PATCH to make Alfa supported injection but I have a problem in the batch 

```

    root@laptop:~/rtl8187_linux_26.1010.0622.2006# make install
    install -d /lib/modules/2.6.29.4/kernel/drivers/net/wireless/rtl_ieee80211
    install -d /lib/modules/2.6.29.4/kernel/drivers/net/wireless/rtl8187
    install -m 644 ./ieee80211/*.ko /lib/modules/2.6.29.4/kernel/drivers/net/wireless/rtl_ieee80211
    install: cannot stat `./ieee80211/*.ko': No such file or directory
    make: *** [install] Error 1
```
Tried installing Hardy. That's error. Any suggestions will be greatly appreciated.
I have used this link :[http://www.aircrack-ng.org/doku.php?id=r8187](http://www.aircrack-ng.org/doku.php?id=r8187)[http://www.aircrack-ng.org/doku.php?id=r8187]("http://www.aircrack-ng.org/doku.php?id=r8187")

A PROBLEM WITH ALFA RTL8187 
I RUN aircrack-ng start wlan0 
and airmon-ng 
```
root@GEN-LW40-J4JE1:/home/GENl# airodump-ng wlan0
ioctl(SIOCSIWMODE) failed: Device or resource busy

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start wlan0 <#>'
Sysfs injection support was not found either.

```

---

### Post by it4update on 2012-01-18
please any help >>>>>

---

### Post by cariboo on 2012-01-18
Please don't create multiple threads on the same subject, I have merged your two threads into one post.

---

### Post by IT2UPDATE on 2012-01-18
PLEASE ANY HELP <<<< HELP ME PLEASE >>> UBUNTU FORUM EXPERT USERS WILL HELP ME >>> AGAIN HELP ME :confused:

---

