---
title: "DWA-642 with Atheros / madwifi-ng drivers help."
date: 2009-03-09
forum: Networking &amp; Wireless
---

### Post by Acidictadpole on 2009-03-09
Hello,

I have followed the tutorial here: [http://ubuntuforums.org/showthread.php?t=935573](http://ubuntuforums.org/showthread.php?t=935573) and got it showing up in iwconfig. However being in my profession (I am a security student right now) I am in need of a little more. I have run backtrack in the past and the card works out of the box, simply plug it in and the card works the way I need.

Now I should probably describe more what I need and where that previous tutorial gets me in terms of that. My card has an atheros chipset, known for its injection capabilities. Using ndiswrapper drivers it doesn't actually let me set the interface into Monitor mode. 

Since this is all very vague I have run a dmesg in both backtrack and ubuntu, and obviously we can see differences. I will paste those in shortly, but I'm no super linux guy and deciphering these is a little beyond my capability. My capability is around "Hey... wait a tick, they're different!" and it hasn't failed me yet. 

If anyone has any ideas to turn this:

```
#[  296.510332] pccard: CardBus card inserted into slot 0
#[  296.519499] ndiswrapper: driver netathw (,01/17/2008,7.4.2.75) loaded
#[  296.519941] PCI: Enabling device 0000:16:00.0 (0000 -> 0002)
#[  296.519961] ACPI: PCI Interrupt 0000:16:00.0[A] -> GSI 16 (level, low) -> IRQ 16
#[  296.520577] PCI: Setting latency timer of device 0000:16:00.0 to 64
#[  296.962745] ndiswrapper: using IRQ 16
#[  297.046638] wlan0: ethernet device 00:21:91:0a:a5:82 using serialized NDIS driver: netathw, version: 0x70004, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 168C:0023.5.conf
#[  297.061309] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
#[  297.084716] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```

Into this:

```
pcmcia_socket pcmcia_socket0: pccard: CardBus card inserted into slot 0
pci 0000:16:00.0: reg 10 32bit mmio: [0x000000-0x00ffff]
ath_pci 0000:16:00.0: enabling device (0000 -> 0002)
ath_pci 0000:16:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
MadWifi: ath_attach: Switching rfkill capability off.
wifi1: Atheros AR5418 chip found (MAC 13.10, PHY SChip 8.1, Radio 15.0)
wifi1: ath_announce: Driver has Karma 1.1 patches by Robin Wood <dninja@gmail.com>
wifi1: ath_announce: Driver has managed mode injection patches by Jeff <dev.802.11@gmail.com>
wifi1: ath_announce: Driver mods are maintained by H D Moore <hdm@metasploit.com>
```

you be greatly praised.

---

### Post by Acidictadpole on 2009-03-11
Still looking for some help on the matter.

---

