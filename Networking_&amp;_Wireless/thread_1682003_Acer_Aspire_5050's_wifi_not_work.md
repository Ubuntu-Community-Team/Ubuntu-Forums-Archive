---
title: "Acer Aspire 5050's wifi not work"
date: 2011-02-05
forum: Networking &amp; Wireless
---

### Post by ikckc on 2011-02-05
Fresh install Ubuntu 10.10 on Acer Aspire 5050 with new hard drive.

I struggled to turn the Wifi's button turn on but led light always on. It does not detect wifi driver.
I installed ndiswrapper to get Acer's Winxp driver: netathr.inf by Windows Wireless Drivers from Ubuntu Software download. It's same thing as ndiswrapper.

Code for ndiswrapper -l:> 

WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
netathr : driver installed
    device (168C:001A) present (alternate driver: ath5k)
Code for iwconfig:
> 
lo        no wireless extensions.

eth0      no wireless extensions.

 Code for iwconfig wlan > 
wlan      No such device
Code for  lspci -v > 
08:04.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
    Subsystem: AMBIT Microsystem Corp. Device 0418
    Flags: bus master, medium devsel, latency 80, IRQ 11
    Memory at c0200000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel modules: ath5k
Code for uname -a:
>  
Linux madaparthi-Aspire-5050 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:48 UTC 2011 i686 GNU/Linux
That mean there is no device in my laptop? How to enable the device without button to turn on if the driver is already install? Anyone can explain and help me please??

Thanks

---

### Post by ikckc on 2011-02-05
I forget to add...It's AR5005G driver that means AR2413 chipset.

I did look up some forums and did through their tutorial. Some sites are not reach and some are not reach the download madwifi. :mad: It's not working or maybe it's me in wrong process because I am new to Ubuntu.
 :confused: I am so confuse if the situations are similar to mine but I want to start over and clear the steps for myself.

---

### Post by ebasa on 2011-02-05
I have the same exact Model and wireless works out of the box on my 10.4

---

### Post by ikckc on 2011-02-06
Nevermind, now it's working after I erase hard drive again and reinstall Ubuntu. It's works. Werid!
but I noticed that It's different kernal.

Code for uname -a:
> Linux madaparthi-Aspire-5050 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686 GNU/Linux
It was 2.6.35.25-generic #44-Ubuntu.

Should not I update the ubuntu?

---

