---
title: "downloaded 10.04, wireless problem."
date: 2010-08-09
forum: Networking &amp; Wireless
---

### Post by naaman fletcher on 2010-08-09
Wiped clean an old dell laptop with all sorts of issues and put 10.04 on it.  It does not see any wireless networks available (trust me, there are).

Looking around this forum I am stuck because everyone seems to say that I need to enable the proprietary driver.  When I go to do that however it says that there are no proprietary drivers available.

Any idea what to do now?

this is a dell inspiron 6400

thanks

---

### Post by rajan on 2010-08-10
try running the command lspci. when i run it on my dell inspiron 8600, i get this as the last line:

```

02:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 03)

```

i suspect that you may not have a wireless device that requires the proprietary driver. 

if, however, you do have it, don't worry. you can install it yourself. it's not terribly difficult (hopefully).

---

### Post by naaman fletcher on 2010-08-10
Thank you.  I ran lspci and got:

Network Controller:  Broadcom Corporation BCM4311 802.11b/g WLAN (rev) 01


What do I do now?

---

### Post by naaman fletcher on 2010-08-10
UPDATE:

I plugged in to the router with an ethernet connection.  got online and was able to download and install the broadcom sta driver.  I reset the computer, and still nothing.

---

### Post by rajan on 2010-08-10
what are you seeing when you go to system > administration > hardware drivers? 

in this menu, this is what i see (file attached)

from the output of lspci you've posted, it appears you have a broadcom card, for which you have installed the correct driver. 

it may be as simple as a reboot, making sure that the wireless switch is toggled to "on" -- i made that mistake myself earlier. 

also, what do you see when you go to network manager? does it show anything?

---

