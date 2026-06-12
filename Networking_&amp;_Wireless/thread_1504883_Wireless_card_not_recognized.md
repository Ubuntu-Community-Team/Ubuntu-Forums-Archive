---
title: "Wireless card not recognized"
date: 2010-06-08
forum: Networking &amp; Wireless
---

### Post by drfox on 2010-06-08
Help! I'm trying to proselytize and have installed Lucid on my receptionist's Gateway M500 with an Orinoco PCI Mini wireless card. The card works in XP, but when I boot into Linux, the network card indicator light doesn't turn on, and lspci gives me this:
00:00.0 Host bridge: ALi Corporation M1671 Super P4 Northbridge [AGP4X,PCI and SDR/DDR] (rev 02)
00:01.0 PCI bridge: ALi Corporation PCI to AGP Controller
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0b.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
00:0b.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
00:0c.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 01)
00:0d.0 USB Controller: NEC Corporation USB (rev 41)
00:0d.1 USB Controller: NEC Corporation USB (rev 41)
00:0d.2 USB Controller: NEC Corporation USB 2.0 (rev 02)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go 32M] (rev a3)
liz@tabby-cat:~$ 
iwconfig gives me this:
liz@tabby-cat:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

No wireless card :(

Pressing the on-off wireless button does nothing. 
What can I do to turn on the modem so that Lucid sees it?

Larry

---

### Post by purelinuxuser on 2010-06-08
Hmm... that is weird, I don't see a network controller in the output of lscpi.  Post the output of
```
lshw -c network
```

---

### Post by bkratz on 2010-06-08
Some laptops use an internal usb bus for certain functions--perhaps it will show up with an lsusb (LSUSB) in lowercase rather than lspci.

---

### Post by drfox on 2010-06-09
lsusb did not show the hardware, and lshw -C network only showed the eth01 and loopback. It's like the modem gets turned off when the power is turned off and only gets turned on by windows.
Any other suggestions?
Larry

---

### Post by purelinuxuser on 2010-06-09
> **drfox said:**
> lsusb did not show the hardware, and lshw -C network only showed the eth01 and loopback. It's like the modem gets turned off when the power is turned off and only gets turned on by windows.
Any other suggestions?
Larry

Doubt this'll turn up anything, but what about
```
dmesg | grep -i orinoco
dmesg | grep -i pci
```

---

