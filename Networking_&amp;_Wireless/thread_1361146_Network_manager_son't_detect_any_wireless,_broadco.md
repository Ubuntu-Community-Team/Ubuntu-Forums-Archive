---
title: "Network manager son't detect any wireless, broadcom driver not currently in use"
date: 2009-12-21
forum: Networking &amp; Wireless
---

### Post by The Glidd on 2009-12-21
I Recently upgraded to 9.1

Installed bcml.kernel, etc.

Broadcom STA shows up under Admin>Drivers>Hardware Drivers, it reads:

"This driver is activated but not currently in use"

I remove and reinstall and am asked to reboot.  There's no change.  The above status remains the same.  

Along with this, network manager detects no wireless at all.  I know the wireless is on; it works fine in the Vista partition.

Any help would be appreciated!

---

### Post by The Glidd on 2009-12-21
Also, here's info from lspci:

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

And from iwconfig:

lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by PRC09 on 2009-12-21
The following link might be helpfull....

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by The Glidd on 2009-12-22
I checked out the link.  Still no solution!

I have b43-fwcutter installed, but the b43 doesn't show up under hardware drivers (it used to, back before the wireless disappeared altogether.  The wireless actually did work with 9.1 for a few hours a few days ago).  

Also, here's what I've got for ifconfig (if it makes any difference)

eth0      Link encap:Ethernet  HWaddr 00:25:64:49:af:58  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::225:64ff:fe49:af58/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26397 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26325 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14805615 (14.8 MB)  TX bytes:11778702 (11.7 MB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:60022 errors:0 dropped:0 overruns:0 frame:0
          TX packets:60022 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10707460 (10.7 MB)  TX bytes:10707460 (10.7 MB)

---

### Post by PRC09 on 2009-12-22
This post is listed as solved so maybe some help for you there.Also if you search the forums there are lots of posts for this card.I am not running 9.10 or that wireless card so hope this helps.




[http://ubuntuforums.org/showthread.php?t=1309760&highlight=broadcom+4312](http://ubuntuforums.org/showthread.php?t=1309760&highlight=broadcom+4312)

---

### Post by bkratz on 2009-12-22
This is still a very active thread regarding your card.  It seems to be closely monitored with answers readily obtained.  You could just tag along the end of it and get your answers.

[http://ubuntuforums.org/showthread.php?t=1266620](http://ubuntuforums.org/showthread.php?t=1266620)

---

