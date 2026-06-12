---
title: "Wireless connection not connecting"
date: 2006-05-03
forum: Networking &amp; Wireless
---

### Post by BrainToad on 2006-05-03
Linux Newb here.  Hopefully I can word this right.

Just got Ubuntu installed, first time having Linux on an actual hard drive (have used Knoppix Live CD before).  But I'm having some internet issues.

I installed on a Dell Inspiron 2200 Laptop with a wireless card (not sure on the model number, but I'm sure I can find out somehow) and I'm trying to connect to my 2Wire Homeportal 1000SW.

I tried setting up my network stuff in the install, and it didn't work, so I waited until I got Ubuntu all the way in to try my luck again, but I still can't get it to work.  I know the router allows DHCP because I've used it before, but when I try to use it with Ubuntu, it doesn't get any signal back.  So I put in the stuff manually, double and triple checking all numbers, trying different numers, etc.  And no such luck.

Previously I've had problems with it on Knoppix as well, but I fixed that by having to put some stuff in manually, then redo the DHCP announcing and it finally worked.  But that was with KDE.

So any help would be appreciated and sorry if this was confusing, I'll try to clarify anything.

---

### Post by brallan on 2006-05-04
is it a pcmcia card? if so post ```
lspci
```.

what do you get for ```
iwconfig
```?

---

### Post by BrainToad on 2006-05-04
Not sure if its PCMIA or not, it's a Mini PCI, name is Dell Wireless 1470 Dual Band WLAN

lspci results:
0000:00:00.0 Host bridge: Intel Corp. Mobile Memory Controller Hub (rev 03)
0000:00:02.0 VGA compatiable controller: Intel Corp. Mobile Graphics Controller (rev 03)
0000:00:02.1 Display Controller: Intel Corp. Mobile Graphics Controller (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB 2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3)
0000:00:1e.2 Multimedia audio controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
0000:00:1e.3 Modem: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6M) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE Interface: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:00:1f.3: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:02:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
0000:02:03.0 Network Controller: Broadcom Corporation: Unknown Device 4319 (rev 02)
0000:02:08.0 Ethernet controller: Intel Crop.: Unknown device 1068 (rev03)


iwconfig results:
lo        no wirelss extensions
eth0    no wireless extensions
sit0     no wireless extensions

Hope that's what you need, sorry for any typos.

---

### Post by BrainToad on 2006-05-04
EDIT:

New problems.  Following the guide at [https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto)
I get to the step where I run ifconfig and iwconfig to see if my wireless card shows up and still doesn't show up, even after having the driver installed.

---

