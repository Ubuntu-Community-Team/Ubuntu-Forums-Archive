---
title: "Wireless USB Adapter (WPN111 in this case)"
date: 2009-09-02
forum: Networking &amp; Wireless
---

### Post by badbetty on 2009-09-02
Hello folks

Just a quick note that it seems that Ubuntu 9.04 x86-64  has a lot of trouble recognising the Netgear WPN111 in a USB port, in that no matter how i tried [at least] it never did.   'lsusb' shows the adapter present; 'ndiswrapper' appears to load drivers fine, but in the end there is no flashing light on the adapter and no network.

My motherboard setup is ASUS M4A78 PRO AMD Phenom II x4 810 Quad  4Gb.

Now then, when I tried the 9.04 x86 (32 bit?)  install, i had no perceivable problems at all. I have reverted to the 32 bit version.

I am unsure as to what the problem is: hardware (my setup is not actually 64 capable), or the Ubuntu install is lacking in this area. If any one has any views they would be most welcome.

Anyway thanks for reading (if you do) and apologies if I have used any wrong terms etc.
BB

---

### Post by TranceWarp on 2009-10-19
Apparently, no matter the operating system you're using, you will have problems with older wireless adapters in a 64-bit environment.  Vista 64-bit would BSOD after 1.5 hours with my VPN311 PCI adapter for my PC.  Ended up getting a wireless bridge.  Not a bad investment.

---

### Post by foxxman on 2009-12-13
that happened to me two but in many cases i just reinstalled the driver till it lit up.and it works fine now. it works if you have the NETWPN111.inf with the.sys files. if you google it it may be the first few links that the files are able to be downloaded. goodluck

---

