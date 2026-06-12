---
title: "wifi help please"
date: 2011-10-10
forum: Networking &amp; Wireless
---

### Post by dale100 on 2011-10-10
I have a Dell Inspiron 1420, 3gb ram.  I have Windows Vista in dual boot with ubuntu 11.10 (I previously had 10.04 updated to 11.04).  I have not had 11.10 long enough to determine what, if any problems I may have, but 10.04 and 11.04 there were basically none, except wifi.  With 10.04, I could not connect at all except with a wired connection.  With 11.04, and now 11.10, the wifi works....when it wants to.

I can log on now (as of this writing, I am on 11.10) with no problems.  Later today, or tomorrow, history suggests I will not be able to log on.  At first I thought this just a glitch or something.  Only it seems that my ability to use wifi with ubuntu is getting worse.  Frankly, I never know if I will be able to access the internet or not.

I have on my computer Intel Wireless wifi link 4965AGN.  Also, according to my windows drivers, installed on my machine are Broadcom Netlink(TM) Fast Ethernet, and TAP Win32 Adapter.  (This all came installed...I have never tried to change it.  It it ain't broke, don't fix it, as they say:))  I am connected with the Intel.

As I said, this problem seems to be intermitten...sometimes I can get on, sometimes not.  I have no idea what step to take next.  Thank You for your help.

---

### Post by praseodym on 2011-10-10
Hi,

please show:

```
uname -a
iwconfig
lspci -nnk | grep -iA2 net
sudo iwlist scan
rfkill list
```

---

