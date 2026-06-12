---
title: "Asus WL-103b (b43legacy) not working"
date: 2010-04-16
forum: Networking &amp; Wireless
---

### Post by W3ird_N3rd on 2010-04-16
I just installed Ubuntu lucid beta2, but I'm having no luck getting my wireless card (Asus WL-103b cardbus) to work. It uses the b43legacy driver. I have also installed the correct firmware. This card used to work if I'm not mistaken..

> [  267.239150] pcmcia_socket pcmcia_socket1: pccard: CardBus card inserted into slot 1
[  267.239267] pci 0000:06:00.0: reg 10 32bit mmio: [0x000000-0x001fff]
[  267.239384] pci 0000:06:00.0: supports D1 D2
[  267.239401] pci 0000:06:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[  267.239421] pci 0000:06:00.0: PME# disabled
[  267.345909] b43-pci-bridge 0000:06:00.0: enabling device (0000 -> 0002)
[  267.345967] b43-pci-bridge 0000:06:00.0: setting latency timer to 64
[  267.351997] ssb: Sonics Silicon Backplane found on PCI device 0000:06:00.0
[  267.506462] b44.c:v2.0
[  267.506535] b44: Invalid MAC address found in EEPROM
[  267.506554] b44 ssb0:1: Problem fetching invariants of chip, aborting.
[  267.506601] b44: probe of ssb0:1 failed with error -22
[  267.659216] cfg80211: Calling CRDA to update world regulatory domain
[  267.859031] cfg80211: World regulatory domain updated:
[  267.859128] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  267.859151] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  267.859171] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  267.859189] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  267.859207] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  267.859225] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  267.940550] b43legacy-phy0: Broadcom 4301 WLAN found
[  267.963094] b43legacy-phy0 debug: Found PHY: Analog 0, Type 1, Revision 4
[  267.963136] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2053, Revision 2
[  267.987102] b43legacy-phy0 debug: Radio initialized
[  268.091956] phy0: Selected rate control algorithm 'minstrel'
[  268.101391] Broadcom 43xx-legacy driver loaded [ Features: PLID, Firmware-ID: FW10 ]
[  268.343156] b43legacy ssb0:0: firmware: requesting b43legacy/ucode2.fw
[  268.430502] b43legacy ssb0:0: firmware: requesting b43legacy/pcm4.fw
[  268.462677] b43legacy ssb0:0: firmware: requesting b43legacy/b0g0initvals2.fw
[  268.591132] b43legacy-phy0: Loading firmware version 0x127, patch level 14 (2005-04-18 02:36:27)
[  268.648871] b43legacy-phy0 debug: Chip initialized
[  268.649958] b43legacy-phy0 debug: 30-bit DMA initialized
[  268.659006] b43legacy-phy0 debug: Wireless interface started
[  268.659248] b43legacy-phy0: Radio hardware status changed to DISABLED
[  268.659312] b43legacy-phy0 debug: Radio initialized
[  268.675360] b43legacy-phy0 debug: Adding Interface type 2
[  268.711083] b43legacy-phy0: Radio turned on by software
[  268.711103] b43legacy-phy0: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
[  268.711914] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  268.712082] b43legacy-phy0 debug: Removing Interface type 2
[  268.712166] b43legacy-phy0 debug: Wireless interface stopped
[  268.713077] b43legacy-phy0 debug: DMA-30 0x0260 (RX) max used slots: 0/64
[  268.713259] b43legacy-phy0 debug: DMA-30 0x0200 (RX) max used slots: 1/64
[  268.713433] b43legacy-phy0 debug: DMA-30 0x02A0 (TX) max used slots: 0/128
[  268.719211] b43legacy-phy0 debug: DMA-30 0x0280 (TX) max used slots: 0/128
[  268.727139] b43legacy-phy0 debug: DMA-30 0x0260 (TX) max used slots: 0/128
[  268.735112] b43legacy-phy0 debug: DMA-30 0x0240 (TX) max used slots: 0/128
[  268.743110] b43legacy-phy0 debug: DMA-30 0x0220 (TX) max used slots: 0/128
[  268.751110] b43legacy-phy0 debug: DMA-30 0x0200 (TX) max used slots: 0/128
[  268.759111] b43legacy-phy0 debug: Radio initialized
[  268.759149] b43legacy-phy0 debug: Radio initialized
I'm not even getting a list of networks. I searched but only found some bugs from 2008 and they do not seem relevant here.

---

### Post by W3ird_N3rd on 2010-04-16
I tried blacklisting b44. That did not help.
I tried blacklisting b43-pci-bridge. That was ignored.
I tried un-blacklisting bcm43xx en blacklisting b43legacy. That did not help.
I tried installing the 2.6.34-999 kernel. That did not help.
I tried killing myself. That did not work out either.

---

### Post by ssum on 2010-06-11
Already found a solution by any chance? Almost at the killing point myself as well here...

---

