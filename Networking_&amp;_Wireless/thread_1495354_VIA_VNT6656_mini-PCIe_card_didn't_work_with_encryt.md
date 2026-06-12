---
title: "VIA VNT6656 mini-PCIe card didn't work with encrytion enabled"
date: 2010-05-28
forum: Networking &amp; Wireless
---

### Post by ozybushwalker on 2010-05-28
I installed Ubuntu Netbook Remix 10.04 on a Kogan netbook with a VIA VNT6656 mini PCIe wireless NIC. This used to work with a variant of GOs (based on Ubuntu 8.04) installed but didn't work with Ubuntu 10.04.

A TP-Link TL-WN321G USB wireless NIC (Ralink RT2501 chipset) worked fine. The VIA wireless NIC worked fine without encryption but that's not very secure.

I noticed a post here [http://ubuntuforums.org/showthread.php?t=1477392]("http://ubuntuforums.org/showthread.php?t=1477392") for Ralink USB cards which didn't work with encryption unless the Access Point was set to WPA2 (rather than WAP/WPA2) and AES (rather than both AES and TKIP) so I set the access point to WPA2 only and AES only and after a while *iwlist scan* showed my AP looking for AES: 

> [FONT="Courier New"]
         Cell 02 - Address: 00:1B:11:B5:C1:C8
                    ESSID:"Bree1"
                    Mode:Managed
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=70/100  Signal level=-62 dBm  Noise level=0 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK[/FONT]

and a bit later the connection came good.

Here's how my VIA wireless NIC shows up to lsusb:
> [FONT="Courier New"]Bus 001 Device 011: ID 160a:3184  [/FONT]

---

