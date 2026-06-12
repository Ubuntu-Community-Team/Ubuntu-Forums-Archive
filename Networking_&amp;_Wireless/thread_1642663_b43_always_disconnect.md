---
title: "b43 always disconnect"
date: 2010-12-10
forum: Networking &amp; Wireless
---

### Post by eDaneeel on 2010-12-10
Hi,

I have a Broadcom BCM4312 wireless card. It is working, but as soon as I start to download something, it disconnects and I cannot connect again.The only way to be connect again is to reboot my netbook. I downloaded from ubuntu software center the b43 driver for LP-PHY card. And then I had -1 channel bug, therefore I installed compat-wireless, I followed this post:[http://ubuntuforums.org/showthread.php?t=1598930&highlight=bcm4312]("http://ubuntuforums.org/showthread.php?t=1598930&highlight=bcm4312") 
If I use aireplay and try to inject packet it also freezes, then I cannot connect to the internet.

After a reboot my dmesg | b43 says:
```
edaneeel@nbook:~$ dmesg | grep b43
[   15.662990] b43-pci-bridge 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.663020] b43-pci-bridge 0000:03:00.0: setting latency timer to 64
[   15.930085] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   16.201776] Registered led device: b43-phy0::tx
[   16.201839] Registered led device: b43-phy0::rx
[   16.201902] Registered led device: b43-phy0::radio
[   16.677705] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)

```

But after my wireless is crashed, it says:
```
root@nbook:/home/edaneeel# dmesg | grep b43
[   15.298136] b43-pci-bridge 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.298166] b43-pci-bridge 0000:03:00.0: setting latency timer to 64
[   15.456405] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   15.643125] Registered led device: b43-phy0::tx
[   15.643180] Registered led device: b43-phy0::rx
[   15.643233] Registered led device: b43-phy0::radio
[   41.361693] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[  305.836397] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[  436.223548] b43-phy0 ERROR: Fatal DMA error: 0x00000800, 0x00000000, 0x00000000, 0x00000000, 0x00000000, 0x00000000
[  436.223583] b43-phy0 ERROR: This device does not support DMA on your system. It will now be switched to PIO.
[  436.223604] b43-phy0: Controller RESET (DMA error) ...
[  436.476442] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[  442.001782] b43-phy0: Controller restarted
[  680.552330] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
[  911.764355] b43-phy0: Loading firmware version 478.104 (2008-07-01 00:50:23)
```

my lspci:
```
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

```

I would be very grateful if somebody could help me, because I have no idea what should I do now.

Thank you in advance.

---

### Post by eDaneeel on 2010-12-12
alright, I give it up. I hate broadcom :) 

I am intend to buy an atheros card.I have Mini Pci express in my Dell inspiron. Is there any suggestion what kind of card would be the best for me, which works fine with aircrack?

---

