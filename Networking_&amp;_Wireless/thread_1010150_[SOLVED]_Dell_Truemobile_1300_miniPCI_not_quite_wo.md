---
title: "[SOLVED] Dell Truemobile 1300 miniPCI not quite working"
date: 2008-12-13
forum: Networking &amp; Wireless
---

### Post by ieee488 on 2008-12-13
the result of *iwconfig* shows:

> lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I am using ndiswrapper.

I know there are one or two unsecured networks near me, and I use them to verify that this is working, but I don't know how to scan for them.

In Windows XP, the card is automatically started. Is that my problem?

It's Broadcom 4306 chipset.


> sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 01
       serial: 00:0d:56:6d:09:95
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 duplex=full firmware=5705-v3.11 ip=192.168.1.45 latency=32 link=yes mingnt=64 module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:01:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:1d:fc:93
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g


>  lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3580] (rev 02)
00:00.1 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3584] (rev 02)
00:00.3 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3585] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
00:02.1 Display controller [0380]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 81)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 01)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 01)
01:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet [14e4:165d] (rev 01)
01:01.0 CardBus bridge [0607]: Texas Instruments PCI7510 PC card Cardbus Controller [104c:ac47] (rev 01)
01:01.1 CardBus bridge [0607]: Texas Instruments PCI7510,7610 PC card Cardbus Controller [104c:ac4a] (rev 01)
01:01.2 FireWire (IEEE 1394) [0c00]: Texas Instruments PCI7410,7510,7610 OHCI-Lynx Controller [104c:802b]
01:01.3 System peripheral [0880]: Texas Instruments PCI7410,7510,7610 PCI Firmware Loading Function [104c:8204]
01:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)


---

### Post by Ayuthia on 2008-12-13
Are you able to see any wireless sites when you use:
```
sudo iwlist scan
```

---

### Post by ieee488 on 2008-12-13
This is part of the response I get to that command :

wlan0     Interface doesn't support scanning : Network is down

---

### Post by Ayuthia on 2008-12-13
Please try and see if this helps:
```
sudo modprobe -r b43 b43legacy ssb ndiswrapper
sudo modprobe ndiswrapper
sudo iwlist scan
```
It looks like the b43legacy module is still active.  The commands above will remove the module (for this session only) and reload ndiswrapper.  Let us know if you are able to see any sites after this.

---

### Post by ieee488 on 2008-12-13
Yes! The scan works!

Then I went one step further,
I edited */etc/modprobe.d/blacklist* and
blacklisted b43, b43legacy, and ssb, (bcm43xx was already blacklisted) and rebooted, > sudo iwlist scan failed again.

It seems the sequence is off somehow.

What am I doing wrong.

I already added ndiswrapper to */etc/modules*

---

### Post by Ayuthia on 2008-12-13
You can try:
```
sudo update-initramfs -u
```and it should update the files in initramfs for the blacklist and module files.

The other option is to try:
```
echo -e '#b43legacy workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b43legacy ssb wl; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS;' | sudo tee -a /etc/modprobe.d/ndiswrapper
```

---

### Post by ieee488 on 2008-12-13
I ran the first command you suggested and rebooted. Ran *sudo iwlist scan* but still got the [COLOR="DarkRed"]wlan0 Interface doesn't support scanning : Network is down [/COLOR].

Then I ran the second command you suggested and rebooted.
BINGO! Worked.

I know that a line was added to /etc/modprobe.d/ndiswrapper file.
Can you briefly explain what it does?

Thank you so much for your help.

---

### Post by Ayuthia on 2008-12-13
> **ieee488 said:**
> I ran the first command you suggested and rebooted. Ran *sudo iwlist scan* but still got the [COLOR="DarkRed"]wlan0 Interface doesn't support scanning : Network is down [/COLOR].

Then I ran the second command you suggested and rebooted.
BINGO! Worked.

I know that a line was added to /etc/modprobe.d/ndiswrapper file.
Can you briefly explain what it does?

Thank you so much for your help.

All it does is the same thing as those commands listed before.  What happens is when ndiswrapper is loaded, the first thing it will do is remove b43, b43legacy, ssb, and wl modules.  Once that is done, it will then load ndiswrapper.  /etc/modprobe.d/ndiswrapper is a file that has some rules for when the ndiswrapper module is being loaded or unloaded.

---

### Post by ieee488 on 2008-12-13
Just curious.

Why didn't the blacklisting via /etc/modprobe.d/blacklist work?

Is it because of order that certain files are processed?

---

### Post by Ayuthia on 2008-12-13
> **ieee488 said:**
> Just curious.

Why didn't the blacklisting via /etc/modprobe.d/blacklist work?

Is it because of order that certain files are processed?

It is not so much about the order of the files being processed, but how things are being loaded into memory when the system is booting up.  At least that is what it looks like to me.  There is a file system that is used when the system is booting up called initramfs that loads things that the system needs when it starts up.  The problem is that it has its own blacklist file that it keeps.  If the modules have not been blacklisted in that file, then it will load.  Once it is loaded, the blacklist files cannot remove them (they just prevent the module from loading).

I am still trying to understand how to update the blacklist files in initramfs.  I thought it was sudo update-initramfs -u that would update it, but when you did it, it did not happen.  I will have study it some more.

---

### Post by ieee488 on 2008-12-13
I am just happy that you helped me to get it to work. :)

I now know that I didn't quite follow the sequence in 
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper).
I skipped over step 3.1.

I wonder if somehow that messed things up.

Anyway, it's great to have the wireless card working on this laptop. 

My next project is to look into using Sierra Wireless AirCard 860 with Ubuntu for mobile broadband on AT&T.

---

