---
title: "No sound on Asus 1015PX in 16.04 (but it works in 10.04 and I still have a backup)"
date: 2017-12-25
forum: Multimedia Software
---

### Post by timothylegg on 2017-12-25
I've noticed some time back after a reinstall that I lost sound on my EeePC, actually on 3 of these machines.  I tinkered with it some, but I didn't consider audio to be a priority.  I handed a couple of these off to some younger family members and found out that audio is in fact quite important.

Luckily, I found a backup disk image from several years back where sound did work and dd'd it back onto the hard disk.

I have Unbuntu 16.04 installed on an SD card that I can boot into that sound isn't working.

Here is some relevant information on the machine, based on what I suspect is important

lspci  (on Ubuntu 10.04)
```
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge (rev 02)
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications AR8152 v2.0 Fast Ethernet (rev c1)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
```


aplay -l  (Ubuntu 10.04)
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```


I shall now reboot and start in Ubuntu 16.04 and perform the same steps...

```
00:00.0 Host bridge: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx DMI Bridge (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation NM10/ICH7 Family SATA Controller [AHCI mode] (rev 02)
01:00.0 Ethernet controller: Qualcomm Atheros AR8152 v2.0 Fast Ethernet (rev c1)
02:00.0 Network controller: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
```


```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I go to All Settings / Sound and I see that it has "Speakers Built-in Audio", but doesn't allow me to investigate any further no matter if I double click or right click, which seems like what would be the right thing to do.  When I "Test Sound" , nothing comes out either speaker.  Volume is turned on. I can affect the signal strength meter on the microphone test though, so there is a partial functionality.  Output volume is turned up.  The speaker icon next to the clock shows it is unmuted and turned up.  I have no idea at what stage the audio is getting disabled, but it can be made to work by booting Ubuntu 10.04

Any ideas

---

### Post by timothylegg on 2018-01-09
I haven't forgotten about this.  I really would like to figure this out.  Admittedly, sound isn't that important to me, but it's curious that a software upgrade would result in a functionality downgrade.  I do not know if there were 'extras' installed though, such as binaries or incompatibly licensed software installed; I simply don't remember the installation process.

---

### Post by slickymaster on 2018-01-09
Thread moved to **Multimedia Software** for a better fit

---

