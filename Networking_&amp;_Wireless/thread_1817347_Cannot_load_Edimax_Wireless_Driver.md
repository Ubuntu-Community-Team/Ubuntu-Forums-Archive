---
title: "Cannot load Edimax Wireless Driver"
date: 2011-08-03
forum: Networking &amp; Wireless
---

### Post by LorraineO on 2011-08-03
I have just bought an Edimax EW-7711UTn wireless adaptor with CD. I have the Linux folder on the CD. Folder name 2009_0525_RT3070_Linux_STA_v2.1.1.0. 
How do I install from this folder
Step by step instructions would be much appreciated.:confused:

Lorraine

---

### Post by chili555 on 2011-08-03
Maybe there is an easier way. Please open a terminal and run and post:```
lsusb
uname -r
lsmod | grep rt2
```We only need to see the line for your wireless device, evidently a Ralink.

The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by LorraineO on 2011-08-04
Here is the readout from terminal. with the Edimax in USB port no access to internet.
  	 	 	 	p { margin-bottom: 0.21cm; }  xxxxxxxx-linux:~$ lsusb 
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 003 Device 003: ID 046d:c05a Logitech, Inc.  
 Bus 003 Device 002: ID 062a:0201 Creative Labs Defender Office Keyboard (K7310) S Zodiak KM-9010 
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 001 Device 005: ID 7392:7711   
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 xxxxxxxx-linux:~$ uname -r 
 2.6.32-33-generic 
 xxxxxxxx-linux:~$ lsmod | grep rt2 
 rt2870sta             461843  0  
 rt2800usb              31531  0  
 rt2x00usb               9703  1 rt2800usb 
 rt2x00lib              27573  2 rt2800usb,rt2x00usb 
 mac80211              205402  3 rt2x00usb,rt2x00lib,rtl8187 
 led_class               2864  2 rt2x00lib,rtl8187 
 cfg80211              126144  3 rt2x00lib,rtl8187,mac80211 
 crc_ccitt               1339  2 rt2800usb,irda 
 



 Here is a report with access using my Netgear adaptor

xxxxxx-linux:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 046d:c05a Logitech, Inc. 
Bus 003 Device 002: ID 062a:0201 Creative Labs Defender Office Keyboard (K7310) S Zodiak KM-9010
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 0846:4260 NetGear, Inc. WG111(v3) 54 Mbps Wireless [RealTek RTL8187B]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
xxxxxx-linux:~$ uname -r
2.6.32-33-generic
lorraine@lorraine-linux:~$ lsmod |grep rt2
rt2870sta             461843  0 
rt2800usb              31531  0 
rt2x00usb               9703  1 rt2800usb
rt2x00lib              27573  2 rt2800usb,rt2x00usb
mac80211              205402  3 rt2x00usb,rt2x00lib,rtl8187
led_class               2864  2 rt2x00lib,rtl8187
cfg80211              126144  3 rt2x00lib,rtl8187,mac80211
crc_ccitt               1339  2 rt2800usb,irda


xxxxx replaces my logon

Lorraine

---

### Post by chili555 on 2011-08-04
> with the Edimax in USB port no access to internet.
<snip>
Bus 001 Device 005: ID 7392:7711

xxxxxxxx-linux:~$ lsmod | grep rt2
rt2870sta 461843 0
[COLOR="Red"]rt2800usb[/COLOR] 31531 0
[COLOR="Red"]rt2x00usb[/COLOR] 9703 1 rt2800usb
[COLOR="Red"]rt2x00lib[/COLOR] 27573 2 rt2800usb,rt2x00usb
mac80211 205402 3 rt2x00usb,rt2x00lib,rtl8187
led_class 2864 2 rt2x00lib,rtl8187
cfg80211 126144 3 rt2x00lib,rtl8187,mac80211
crc_ccitt 1339 2 rt2800usb,irda
You have a little conflict going there. Please open a terminal and do:```
sudo su
echo "blacklist rt2800usb" >> /etc/modprobe.d/blacklist.conf
exit
```Leave the Edimax inserted, reboot and let us have your report.

---

### Post by LorraineO on 2011-08-05
Followed inst. re-booted and I am connected .:D:D
Thanks for your help.

---

### Post by chili555 on 2011-08-05
You are very welcome. Would you please use thread tools at the top and Mark Solved?

---

