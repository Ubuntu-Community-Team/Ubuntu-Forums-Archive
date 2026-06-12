---
title: "Operation not Supported : can't Set RTL8187 to Ad-hoc or AP"
date: 2012-06-02
forum: Networking &amp; Wireless
---

### Post by Gelai on 2012-06-02
I've been trying for 1 month, setting up my RTL8187 USB Wireless Antenna to Act as an Access Point or Ad-hoc. i've install compat-wireless driver and hostpd on my laptop but still it won't work as what i wanted. anyone can give or bring me to the right path of how do get this thing work.. your prompt response is Highly Appreciated! Thank you very much.. =)

---

### Post by chili555 on 2012-06-02
I hope this helps: [http://linuxwireless.org/en/users/Drivers/rtl8187](http://linuxwireless.org/en/users/Drivers/rtl8187)> [B]not working yet
[/B]
    AP/Master mode It says that ad-hoc is working in Linux 3.4; the newest kernel in Ubuntu 12.04 is 3.2-xx.

I think it means what it says, the operation is not supported.

---

### Post by Gelai on 2012-06-03
> **chili555 said:**
> I hope this helps: [http://linuxwireless.org/en/users/Drivers/rtl8187](http://linuxwireless.org/en/users/Drivers/rtl8187)It says that ad-hoc is working in Linux 3.4; the newest kernel in Ubuntu 12.04 is 3.2-xx.

I think it means what it says, the operation is not supported.


No Possible Way!??? :( :( :( :( :(  im really frustrated with this.. :( if somebody has an idea please help with this..

---

### Post by Gelai on 2012-06-04
Can somebody Give an idea of What USB Wireless Antenna is Supported and Working as an AccessPoint/Ad-hoc mode in UBUNTU 11.10--3.0.0-12-generic. Thank you very much..

---

### Post by Gelai on 2012-06-05
Now, Im going to try using Oneiric Server i386 and upgrade the kernel to 3.4 and wait for the results.. anyone please give me an Idea.! 

I've tried updating my 3.0.0-12 to 3.4 yesterday and my machine just teared-down. and tried also quantal, but it still unstable for me (im excited for the final release of this ver. of ubuntu  \m/ :D ) and now, i came up with an idea to fresh install the 11.10 and update to 3.4 kernel.. i really feel that im messing around,, anyone can guide me to get my RTL8187 USB Wireless use as an AP/Ad-hoc....??   Thanks!

---

### Post by chili555 on 2012-06-05
> **Gelai said:**
> Can somebody Give an idea of What USB Wireless Antenna is Supported and Working as an AccessPoint/Ad-hoc mode in UBUNTU 11.10--3.0.0-12-generic. Thank you very much..Please see here: [http://wireless.kernel.org/en/users/Drivers/zd1211rw](http://wireless.kernel.org/en/users/Drivers/zd1211rw)> Monitor mode working

Master mode working

Ad-hoc mode working And also here: [http://wireless.kernel.org/en/users/Drivers/zd1211rw/devices](http://wireless.kernel.org/en/users/Drivers/zd1211rw/devices)

Note that some of these devices are V.1 or some such; if you buy a version 2, it's probably a different chipset.

---

