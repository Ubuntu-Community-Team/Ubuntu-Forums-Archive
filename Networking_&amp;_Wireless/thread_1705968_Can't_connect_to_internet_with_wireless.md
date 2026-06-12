---
title: "Can't connect to internet with wireless"
date: 2011-03-13
forum: Networking &amp; Wireless
---

### Post by thamalm on 2011-03-13
Hi,
I'm a new Ubuntu user (running Ubuntu x64 ).
I can connect to the Internet if I use my Ethernet cable but not using wireless.
My wireless card/device is..```

Broadcom Corporation BCM4313 802.11b/g LP-PHY 
```What do I do?

---

### Post by cpezie on 2011-03-13
Yep, i'm in the same boat.

I've got an older HP dv1000.  I had Vista installed previously and wireless worked fine.  I installed Ubuntu 10.10 yesterday and now I can only get network access via ethernet.  

Ubuntu found and installed Broadcom B43 wireless driver.  Also states this driver is activated and currently in use.

I don't even see available networks and I know there are plently in my area.

Thanks in advance,

---

### Post by Shriner on 2011-03-13
Found another thread, that reports that if you are using a kernel before  2.6.34 this problem occurs. It is reported that manually updating your  kernel to 2.6.34 will cure the drops with all wireless cards. I'm not  willing to verify this at this time because my ISP has oversold their  DSL capablities and my connection sucks at this time. I guess I'm  fortunate that I have a WET-11 to use in the interim.

Instructions for manually updating your kernel can be found @
[https://wiki.ubuntu.com/KernelTeam/GitKernelBuild]("http://ubuntuforums.org/view-source:https://wiki.ubuntu.com/KernelTeam/GitKernelBuild")

You can determine your current kernel with uname -a

---

### Post by Shriner on 2011-03-13
Another thing that might work is checking to see if the wlan is in power saving mode. Check with "iwconfig", if power saving is on disable with "sudo iwconfig wlan0 power off". Assuming that your wireless is wlan0.

---

### Post by cpezie on 2011-03-13
well I started building the kernel before seeing your most recent message.  But here's the results of the iwconfig.

cp@cp-HP-Pavilion-dv1000-DZ677AV-ABA:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:ff/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:ff   Fragment thr:ff
          Power Management:ff

---

### Post by cpezie on 2011-03-13
Looks like my issue isn't related to the kernel.  I'm running 2.6.35-27-generic #48-Ubuntu

---

### Post by thamalm on 2011-03-14
Please don't try and hijack my thread.

---

### Post by cpezie on 2011-03-14
> **thamalm said:**
> Please don't try and hijack my thread.
 
 
Sooo you think it makes sense for me to create a duplicate thread for the same issue?
 
OK, how about this.  I'll go check the forum guidelines and if they suggest that your thought process makes sense then I will create a duplicate thread for myself.

---

