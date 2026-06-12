---
title: "How to enable packet injection in broadcom"
date: 2011-03-18
forum: Networking &amp; Wireless
---

### Post by h313 on 2011-03-18
Recently, i have been googling alot, but could not find any solution to enable packet injection on ubuntu. 
My card was perfectly running fine(though monitor mode 
and packet injection not working).
I had got bcm-sta wireless drivers installed. 

When i run lspci --nn command,
i found out my driver to be as below::

```
Network controller [0280]: Broadcom Corporation Device [14e4:4727] (rev 01)
```

when i run " airmon-ng "
it displays

```
Interface        Chipset       Driver
eth1              unknown       wl
```

also when i try " airodump-ng "

its says : 

```
ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start wlan0 <#>'
Sysfs injection support was not found either.   
```


can anyone tell me a solution to this problem.
I need to get packet injection working desperately.
Also , do i need to patch my drivers or something like that?

PLZZ help me out.

---

### Post by xx58 on 2011-03-18
:rolleyes: There are only view card with packet compatible injection. Try it with backtrack 3 and find out.

---

### Post by h313 on 2011-03-22
I checked the list mine is bcm 4727 card, and it is not supported.
so does this mean i have to patch the drivers in order to get packet injection support.

---

