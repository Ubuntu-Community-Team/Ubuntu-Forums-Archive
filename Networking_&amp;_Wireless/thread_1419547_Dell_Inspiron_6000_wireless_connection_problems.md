---
title: "Dell Inspiron 6000 wireless connection problems"
date: 2010-03-02
forum: Networking &amp; Wireless
---

### Post by lukekirstein on 2010-03-02
I'm relatively new at all of this, and while I have some Linux experience, I can't do it without a walthrough :smile:.

I've been trying to get wireless working on my Dell Inspiron 6000 all night now. I don't have integrated wireless but a card that I purchased from Amazon (the internal card was water-damaged and needed to be replaced). 

I've followed the thousands of Wiki's and guides online for ndiswrapper and thought I had it down. However, while Ubuntu picks up the card, it won't connect to any networks. I see networks in the top left but it hangs on connecting to any of them, asking for passwords repeatedly but never getting any farther. 

Any ideas?

---

### Post by bkratz on 2010-03-02
> **lukekirstein said:**
> I'm relatively new at all of this, and while I have some Linux experience, I can't do it without a walthrough :smile:.

I've been trying to get wireless working on my Dell Inspiron 6000 all night now. I don't have integrated wireless but a card that I purchased from Amazon (the internal card was water-damaged and needed to be replaced). 

I've followed the thousands of Wiki's and guides online for ndiswrapper and thought I had it down. However, while Ubuntu picks up the card, it won't connect to any networks. I see networks in the top left but it hangs on connecting to any of them, asking for passwords repeatedly but never getting any farther. 

Any ideas?




We need more information. Please post the outputs of:

lspci
lsusb
iwconfig
sudo lshw -C network
rfkill list

(those are lowercase L's not 1's)

---

### Post by lukekirstein on 2010-03-02
lspci:

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
03:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)


lsusb:
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 005: ID 0a5c:4503 Broadcom Corp. 
Bus 003 Device 004: ID 0a5c:4502 Broadcom Corp. 
Bus 003 Device 003: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


iwconfig:

lo        no wireless extensions.

pan0      no wireless extensions.

vboxnet0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.


sudo lshw -C Network
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:12:3f:e2:c7:f7
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.0.101 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:18 memory:dfcfc000-dfcfdfff
  *-network:1
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       logical name: wlan0
       version: 02
       serial: 00:90:4b:fa:e1:bc
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.55+Broadcom,10/12/2006, 4.100. latency=64 link=no multicast=yes wireless=IEEE 802.11g
       resources: irq:17 memory:dfcfe000-dfcfffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

rfkill list:
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


------

Anything else?

---

### Post by bkratz on 2010-03-02
This is a good place to start, your card is specifically mentioned

[http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices)

See the section labeled

Ubuntu/Debian

If you have any problems post back


Oh I just noticed you did the ndiswrapper methodology. Will find a more appropriate guide.

---

### Post by bkratz on 2010-03-02
Here is a thread specifically about your card. If you wish to try the native drivers we will probably have to remove ndiswrapper, so look through the whole thread before deciding.

[http://ubuntuforums.org/showthread.php?t=1382918&highlight=AirForce+54g](http://ubuntuforums.org/showthread.php?t=1382918&highlight=AirForce+54g)


Since you do see networks (rereading the first post), have you tried temporarily removing the encryption on your network just to see if you can connect? That way at least we would know if everything else is correctly working.

---

### Post by lukekirstein on 2010-03-02
Thank you so much for your help. I've tried to connect to open and encrypted networks, and I have a lot in my neighborhood to choose from. I'm trying the sudo apt-get install b43fwcutter, since I haven't played with fwcutter yet. Will post results soon.

---

### Post by lukekirstein on 2010-03-02
Who would've known that one command line would have saved me the countless, sleep-free hours I have spent. fwcutter worked like a charm. Thanks for finding the thread for me and all your help!

```
sudo apt-get install b43-fwcutter
```

Thanks again!

---

### Post by bkratz on 2010-03-02
> **lukekirstein said:**
> Who would've known that one command line would have saved me the countless, sleep-free hours I have spent. fwcutter worked like a charm. Thanks for finding the thread for me and all your help!

```
sudo apt-get install b43-fwcutter
```

Thanks again!

Sure glad it worked for you!  Could you please use the thread tools and mark as {solved} in case it helps someone else?

---

