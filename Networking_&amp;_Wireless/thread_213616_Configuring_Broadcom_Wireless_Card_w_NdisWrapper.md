---
title: "Configuring Broadcom Wireless Card w/ NdisWrapper"
date: 2006-07-11
forum: Networking &amp; Wireless
---

### Post by jeelliso on 2006-07-11
Hello,

I am trying to configure my Broadcom wireless card using NdisWrapper.
Here is the lspci output regarding my wireless card:```
0000:05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```Here is the output from lspci -n regarding the wireless card```
0000:05:02.0 0280: 14e4:4318 (rev 02)
```I am running Ubuntu 6.06 and here is the output of uname -a```
Linux MarUbuntu 2.6.15-25-386 #1 PREEMPT Wed Jun 14 11:25:49 UTC 2006 i686 GNU/Linux
```I hope this gives enough information regarding my system.

I followed the instructions [here]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28WifiDocs%2FDriver%29") from the Ubuntu site, but here is my problem  even after the reboot following ndiswrapper installation and configuration: there is no 'wlan0' device interface; the 'Wireless connection' is shown as 'eth1' from the Network Settings GUI.  So when I try to 'ifconfig eth1 up' I get the following error```
#sudo ifconfig eth1 up
SIOCSIFFLAGS: No such file or directory
```The corresponding message logged through dmesg shows```
[17181793.732000] bcmw43xx: Error: Microcode "bcmw43xx_microcode5.fw" not available or load failed.
```Any help would be appreciated; I will be monitoring the thread actively so if you need any more information I will be around to give it.

Thanks in advance,
~Justin

---

### Post by MarkSheely on 2006-07-11
Justin,

The best method seems to be this one here:

[http://www.ubuntuforums.org/showthread.php?t=197102](http://www.ubuntuforums.org/showthread.php?t=197102)

If you have any more problems after trying this, you might try posting over in that thread.  That is where most BCM4318 users seem to be congregating to help one another out.  

Stick with it - 

--Mark

---

### Post by jeelliso on 2006-07-11
Thanks Mark.  I wonder why I didn't find this thread when searching.  I guess I didn't try hard enough.

~Justin

---

