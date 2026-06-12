---
title: "Wireless Internet Problems"
date: 2009-04-19
forum: Networking &amp; Wireless
---

### Post by Brennon on 2009-04-19
This discussion has probably been exhausted in other threads but I just can't seem to get my internal wireless card (Broadcom BCM 4306 802.11b/g) to communicate with a Cisco Linksys Router WRT54G2.  Ubuntu recognized and activated the driver.  I don't know what I am doing wrong.  I've noticed when I go to my router setup screen (192.168.0.1) that the Host and Domain name fields are blank.  Should they have information in these?  When I plug the ethernet cable from the router the laptop, the internet works fine.

I am using an Emachine M6410 laptop.  Any help will be greatly appreciated!

Brennon

---

### Post by StuartN on 2009-04-19
Assuming that your network interface has been detected (it should appear when you do "lspci" in a terminal) type "sudo iwlist scanning" and your access point should appear in the list of detected networks. When you manage to connect then the access point and wireless adapter should be associated when you type "sudo iwconfig", but post the output from that as it might help.

---

### Post by Brennon on 2009-04-19
This is what I get when I type "sudo iwlist scanning":

> lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results


And when I put in "sudo iwconfig", this pops up:

> lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr: off   Fragment thr=2352 B   
          Encryption key: off
          Power Management: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Now what?

---

### Post by divague on 2009-04-19
I had that same problem with the router, the first time i configured it only worked when i plugged my laptop so I pressed the reset button and reconfigured it and it worked. (i have the same router and wireless card model). The Domain and Host name fields are blank in mine too. Have you tried connecting to other wireless networks? maybe the drivers aren't working.

---

### Post by Brennon on 2009-04-19
divague, 

I have not tried it on other networks.  I will trying reseting the router, though.  I just hope I can get this cleared up.

---

### Post by Brennon on 2009-04-21
I still haven't figured out how to get my wireless internet to work.  Please help or I may go back to Windows XP.

---

### Post by divague on 2009-04-22
Have you tried connecting to other wireless networks? Maybe your wireless card is not working right.

---

### Post by Brennon on 2009-04-22
I have not other networks to try on.  My wife's laptop connects easily to our wireless internet.  When I enter in the commands into terminal that you recommended,  this is what I get:

> 
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
01:05.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
01:06.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
01:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
brennon@brennon-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

brennon@brennon-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@0000:01:06.0
       logical name: eth0
       version: 01
       serial: 00:03:25:0d:71:06
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.0.100 latency=64 module=ssb multicast=yes
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:01:09.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 46:5b:cb:64:b7:cc
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:90:96:8a:de:b5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

---

### Post by Ayuthia on 2009-04-22
Can you try the following in the Terminal:
```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode Managed
sudo ifconfig wlan0 up
sudo iwlist scan

```
From your earlier post, it looks like your card was in ad-hoc mode.  Hopefully this will switch it over to Managed mode and get your card working.

---

