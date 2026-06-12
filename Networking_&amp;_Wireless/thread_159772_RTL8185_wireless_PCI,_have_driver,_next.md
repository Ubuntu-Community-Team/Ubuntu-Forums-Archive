---
title: "RTL8185 wireless PCI, have driver, next?"
date: 2006-04-13
forum: Networking &amp; Wireless
---

### Post by Panhead Bill on 2006-04-13
Card is a generic CompUSA PCI wireless card.  All visible chips have Realtek 8185 designations.  I have searched the threads, looked in the how to's, wiki, and am a little confused.

If the card I have has a LINUX driver;

[http://www.realtek.com.tw/downloads/downloads1-3.aspx?keyword=rtl8185](http://www.realtek.com.tw/downloads/downloads1-3.aspx?keyword=rtl8185)

Why do some RTL8185  threads refer people to the RTL8180 driver?  Is there a reason NOT to use the 8185 driver?

Being a noobie, is my next step to compile this driver?

---

### Post by az on 2006-04-13
You can use ndiswrapper in breezy.  If you want to be daring, try using Dapper since it includes the driver in the stock kernel.

You can compile the driver for breezy,  which is not that difficult (install build-essential, gcc-3.4 and linux-headers-xxxxxxxx) but maybe just dist-upgrading to dapper is something you want to try...

---

### Post by Panhead Bill on 2006-04-16
[QUOTE=azz]You can use ndiswrapper in breezy.  If you want to be daring, try using Dapper since it includes the driver in the stock kernel.QUOTE]

Does Dapper have the 8180 or the 8185 driver?

---

### Post by az on 2006-04-16
r818x and r8187

---

### Post by Panhead Bill on 2006-04-18
I loaded ndiswrapper-utils and ndisgtk, checked the ndiswrapper list but my card isn't listed, nor is the exact PCI ID: 10ec:8185.

I then downloaded the Linux driver on Realtek's site, but after figuring out how to use the tar command, I had a list of 20 some files with .c or .h suffixes, not the INF or SYS files that wireless/driver/Ndiswrapper - Ubuntu Wiki refers to.

I guess I'll give Flight 6 a try.

---

### Post by Ninjai on 2006-04-18
Dont know if it helps but with my Realtek wireless chip I had to use ndiswrapper and win2000 driver from website-not xp's as it didn't work. Nor did the linux driver-kernel version way older. This was using Flight 6 as well btw.

---

### Post by Panhead Bill on 2006-04-24
Update:  Dapper flight 6 is an improvement.  My wireless card is seen by the system and can activate.  Now if I could only get wpasupplicant working so I can access the home network with the wireless card.

---

