---
title: "Wireless help ASUS P5KPL-CM"
date: 2010-10-22
forum: Networking &amp; Wireless
---

### Post by magtrask on 2010-10-22
Hi, just switched my ASUS P5KPL-CM desktop over from XP to 10.04
On XP I was using to my Netgear Wireless-N 300 Router. 
Now, Auto Eth0 line no problem, but I have no option to "enable wireless"
I tried to follow another users thread.  I've installed the Windows Wireless Driver app, and downloaded the card info from [http://support.asus.com/download/download.aspx?product=1&SLanguage=us-en&type=map&model=P5KPL-CM](http://support.asus.com/download/download.aspx?product=1&SLanguage=us-en&type=map&model=P5KPL-CM)
I tried to unrar, but I don't see any inf files to use.
But I don't really know what I'm doing or if the above is necessary in my situation, so I'll stop now and ask for help.

My MSI laptop (Ubuntu 9.10) is receiving the wireless signal, so the router is fine.

Please tell me the commands you need to see the output for and I'll provide!
Thank you.

---

### Post by magtrask on 2010-10-23
I've tried a few commands from reading other threads.  
```
sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device

``````
iwconfig 
lo        no wireless extensions.
eth0      no wireless extensions.
```Any ideas?

---

### Post by magtrask on 2010-12-04
Well, I'm talking to myself here, but I thought I'd say I've upgraded to 10.10.  Still no wireless.  And now my laptop which had wireless working on Karmic, I've upgraded as well and as a result lost wireless.   But one thing at a time... I'll stick with the ASUS question here and put the laptop question on a thread I got help with before.
Any help please? Thanks.

update: laptop fine, not a 10.10 issue after all of course, wlan0 hard blocked, found the key to enable it.

---

### Post by bkratz on 2010-12-11
> **magtrask said:**
> Well, I'm talking to myself here, but I thought I'd say I've upgraded to 10.10.  Still no wireless.  And now my laptop which had wireless working on Karmic, I've upgraded as well and as a result lost wireless.   But one thing at a time... I'll stick with the ASUS question here and put the laptop question on a thread I got help with before.
Any help please? Thanks.

update: laptop fine, not a 10.10 issue after all of course, wlan0 hard blocked, found the key to enable it.

Glad to hear the laptop is OK now, but we probably need to look at the following for your desktop


```
lshw -C Network
lspci -nn
lsusb
uname -rm
dmesg | grep -ie wlan -ie radio
```

to see what direction to proceed in.

---

### Post by magtrask on 2010-12-11
> **bkratz said:**
> Glad to hear the laptop is OK now, but we probably need to look at the following for your desktop


```
lshw -C Network
lspci -nn
lsusb
uname -rm
dmesg | grep -ie wlan -ie radio
```to see what direction to proceed in.

```
jen@Rooster:~$ sudo lshw -C Network
[sudo] password for jen: 
  *-network               
       description: Ethernet interface
       product: AR8121/AR8113/AR8114 Gigabit or Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: b0
       serial: 00:26:18:4c:e9:90
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI duplex=full firmware=L1e ip=192.168.1.2 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:44 memory:febc0000-febfffff ioport:ec00(size=128)

``````
jen@Rooster:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller [8086:29c0] (rev 10)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82G33/G31 Express Integrated Graphics Controller [8086:29c2] (rev 10)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge [8086:27b8] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation N10/ICH7 Family SATA IDE Controller [8086:27c0] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 01)
01:00.0 Ethernet controller [0200]: Atheros Communications AR8121/AR8113/AR8114 Gigabit or Fast Ethernet [1969:1026] (rev b0)

``````
jen@Rooster:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 413c:3010 Dell Computer Corp. Optical Wheel Mouse
Bus 002 Device 002: ID 045e:009d Microsoft Corp. Wireless Optical Desktop 3.0
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 03f0:4512 Hewlett-Packard 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

``````
jen@Rooster:~$ uname -rm
2.6.35-23-generic i686

``````
jen@Rooster:~$ dmesg | grep -ie wlan -ie radio
jen@Rooster:~$ 

```Thanks again Bkratz.

---

### Post by bkratz on 2010-12-11
Well, that wasn't very helpful! I don't see a wireless card anywhere in either the lspci or lsusb listing.  You might try updating the listing again with 

sudo update-pciids

and see if you see one labeled something like network or wireless in the description. As stated earlier in a PM, the part number given above is for the motherboard and I don't see any mention of wireless in the link. I know you used to run Windows on it: is this a dual boot system where maybe Windows can give us a hint?  I assume there is a plug-in card or adapter somewhere--does it have any identifiers somewhere on it?

---

### Post by magtrask on 2010-12-11
> **bkratz said:**
> Well, that wasn't very helpful! I don't see a wireless card anywhere in either the lspci or lsusb listing.  You might try updating the listing again with 

sudo update-pciids

and see if you see one labeled something like network or wireless in the description. As stated earlier in a PM, the part number given above is for the motherboard and I don't see any mention of wireless in the link. I know you used to run Windows on it: is this a dual boot system where maybe Windows can give us a hint?  I assume there is a plug-in card or adapter somewhere--does it have any identifiers somewhere on it?

I tried sudo update-pciids and got all the same results.  I see no reference at all to wlan.
No, not a dual boot, I wiped it clean! But definitely used the wireless router with windows before the switch.
There is no plug-in card or adapter visible, would I see it if I took the box cover off the machine?

---

### Post by bkratz on 2010-12-11
Well, you could see several internal cards, such as a video card; but do you see an external antenna on the back anywhere? If so, that would be the wireless card, but yes then you would have to open it up to see anything. If you are not comfortable with removing the cover, is there anyone that could assist you?  You might wait a bit and see if anyone has any better ideas.


Just had a thought, when you purchased the device, did you receive a driver CD that may indicate what the wireless card is?

---

### Post by magtrask on 2010-12-11
Not knowing what I'm doing has never stopped me from taking things apart. 
I'll let you know if I see anything interesting.

---

