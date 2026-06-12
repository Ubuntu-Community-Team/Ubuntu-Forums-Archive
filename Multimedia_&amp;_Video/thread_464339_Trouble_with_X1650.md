---
title: "Trouble with X1650"
date: 2007-06-04
forum: Multimedia &amp; Video
---

### Post by cdemi on 2007-06-04
hi, i am pretty new to ubuntu. i am starting to like it however i have trouble getting my ATI RADEON X1650 to work. i cannot even install the drivers. ubuntu does not recognize my VGA. when i type lspci in the terminal i get the following output:

```
00:00.0 Host bridge: VIA Technologies, Inc. PT880 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. PT880 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. PT880 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. PT880 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. PT880 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. PT880 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
00:0a.0 Multimedia audio controller: ESS Technology ES1969 Solo-1 Audiodrive (rev 01)
00:0b.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
[B][COLOR="Red"]01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 71c7 (rev 9e)
01:00.1 Display controller: ATI Technologies Inc Unknown device 71e7 (rev 9e)[/COLOR][/B]

```

please help me :(

---

### Post by cdemi on 2007-06-04
I just booted from a KNOPPIX Live CD and it too could not detect my VGA :S wtf is wrong with my VGA? is it defected? but on windows it works well and everything. what do you think is wrong? i really wanna use linux!!

---

### Post by tseliot on 2007-06-05
> **cdemi said:**
> hi, i am pretty new to ubuntu. i am starting to like it however i have trouble getting my ATI RADEON X1650 to work. i cannot even install the drivers. ubuntu does not recognize my VGA. when i type lspci in the terminal i get the following output:

```
[B][COLOR="Red"]01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 71c7 (rev 9e)
01:00.1 Display controller: ATI Technologies Inc Unknown device 71e7 (rev 9e)[/COLOR][/B]

```

Actually this means that your graphic card was detected.

What is your problem? Do you get a blue screen or only poor performance?

---

### Post by cdemi on 2007-06-05
i can't get ATI drivers to install, they say that my video card is not supported. and even if i try to use restricted drivers, it does not show up, sorry for my bad english

---

