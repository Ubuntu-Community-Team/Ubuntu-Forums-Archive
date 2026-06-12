---
title: "&quot;modprobe ndiswrapper&quot;"
date: 2012-06-23
forum: Networking &amp; Wireless
---

### Post by Fusion407 on 2012-06-23
Hiya,

I've been trying to get windows drivers installed on ubuntu 11.10 using ndiswrapper... which I believe I did. I got the system to detect my USB wireless adapter (belkin n300). Using "ndiswrapper -l" it says the driver is installed and shows the id of my adapter, telling me that it's detected. But I still have no connection... iwconfig doesn't show wlan0. I've gone through many threads trying to get this to work and I do have a problem with 1 command. "modprobe ndiswrapper". I don't get any kind of error from it. If I try running it either. 1) the terminal freezes not allowing me to enter anymore commands. 2) weird black screen with a huge line of code.

btw I'm new to ubuntu...

can anyone help?

---

### Post by praseodym on 2012-06-23
Hi,

please show the outputs of
```

lsusb
lsmod
iwconfig
dmesg | grep ndis
rfkill list
```
Edit: Plus

```
uname -a
```

---

### Post by Fusion407 on 2012-06-23
I can't give a copy-paste because I'm using a different computer that has working internet... Is it possible if you can tell what I should look for in the outputs?

---

### Post by praseodym on 2012-06-24
Please show the ID outputs of

lsusb

Example here:
```
Bus 004 Device 001: ID [COLOR="Red"]1d6b:0001[/COLOR] Linux Foundation 1.1 root hub
Bus 003 Device 001: ID [COLOR="Red"]1d6b:0001[/COLOR] Linux Foundation 1.1 root hub
Bus 002 Device 002: ID [COLOR="Red"]03f0:2a12[/COLOR] Hewlett-Packard 
Bus 002 Device 001: ID [COLOR="Red"]1d6b:0002[/COLOR] Linux Foundation 2.0 root hub
Bus 001 Device 002: ID [COLOR="Red"]058f:6363[/COLOR] Alcor Micro Corp. 
Bus 001 Device 001: ID [COLOR="Red"]1d6b:0002[/COLOR] Linux Foundation 2.0 root hub
```
and the complete output of
```
rfkill list
```

---

