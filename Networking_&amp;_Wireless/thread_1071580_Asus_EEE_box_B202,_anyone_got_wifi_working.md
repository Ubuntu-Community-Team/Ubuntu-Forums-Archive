---
title: "Asus EEE box B202, anyone got wifi working?"
date: 2009-02-16
forum: Networking &amp; Wireless
---

### Post by matthew_exon on 2009-02-16
Hi,

I just bought an Asus EEE box B202, and I've installed Intrepid Ibex on it.  As with seemingly every computer I've ever tried to install any distribution of Linux on, it's got an Ralink wifi driver which is a total pain to get working...

I'm using these instructions here:

[http://ubuntuforums.org/showthread.php?t=563547](http://ubuntuforums.org/showthread.php?t=563547)

I downloaded the windows wifi drivers from Asus's web site.  I installed them using ndiswrapper -i, and now I have these:

```
root@Winter:/etc/ndiswrapper/rt2860# cksum rt*
222794296 43754 rt2860.inf
287247444 572416 rt2860.sys

```
And it appears to work:

```
root@Winter:~# ndiswrapper -l
rt2860 : driver installed
	device (1814:0781) present

```
Here's the PCI info, in case it's useful:

```
03:00.0 Network controller: RaLink Device 0781
	Subsystem: RaLink Device 2790
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at fe7f0000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/5 Enable-
	Capabilities: [70] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Kernel driver in use: ndiswrapper

```
I can now see the device in gnome-network-admin, and it sees my local network's ESSID and understands that it uses WEP and needs a key.  So it's doing something right.  The only problem is that it doesn't actually connect at all.  When I use ifup, it fails to get a DHCP address:

```
root@Winter:~# ifup wlan0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:15:af:ba:aa:99
Sending on   LPF/wlan0/00:15:af:ba:aa:99
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

dmesg shows me this:

```
[ 1177.321436] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```
I've seen this same effect when I had the wrong password, but I'm pretty sure my password is correct: I can connect to the network using a different Linux machine, and the EEE box can connect to the network using Windows.  The password is ten numbers, and I've tried it both as a hexadecimal password and as an ASCII password, even though it's surely hexadecimal.  Always the same result.

From trying this with other computers I believe that an ndiswrapper driver can appear to work, but actually be the wrong driver.  At least, downloading a driver for the same device from a different manufacturer sometimes makes a difference.  So if there's anyone with a working wifi driver, could they post the checksums of their .inf and .sys files, and let me know where they got them from?

By the way, I just tried installing the EEE packages from array.org.  No improvement, although my attempts at ndiswrapper might have interfered with things.  I did notice that there is an alternate driver now, rt2860sta.  But rmmod ndiswrapper and modprobe rt2860sta results in pretty much the same situation: it can see the network, but not connect to it.  This time dmesg shows:

```
[  757.760052] ra0: no IPv6 routers present

```
If I use array.org, should I be using ndiswrapper still, or native drivers?

Thanks for any help,
Matthew Exon

---

### Post by Aarookie on 2009-02-16
try this
Open a terminal and enter these commands:
(this is also assuming like me the target computer has no way of getting to the internet, if you have RJ45 plugged in or some alternate method of connecting to internet you can skip first step.

1. Insert your Ubuntu cd and open terminal
2.sudo apt-cdrom add
3.sudo apt-get install build-essential (Not sure this part is necessary but it sure was for proper tarballing when I was trying to install multiple tar.gz files.
4.sudo apt-get install ndisgtk

5.Open system>administration>Windows wireless drivers menu/program.
6.My computer sort of stuttered at this point but eventually a little window opened up and I was able to browse to my .inf file from winxp driver.
7.For some reason configure network didn't work at this point the unlock button was greyed out, also mouse pointer was skipping a few beats every so often but after a restart I am able to click on my 2 little computers in the gnome task bar and attempt to connect to my network same way I have done on my laptop here. At this point however I was unable to connect to wpa type network, switched router back to wep and hooked right up
I'm on 32 bit computer, not sure if this will work in 64 bit environment, my bro's computer wouldn't accept 32 bit driver with this method, and his card doesn't have 64 bit windows' drivers

---

### Post by matthew_exon on 2009-02-16
I do have wired net access, which is lucky since I don't have a CD drive.  I have no way of accessing the driver on the CD.

I tried all of your suggestion but with the driver I've got.  Ndisgtk is nifty, but it seems to get me to exactly the same situation I was in before.  I confirm that the unlock button was greyed out, so I rebooted.  The two little computers icon has everything greyed out, including the wired network (which works).  Says "device is unmanaged".  Using gnome-network-admin I can see my network and try to connect to it, but as usual it fails in DHCP.

What kind of computer are you using?  Is it an EEE family machine?

By the way, it just occurred to me to try the drivers that are already installed on the Windows partition.  But I get exactly the same result.  The checksums for those are:

```
2978032819 637824 /etc/ndiswrapper/rt2860/rt2860.sys
914440711 60365 /etc/ndiswrapper/rt2860/rt2860.inf
```

---

### Post by matthew_exon on 2009-02-19
This is resolved, sortof.  I bought another router, and found that I can connect to it no problems.  My guess is that Ubuntu can't cope with some setting on the router, something to do with WEP maybe.  Which is bad.  But at least I'm up and running.

---

### Post by matthew_exon on 2009-02-20
OK, now it seems to be properly resolved.  I got home just now to find my new router was suddenly behaving like my old router: I could see it, but DHCP failed.  After finding this thread:

[http://ubuntuforums.org/showthread.php?t=970236](http://ubuntuforums.org/showthread.php?t=970236)

...I tried Wicd, and found that not only could I connect to my new router again, but also to the old one.  Something somewhere is badly wrong with network-manager or gnome-network-manager, but there are already plenty of people shouting about this.  And in the meantime, I'm happy.

---

