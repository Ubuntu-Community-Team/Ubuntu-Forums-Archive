---
title: "Just installed Jaunty RC -NO WiFi"
date: 2009-04-21
forum: Networking &amp; Wireless
---

### Post by chicagofog on 2009-04-21
It worked fine with Intrepid.
Now I have now wireless. Any ideas?


wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.417 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


lspci: 05:0a.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

---

### Post by RedSingularity on 2009-04-21
Did you try reinstalling drivers?

---

### Post by chicagofog on 2009-04-21
More info:

root@SOUNDWAVE:~$ sudo ifconfig wlan0 
wlan0     Link encap:Ethernet  HWaddr 00:11:50:50:89:ff  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

root@SOUNDWAVE:~$ sudo ifconfig wlan0 down
root@SOUNDWAVE:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: No such file or directory
root@SOUNDWAVE:~$

So, basically it "kind of" sees the card. but I cannot bring the interface up.

---

### Post by chicagofog on 2009-04-21
I'm not 100% sure how to reinstall the drivers.

---

### Post by iswear on 2009-04-21
If you need the drivers you can get them [Here]("http://ubuntuforums.org/showthread.php?t=201902")

---

### Post by chicagofog on 2009-04-21
Well this is exactly why I don't use Linux. I want my install to work. This Broadcom card is nearly 3 years old. There is no reason why it shouldn't work after the install. I followed all those steps (there were many) and it did not work. Unreal. I spent 5 hours working on a wifi card driver with no results...just like I did in the Mandrake world a decade ago. I'm hooking up the other HDD and once again feeling as though Ubuntu\Linux is not ready for prime time. IMHO

---

### Post by iswear on 2009-04-21
You should take a look at [this]("http://ubuntuforums.org/showthread.php?t=489126") just follow the steps that kevdog posted.

---

### Post by kevdog on 2009-04-21
Just a clarification to the original poster.  Drivers as you call them are actually kernel modules.  That means anytime you go to a new kernel (such as in the case of moving from intrepid to jaunty) you need to reinstall the kernel modules.  This means previously installed kernel modules or drivers need to reinstalled into the new kernel. If you dont want to do this, when booting - select the old kernel in grub during the first few seconds of the boot process.  Again with linux there are internal and external kernel modules. Internal modules come with the kernel, external ones the user adds later (such as ndiswrapper).  Some modules are dropped and no longer supported and others are added with each new kernel.  Hence internal modules may change with each new release(example intel video driver i810).  External kernel modules always have to be reinserted or reinstalled with each kernel upgrade.

I hope I made myself clear.

---

### Post by chicagofog on 2009-04-22
> **kevdog said:**
> Just a clarification to the original poster.  Drivers as you call them are actually kernel modules.  That means anytime you go to a new kernel (such as in the case of moving from intrepid to jaunty) you need to reinstall the kernel modules.  This means previously installed kernel modules or drivers need to reinstalled into the new kernel. If you dont want to do this, when booting - select the old kernel in grub during the first few seconds of the boot process.  Again with linux there are internal and external kernel modules. Internal modules come with the kernel, external ones the user adds later (such as ndiswrapper).  Some modules are dropped and no longer supported and others are added with each new kernel.  Hence internal modules may change with each new release(example intel video driver i810).  External kernel modules always have to be reinserted or reinstalled with each kernel upgrade.

I hope I made myself clear.

It was a clean install. Intrepid was blown away before Jaunty.

---

