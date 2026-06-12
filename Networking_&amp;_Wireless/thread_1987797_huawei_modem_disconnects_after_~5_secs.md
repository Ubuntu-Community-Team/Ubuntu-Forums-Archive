---
title: "huawei modem disconnects after ~5 secs"
date: 2012-05-26
forum: Networking &amp; Wireless
---

### Post by sphCow on 2012-05-26
The problem is that my Huawei 3G USB modem E352 is being detected, I can connect through it, but after a few seconds it disconnects and the modem disappears from network manager. Then I usually disconnect and reconnect the modem to the USB port, and the same thing happens over and over. 

I tried two versions of Mobile Partner (aka the Huawei Dashboard). First of them fails to install NDIS driver (may be ubuntu 12.04 is incompatible) but installs Mobile Partner, so I can connect through MP and browse through Firefox but ubuntu detects no network connection so update/ software center do not work. The second version is called something like "BAM Huawei", that installs but the MP interface often hangs, fails to detect modem etc. So, both the two are useless.

I went through some useful threads at Ubuntu Forums where people have discussed about Huawei modem problems, but in most of the cases their modem were undetected, while mine is detected even it connects then disconnects. That's peculiar. Someone suggested to choose CHAP or PAP protocol only. I tried but that was no good. I have an android phone, Samaung Galaxy Mini, I can connect though its modem without any problem. But Huawei fails always. Any workaround?

---

### Post by p1977p on 2012-07-01
Solved the problem without reinserting the modem. follow the steps below:

1)  Install usb_modeswitch if not already installed.

2) run   ```
 usb-devices 
``` in terminal. you should get a output showing something like this:


> T:  Bus=01 Lev=01 Prnt=01 Port=04 Cnt=01 Dev#=  5 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1436 Rev=00.00
S:  Manufacturer=HUAWEI Technology
S:  Product=HUAWEI Mobile
C:  #Ifs= 7 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 1 Cls=02(commc) Sub=06 Prot=ff Driver=(none)
I:  If#= 2 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=(none)
I:  If#= 3 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 4 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 5 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 6 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

Note that interface number 2 is data interface. Also note vendor code 12d1 and product ID 1436 for your modem. (these may differ)

3) run ```
sudo usb_modeswitch -v 12d1 -p 1436 -i 2 -R
``` in terminal
you should get something like this:> 
 $ sudo usb_modeswitch -v 12d1 -p 1436 -i 2 -R

Looking for default devices ...
   found matching product ID
   adding device
 Found device in default mode, class or configuration (1)
Accessing device 005 on bus 001 ...
Getting the current device configuration ...
 OK, got current device configuration (1)
Using first interface: 0x02
Using endpoints 0x01 (out) and 0x82 (in)
Not a storage device, skipping SCSI inquiry

USB description data (for identification)
-------------------------
Manufacturer: HUAWEI Technology
     Product: HUAWEI Mobile
  Serial No.: not provided
-------------------------
Warning: no switching method given.
Resetting usb device .
 OK, device was reset

Now it should show up in Networkmanager applet in taskbar. Click to connect.

---

### Post by p1977p on 2012-10-14
I have made improvements since  the last reply and now have a script that can do the job automatically. Please read this new post of mine:

[http://ubuntuforums.org/showthread.php?p=12294889](http://ubuntuforums.org/showthread.php?p=12294889)

---

