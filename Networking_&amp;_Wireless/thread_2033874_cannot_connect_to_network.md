---
title: "cannot connect to network"
date: 2012-07-27
forum: Networking &amp; Wireless
---

### Post by gken on 2012-07-27
Hi,

Yesterday my computer was connecting to networks happily (wired) - I then suspended the machine and brought it home from the office and un-suspended when I got home.  At home, I connected to my normal wired connection and the connection was made as usual, but I cannot connect to any addresses.

Ethernet controller [0200]: Intel Corporation 82577LM Gigabit Network Connection [8086:10ea] (rev 05)
Subsystem: Dell Device [1028:040a]
Kernel driver in use: e1000e

Network controller [0280]: Intel Corporation Centrino Advanced-N 6200 [8086:422c] (rev 35)
Sybsystem: Intel Corporation Centrino Advanced-N 6200 2x2 AGN [8086:1321]
Kernel driver in use: iwlwifi

Any suggestions for troubleshooting this would be greatly appreciated - I'm a bit of a newbie...

Thanks!

---

### Post by kc1di on 2012-07-27
did you try to reboot the machine?

---

### Post by gken on 2012-07-27
> **kc1di said:**
> did you try to reboot the machine?

Yes - and also tried /etc/init.d/networking restart

---

### Post by gken on 2012-07-27
Figured it out - I needed to do this

sudo dhclient 

and now it is working just fine :):):) - ipconflict then I guess?

---

