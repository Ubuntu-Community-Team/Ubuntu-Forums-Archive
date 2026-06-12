---
title: "Ubuntu can't see my bluetooth hardware"
date: 2012-12-01
forum: Networking &amp; Wireless
---

### Post by SpIZER on 2012-12-01
Hi folks.

I bought a mini pci-e card (combo Wifi and bluetooth) for my laptop SAMSUNG r469

name of the card 
```

lspci -nn | grep -i netw
02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 2230 [8086:0887] (rev 71)

```The Wireless-N 2230 must contain the bluetooth 4.0, but I cant see.

```

igor@R469:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```Here some info from dmesg
```

igor@R469:~$ dmesg | grep -i blu
[   16.139154] Bluetooth: Core ver 2.16
[   16.141777] Bluetooth: HCI device and connection manager initialized
[   16.141781] Bluetooth: HCI socket layer initialized
[   16.141784] Bluetooth: L2CAP socket layer initialized
[   16.141791] Bluetooth: SCO socket layer initialized
[   16.157084] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   16.157087] Bluetooth: BNEP filters: protocol multicast
[   16.180356] Bluetooth: RFCOMM TTY layer initialized
[   16.180363] Bluetooth: RFCOMM socket layer initialized
[   16.180365] Bluetooth: RFCOMM ver 1.11
igor@R469:~$ dmesg | grep -i iwlwifi
[   14.175390] iwlwifi 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   14.175426] iwlwifi 0000:02:00.0: setting latency timer to 64
[   14.175472] iwlwifi 0000:02:00.0: pci_resource_len = 0x00002000
[   14.175474] iwlwifi 0000:02:00.0: pci_resource_base = ffffc90000660000
[   14.175476] iwlwifi 0000:02:00.0: HW Revision ID = 0x71
[   14.175633] iwlwifi 0000:02:00.0: irq 47 for MSI/MSI-X
[   14.175728] iwlwifi 0000:02:00.0: Detected 2000 Series 2x2 BGN/BT, REV=0xC0
[   14.175839] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   14.191730] iwlwifi 0000:02:00.0: device EEPROM VER=0x812, CALIB=0x6
[   14.191733] iwlwifi 0000:02:00.0: Device SKU: 0X150
[   14.191735] iwlwifi 0000:02:00.0: Valid Tx ant: 0X3, Valid Rx ant: 0X3
[   14.276073] iwlwifi 0000:02:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[   14.518558] iwlwifi 0000:02:00.0: loaded firmware version 18.168.6.1
[   16.238329] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   16.246041] iwlwifi 0000:02:00.0: Radio type=0x2-0x0-0x0
[   16.508392] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   16.516079] iwlwifi 0000:02:00.0: Radio type=0x2-0x0-0x0
[   71.017990] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = f0:7d:68:99:fc:f0 tid = 0

```WiFi works perfect, but bluetooth not. Can you help me?

---

### Post by ahallubuntu on 2012-12-01
Was this card designed to work with this laptop?  If not, the bluetooth may not work as part of this Intel card.  It may not be supported by the motherboard chipset.

FYI, it appears that this laptop had an option for bluetooth support.  A clue here:

[https://sites.google.com/site/driverforlaptop/samsung-r469-windows-xp-driver-notebook](https://sites.google.com/site/driverforlaptop/samsung-r469-windows-xp-driver-notebook)

in that a Broadcom bluetooth driver (for XP) is offered, and only Atheros and Realtek WiFi card drivers are offered.

It's possible you can add a separate bluetooth card somewhere on the motherboard.  I have done this on a couple of Dell laptops, where there was a place to plug it in - very easy to add.  Sometimes bluetooth is an option that isn't practical because the motherboard doesn't have a socket soldered on for it, even though some versions of the computer were sold with that option.

Of course, you can buy a cheap USB bluetooth dongle (for under $2 USD), but they are still a bit annoying plugged into your USB port.

---

