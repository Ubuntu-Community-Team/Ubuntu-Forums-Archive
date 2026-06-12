---
title: "Wireless card: Wifi Radar vs. iwlist/iwconfig"
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by jhsu802701 on 2009-11-08
I'm using a Linksys WPC54GS version 1.1 wireless card.  I think I finally got it to work, but I'm not sure.

The link light and commands like iwlist and iwconfig show that my wireless card is working.  However, WiFi Radar and the NM Applet show no evidence that it is.

Unfortunately, I live in a small town with no WiFi venue open.  With another WiFi card (that has always worked right out-of-the-box), I can see the presence of networks in WiFi Radar and NM Applet.

With my Linksys WPC54GS version 1.1 wireless card plugged into my laptop, I get the following lspci output:
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:03.0 CardBus bridge: Texas Instruments PCI1225 (rev 01)
00:03.1 CardBus bridge: Texas Instruments PCI1225 (rev 01)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
01:00.0 VGA compatible controller: Neomagic Corporation NM2360 [MagicMedia 256ZX]
01:00.1 Multimedia audio controller: Neomagic Corporation NM2360 [MagicMedia 256ZX Audio]
06:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

BCM4306 is the driver I need, and bcm43xx-fwcutter is the package that has it, so I used Synaptic to download and install the program.

When I enter the command "sudo modprobe -r bcm43xx && sudo modprobe bcm43xx", the link light on the wireless card suddenly comes on.  However, I have no idea what this command means or how it activates the wireless card.  Can anyone explain?

I get the following "iwlist scan" output:
lo        Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:15:6D:10:0C:92
                    ESSID:"XTI-11"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=82/100  Signal level=-74 dBm  Noise level=-68 dBm
                    Extra: Last beacon: 52ms ago
          Cell 02 - Address: 00:16:B6:DE:BF:64
                    ESSID:"mort"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=78/100  Signal level=-80 dBm  Noise level=-68 dBm
                    Extra: Last beacon: 116ms ago
          Cell 03 - Address: 00:15:6D:54:AC:AB
                    ESSID:"XTI-Dassel-S"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=82/100  Signal level=-74 dBm  Noise level=-68 dBm
                    Extra: Last beacon: 3240ms ago

I get the following iwconfig output:
lo        no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I get the following "lshw -C network" output:
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth1
       version: 03
       serial: 00:13:10:47:e7:93
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.24-19-generic latency=64 module=bcm43xx multicast=yes wireless=IEEE 802.11b/g

In other words, the lit link LED on the wireless card and the outputs of all these commands indicate that my wireless card is working.

However, WiFi Radar does NOT show these networks - it's completely blank.  The is true when I go to NM applet and click on "edit wireless networks".

My questions:
1.  Why don't WiFi Radar or NM Applet 0.6.6 show any evidence that my wireless card is working even though commands like "iwlist scan", iwconfig, and "lshw -C network" and the link LED on the wireless card show the presence of networks in my area?
2.  If WiFi Radar or NM Applet are somehow incompatible with this wireless card, is there another wireless network GUI I should use instead?

---

