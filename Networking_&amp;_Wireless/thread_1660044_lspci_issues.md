---
title: "lspci issues?"
date: 2011-01-04
forum: Networking &amp; Wireless
---

### Post by adduds on 2011-01-04
DWL-G510

tried two different pci slots and my wifi card doesn't show up??```
toews@desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:09.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
00:0a.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
00:0a.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
00:0a.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7600 GT] (rev a2)

```

---

### Post by bkratz on 2011-01-04
Well it looks like you either have two or it is hiding as a

[COLOR="Red"]00:09.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)[/COLOR]

Will have to look at bit more for information

---

### Post by adduds on 2011-01-04
When doing a lspci -v i found this...

i still don't think i have drivers installed for my card though?

```
00:09.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
	Subsystem: D-Link System Inc AirPlus G DWL-G510 Wireless PCI Adapter(rev.B)
	Flags: bus master, medium devsel, latency 168, IRQ 17
	Memory at eb000000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: ath5k
	Kernel modules: ath5k

```

*NOTE*

I tried doing this:

[WIFI Docs DWL-G510]("https://help.ubuntu.com/community/WifiDocs/DWL-G510")

and also found this:

[Ubuntu Hardware support]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink")

although i cannot find these RT61 drivers....they speak of 

**

---

### Post by bkratz on 2011-01-04
> **adduds said:**
> When doing a lspci -v i found this...

i still don't think i have drivers installed for my card though?

```
00:09.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
	Subsystem: D-Link System Inc AirPlus G DWL-G510 Wireless PCI Adapter(rev.B)
	Flags: bus master, medium devsel, latency 168, IRQ 17
	Memory at eb000000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>
	Kernel driver in use: [COLOR="Red"]ath5k[/COLOR]
	Kernel modules: ath5k

```



Well actually you do. Have you tried to left click on the network manager icon and see if you see any available A/p'S?
or drop to the terminal and try a

sudo iwlist scan

and look at the results.  By the way here is a thread I found.

[http://www1.ubuntuforums.org/showthread.php?t=1345078](http://www1.ubuntuforums.org/showthread.php?t=1345078)

Also see post 115 here

[http://ubuntuforums.org/showthread.php?t=1309072&page=12](http://ubuntuforums.org/showthread.php?t=1309072&page=12)

---

### Post by adduds on 2011-01-05
result of sudo iwlist scan

```
toews@desktop:~$ sudo iwlist scan
[sudo] password for toews: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:13:46:4A:DF:5A
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"toews"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000c700b20d
                    Extra: Last beacon: 690ms ago
                    IE: Unknown: 0005746F657773
                    IE: Unknown: 010882848B960C183048
                    IE: Unknown: 030101
                    IE: Unknown: DD0600032F010001
                    IE: Unknown: 2A0100
                    IE: Unknown: 32041224606C
                    IE: Unknown: DD0900037F010100060000
                    IE: Unknown: DD0C00037F020101010002A34000

```

so how do i connect to my network i'm on LAN right now but wanna be on a WAN......

network connections 

also did a sudo lshw

```
        *-network:0
             description: Wireless interface
             product: AR2413 802.11bg NIC
             vendor: Atheros Communications Inc.
             physical id: 9
             bus info: pci@0000:00:09.0
             logical name: wlan0
             version: 01
             serial: 00:15:e9:84:e5:92
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=ath5k driverversion=2.6.35-24-generic firmware=N/A latency=168 link=no maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg

```

so where do i go to network manager and connect????

---

### Post by kedarkekan on 2011-01-05
Try "Connect to Hidden Wireless Network" option in Netwerk Manager.

It seems you already have ath5k installed. It's just that the AP might not be broadcasting it's SSID.

---

### Post by PatchesTheCaveman on 2011-01-05
You might have a better experience with wicd than NetworkManager.  Both these programs drive the network icon that appears on your top panel, but many users find wicd to work better.  To make the switch, make sure you are plugged into a working wired Ethernet Internet connection, then go to Applications > Accessories > Terminal on your top panel.  In the black box that appears, type each of the following commands, pressing Enter after each one:
```
sudo apt-get update
sudo apt-get remove network-manager
sudo apt-get install wicd
```

You might need to reboot for NetworkManager to be fully removed and to allow wicd to take over.

---

### Post by adduds on 2011-01-06
Ty list as solved

---

### Post by bkratz on 2011-01-06
> **adduds said:**
> Ty list as solved

did you actually get your problem solved? If so, what did you find?
By the way only you can mark the thread as solved using the thread tools at the top of the page.

---

### Post by gordintoronto on 2011-01-06
That wireless adapter works "out of the box." I think the OP figured he needed to install a driver, when it is actually built into Linux as of more than two years ago.

I have the same wireless adapter, and it has worked with every version of Linux I have tried over the past three years, probably more than 20 versions. (Ubuntu, Puppy, Mint, Crunchbang, etc, etc.)

---

### Post by adduds on 2011-01-07
All i really did in the end once I figured out my driver was already installed was installed wicd couldn't get it to connect to my network....uninstalled it and the network manager auto connected to my network lmao

so what drivers are auto installed in ubuntu??? unlike microsoft you don't always need install cds for hardware?

> **gordintoronto said:**
> That wireless adapter works "out of the box." I think the OP figured he needed to install a driver, when it is actually built into Linux as of more than two years ago.


lol you're more than right hahahahaha

---

### Post by PatchesTheCaveman on 2011-01-07
This list is kinda out-of-date, but it will give you an idea:
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by adduds on 2011-01-07
> **PatchesTheCaveman said:**
> This list is kinda out-of-date, but it will give you an idea:
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

nice

---

### Post by gordintoronto on 2011-01-07
> **adduds said:**
> so what drivers are auto installed in ubuntu??? unlike microsoft you don't always need install cds for hardware?


Actually, Windows also has a lot of built-in drivers. If you run the command (from Accessories/Terminal) lspci

you will get a list of some of your devices. The command lsusb might show some more.

In Ubuntu, I installed a driver for my video card from Administration/Additional Drivers. I installed my network printer by going to Administration/Printing and making about four mouse clicks. And my wireless adapter and webcam "just worked". No install CDs!

---

