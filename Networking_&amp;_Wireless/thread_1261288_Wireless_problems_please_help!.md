---
title: "Wireless problems please help!"
date: 2009-09-08
forum: Networking &amp; Wireless
---

### Post by Darknp21 on 2009-09-08
Hey, I am new to ubuntu 9.04. I am dual booting with windows vista, and my wireless works perfectly in vista but does not seem to work in ubuntu. If i boot in vista before booting in ubuntu, my internet in ubuntu seems to work.  My wireless card is an intel pro 3945 ABG, and i have a Dell xps m1530! Please help! I would really like to use ubuntu a lot more but the wireless problem is holding me back thx!!

---

### Post by Crafty Kisses on 2009-09-08
Just to confirm a couple of things, can you post the results of these commands?
```
lspci
lsusb
lshw -C network
```

---

### Post by Darknp21 on 2009-09-08
Thank you so much for responding. Here is the information that you have requested:   

**LSPCI**

                                 ```

 00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)  
 00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)  
 00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)  
 00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)  
 00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)  
 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)  
 00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)  
 00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)  
 00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)  
 00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)  
 00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)  
 00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)  
 00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)  
 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)  
 00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)  
 00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)  
 00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)  
 00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)  
 01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)  
 03:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)  
 03:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)  
 03:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)  
 03:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)  
 03:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)  
 09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12) 
 0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)  
 
```
**Lsusb**


                                  ```

 Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 007 Device 005: ID 0a5c:4503 Broadcom Corp.  
 Bus 007 Device 003: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth  
 Bus 007 Device 004: ID 0a5c:4502 Broadcom Corp.  
 Bus 007 Device 002: ID 0a5c:4500 Broadcom Corp.  
 Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 001 Device 002: ID 05a9:2640 OmniVision Technologies, Inc.  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub  
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 Bus 003 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader  
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub  
 
```
[B]Lshw -c Network 
[/B]


                                  ```

 *-network                
        description: Ethernet interface  
        product: 88E8040 PCI-E Fast Ethernet Controller  
        vendor: Marvell Technology Group Ltd.  
        physical id: 0  
        bus info: pci@0000:09:00.0  
        logical name: eth0  
        version: 12  
        serial: 00:1d:09:43:48:97  
        width: 64 bits  
        clock: 33MHz  
        capabilities: bus_master cap_list ethernet physical  
        configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 module=sky2 multicast=yes  
   *-network UNCLAIMED  
        description: Network controller  
        product: PRO/Wireless 3945ABG [Golan] Network Connection  
        vendor: Intel Corporation  
        physical id: 0  
        bus info: pci@0000:0b:00.0  
        version: 02  
        width: 32 bits  
        clock: 33MHz  
        capabilities: cap_list  
        configuration: latency=0  
   *-network DISABLED  
        description: Ethernet interface  
        physical id: 1  
        logical name: pan0  
        serial: 5e:4e:21:4c:66:3c  
        capabilities: ethernet physical  
        configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes  
 
```

---

### Post by Darknp21 on 2009-09-09
bump

---

### Post by Crafty Kisses on 2009-09-09
That's weird, when the wireless doesn't work, what are the results of the following?
```
lsmod
```

---

### Post by Darknp21 on 2009-09-09
the results of LSMOD is : Thank you for u help!

```

Module                  Size  Used by
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
joydev                 18496  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
snd_hda_intel         434100  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
uvcvideo               63368  0 
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
psmouse                61972  0 
video                  25360  0 
compat_ioctl32          9344  1 uvcvideo
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ricoh_mmc              11904  0 
sdhci_pci              15232  0 
sdhci                  23940  1 sdhci_pci
output                 11008  1 video
usbhid                 42336  0 
btusb                  19608  2 
dcdbas                 15264  0 
videodev               41600  1 uvcvideo
v4l1_compat            21764  2 uvcvideo,videodev
intel_agp              34108  0 
agpgart                42696  1 intel_agp
snd                    62756  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
serio_raw              13444  0 
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
pcspkr                 10496  0 
ndiswrapper           193436  0 
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
sky2                   54916  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

```

---

### Post by benjoseph on 2009-09-10
For a full month I have been struggling to connect to INTERNET through a D-Link USB Adapter. Then I tried my son in Law Belkin adapter and things got much better, so I decided I was going to buy a Belkin adapter for around £ 30 pounds, when just by chance I happened to visit Ripon open market, and from a stall (selling hardware) I bought for £ 12 pounds a "TP-LINK 54 Wireless G USB adapter", and when I tried at home I was struck by amazement. The connection is just fantastic, and never fails. I recommended with no hesitation whosoever. Just in case some one need one here is the e-mail address of this retailer. [email]stephen@roseparrot3.orangehome.co.uk[/email]  

happy surfing 

benjoseph

---

### Post by Darknp21 on 2009-09-10
Thx for the idea,  but i dont think i will be able to get a new wireless card. Can someone please offer some assistance with this issue, and thx codename for helping in fixing this problem.

---

### Post by chili555 on 2009-09-11
I notice in *lsmod* that ndiswrapper is loaded and doing nothing. Did you try to get your wireless going with ndiswrapper? Did you blacklist the native module, iwl3945? If you open a terminal and do:```
sudo modprobe iwl3945
```Does your wireless spring to life? Please let us know and we'll get it sorted out.

---

### Post by Darknp21 on 2009-09-15
Hi, sorry for the delayed response. But the commands didnt do anything my wireless does not work.  Also i tried to get ndiswrapper to work and it didnt work. Thank you!

---

### Post by Darknp21 on 2009-09-17
bump

---

### Post by gertpozzo on 2009-09-20
Hi.
That's a bug of iwl3945 driver that is already known but that hasn't been fixed yet.

You can see the bug reports here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/319270](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/319270)
[http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=1651](http://bugzilla.intellinuxwireless.org/show_bug.cgi?id=1651)

I don't know if there is any workaround

---

### Post by chili555 on 2009-09-21
May we please see:```
dmesg | grep iwl3945
```Thanks.

---

### Post by Darknp21 on 2009-09-21
Hey chili555, I entered the code into the terminal and it did not display anything...i am not sure if i am doing anything wrong or its something with my cpu. Thank

---

### Post by gertpozzo on 2009-09-21
I own an xps 1530 too and am having the same problem.

As I've already said that's a known bug of the driver that hasn't yet been fixed.

---

### Post by chili555 on 2009-09-21
Typically, it means that *dmesg* has no messages about iwl3945, not that anything is wrong. It does raise the question of just what module is, or is not being loaded. Please do:```
lsmod > lsmod.txt
dmesg > dmesg.txt
```Two text files will be created in your home directory that you can transfer to a USB drive and then to a computer with an internet connection and post here. Thanks.

---

### Post by Darknp21 on 2009-09-21
**LSMOD**
```

Module                  Size  Used by
binfmt_misc            16776  1 
ppdev                  15620  0 
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
input_polldev          11912  0 
lp                     17156  0 
parport                42220  2 ppdev,lp
joydev                 18496  0 
snd_hda_intel         434100  3 
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
uvcvideo               63368  0 
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nvidia               7233756  38 
snd                    62756  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
compat_ioctl32          9344  1 uvcvideo
psmouse                61972  0 
soundcore              15200  1 snd
intel_agp              34108  0 
agpgart                42696  2 nvidia,intel_agp
videodev               41600  1 uvcvideo
v4l1_compat            21764  2 uvcvideo,videodev
usbhid                 42336  0 
ricoh_mmc              11904  0 
sdhci_pci              15232  0 
sdhci                  23940  1 sdhci_pci
video                  25360  6 
iTCO_wdt               19108  0 
iTCO_vendor_support    11652  1 iTCO_wdt
snd_page_alloc         16904  2 snd_hda_intel,snd_pcm
usblp                  20224  0 
dcdbas                 15264  0 
btusb                  19608  2 
pcspkr                 10496  0 
serio_raw              13444  0 
output                 11008  1 video
ndiswrapper           193436  0 
ohci1394               38576  0 
ieee1394               94660  1 ohci1394
sky2                   54916  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit

```[B]

Dmesg

[/B]```
[    0.480018] Bluetooth: HCI device and connection manager initialized
[    0.480018] Bluetooth: HCI socket layer initialized
[    0.480018] NET: Registered protocol family 8
[    0.480018] NET: Registered protocol family 20
[    0.480027] NetLabel: Initializing
[    0.480028] NetLabel:  domain hash size = 128
[    0.480029] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.480040] NetLabel:  unlabeled traffic allowed by default
[    0.480053] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.480056] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.484045] AppArmor: AppArmor Filesystem Enabled
[    0.492007] pnp: PnP ACPI init
[    0.492013] ACPI: bus type pnp registered
[    0.500562] Switched to high resolution mode on CPU 1
[    0.504007] Switched to high resolution mode on CPU 0
[    0.507553] pnp 00:0a: io resource (0x1000-0x1005) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.507556] pnp 00:0a: io resource (0x1008-0x100f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.507630] pnp 00:0b: io resource (0x1006-0x1007) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.507633] pnp 00:0b: io resource (0x100a-0x1059) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.507635] pnp 00:0b: io resource (0x1010-0x102f) overlaps 0000:00:1f.0 BAR 7 (0x1000-0x107f), disabling
[    0.526649] pnp: PnP ACPI: found 13 devices
[    0.526651] ACPI: ACPI bus type pnp unregistered
[    0.526654] PnPBIOS: Disabled by ACPI PNP
[    0.526661] system 00:01: iomem range 0xff800000-0xff8fffff has been reserved
[    0.526664] system 00:01: iomem range 0xffc00000-0xffcfffff has been reserved
[    0.526670] system 00:06: ioport range 0xc80-0xcff could not be reserved
[    0.526675] system 00:09: iomem range 0xfed00000-0xfed003ff has been reserved
[    0.526680] system 00:0a: ioport range 0x900-0x97f has been reserved
[    0.526682] system 00:0a: ioport range 0x4d0-0x4d1 has been reserved
[    0.526686] system 00:0b: ioport range 0xf400-0xf4fe has been reserved
[    0.526689] system 00:0b: ioport range 0x1080-0x10bf has been reserved
[    0.526691] system 00:0b: ioport range 0x10c0-0x10df has been reserved
[    0.526693] system 00:0b: ioport range 0x809-0x809 has been reserved
[    0.526697] system 00:0c: iomem range 0x0-0x9efff could not be reserved
[    0.526699] system 00:0c: iomem range 0x9f000-0x9ffff could not be reserved
[    0.526702] system 00:0c: iomem range 0xc0000-0xcffff could not be reserved
[    0.526704] system 00:0c: iomem range 0xe0000-0xfffff could not be reserved
[    0.526706] system 00:0c: iomem range 0x100000-0xdfe71fff could not be reserved
[    0.526708] system 00:0c: iomem range 0xdfe72000-0xdfefffff has been reserved
[    0.526710] system 00:0c: iomem range 0xdff00000-0xdfffffff has been reserved
[    0.526712] system 00:0c: iomem range 0xffe00000-0xffffffff has been reserved
[    0.526715] system 00:0c: iomem range 0xffa00000-0xffbfffff has been reserved
[    0.526717] system 00:0c: iomem range 0xfec00000-0xfec0ffff has been reserved
[    0.526719] system 00:0c: iomem range 0xfee00000-0xfee0ffff has been reserved
[    0.526721] system 00:0c: iomem range 0xfed20000-0xfed8ffff has been reserved
[    0.526723] system 00:0c: iomem range 0xfeda0000-0xfeda3fff has been reserved
[    0.526725] system 00:0c: iomem range 0xfeda4000-0xfeda4fff has been reserved
[    0.526728] system 00:0c: iomem range 0xfeda5000-0xfeda5fff has been reserved
[    0.526730] system 00:0c: iomem range 0xfeda6000-0xfeda6fff has been reserved
[    0.526732] system 00:0c: iomem range 0xfed18000-0xfed1bfff has been reserved
[    0.526734] system 00:0c: iomem range 0xf8000000-0xfbffffff has been reserved
[    0.561412] pci 0000:00:01.0: PCI bridge, secondary bus 0000:01
[    0.561415] pci 0000:00:01.0:   IO window: 0xe000-0xefff
[    0.561418] pci 0000:00:01.0:   MEM window: 0xf2000000-0xf6efffff
[    0.561421] pci 0000:00:01.0:   PREFETCH window: 0x000000e0000000-0x000000efffffff
[    0.561426] pci 0000:00:1c.0: PCI bridge, secondary bus 0000:09
[    0.561429] pci 0000:00:1c.0:   IO window: 0xd000-0xdfff
[    0.561435] pci 0000:00:1c.0:   MEM window: 0xf1f00000-0xf1ffffff
[    0.561439] pci 0000:00:1c.0:   PREFETCH window: disabled
[    0.561447] pci 0000:00:1c.1: PCI bridge, secondary bus 0000:0b
[    0.561448] pci 0000:00:1c.1:   IO window: disabled
[    0.561454] pci 0000:00:1c.1:   MEM window: 0xf1e00000-0xf1efffff
[    0.561459] pci 0000:00:1c.1:   PREFETCH window: disabled
[    0.561466] pci 0000:00:1c.4: PCI bridge, secondary bus 0000:0c
[    0.561469] pci 0000:00:1c.4:   IO window: 0xc000-0xcfff
[    0.561475] pci 0000:00:1c.4:   MEM window: 0xf1c00000-0xf1dfffff
[    0.561479] pci 0000:00:1c.4:   PREFETCH window: 0x000000f0000000-0x000000f01fffff
[    0.561487] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:03
[    0.561489] pci 0000:00:1e.0:   IO window: disabled
[    0.561494] pci 0000:00:1e.0:   MEM window: 0xf1b00000-0xf1bfffff
[    0.561499] pci 0000:00:1e.0:   PREFETCH window: disabled
[    0.561512] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.561516] pci 0000:00:01.0: setting latency timer to 64
[    0.561523] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.561528] pci 0000:00:1c.0: setting latency timer to 64
[    0.561537] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.561541] pci 0000:00:1c.1: setting latency timer to 64
[    0.561550] pci 0000:00:1c.4: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.561554] pci 0000:00:1c.4: setting latency timer to 64
[    0.561562] pci 0000:00:1e.0: setting latency timer to 64
[    0.561566] bus: 00 index 0 io port: [0x00-0xffff]
[    0.561567] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.561569] bus: 01 index 0 io port: [0xe000-0xefff]
[    0.561571] bus: 01 index 1 mmio: [0xf2000000-0xf6efffff]
[    0.561573] bus: 01 index 2 mmio: [0xe0000000-0xefffffff]
[    0.561574] bus: 01 index 3 mmio: [0x0-0x0]
[    0.561576] bus: 09 index 0 io port: [0xd000-0xdfff]
[    0.561578] bus: 09 index 1 mmio: [0xf1f00000-0xf1ffffff]
[    0.561579] bus: 09 index 2 mmio: [0x0-0x0]
[    0.561580] bus: 09 index 3 mmio: [0x0-0x0]
[    0.561582] bus: 0b index 0 mmio: [0x0-0x0]
[    0.561584] bus: 0b index 1 mmio: [0xf1e00000-0xf1efffff]
[    0.561585] bus: 0b index 2 mmio: [0x0-0x0]
[    0.561586] bus: 0b index 3 mmio: [0x0-0x0]
[    0.561588] bus: 0c index 0 io port: [0xc000-0xcfff]
[    0.561590] bus: 0c index 1 mmio: [0xf1c00000-0xf1dfffff]
[    0.561591] bus: 0c index 2 mmio: [0xf0000000-0xf01fffff]
[    0.561593] bus: 0c index 3 mmio: [0x0-0x0]
[    0.561594] bus: 03 index 0 mmio: [0x0-0x0]
[    0.561596] bus: 03 index 1 mmio: [0xf1b00000-0xf1bfffff]
[    0.561597] bus: 03 index 2 mmio: [0x0-0x0]
[    0.561599] bus: 03 index 3 io port: [0x00-0xffff]
[    0.561600] bus: 03 index 4 mmio: [0x000000-0xffffffff]
[    0.561606] NET: Registered protocol family 2
[    0.576040] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.576226] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.576501] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.576645] TCP: Hash tables configured (established 131072 bind 65536)
[    0.576646] TCP reno registered
[    0.580046] NET: Registered protocol family 1
[    0.580133] checking if image is initramfs... it is
[    1.084853] Freeing initrd memory: 7352k freed
[    1.084889] Simple Boot Flag at 0x79 set to 0x1
[    1.085050] cpufreq: No nForce2 chipset.
[    1.085167] audit: initializing netlink socket (disabled)
[    1.085188] type=2000 audit(1253546598.085:1): initialized
[    1.091381] highmem bounce pool size: 64 pages
[    1.091386] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.092439] VFS: Disk quotas dquot_6.5.1
[    1.092485] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.092973] fuse init (API version 7.10)
[    1.093042] msgmni has been set to 1659
[    1.093180] alg: No test for stdrng (krng)
[    1.093189] io scheduler noop registered
[    1.093191] io scheduler anticipatory registered
[    1.093192] io scheduler deadline registered
[    1.093203] io scheduler cfq registered (default)
[    1.093365] pci 0000:01:00.0: Boot video device
[    1.094795] pcieport-driver 0000:00:01.0: setting latency timer to 64
[    1.094827] pcieport-driver 0000:00:01.0: found MSI capability
[    1.094848] pcieport-driver 0000:00:01.0: irq 2303 for MSI/MSI-X
[    1.094856] pci_express 0000:00:01.0:pcie00: allocate port service
[    1.094867] pci_express 0000:00:01.0:pcie02: allocate port service
[    1.094877] pci_express 0000:00:01.0:pcie03: allocate port service
[    1.094920] pcieport-driver 0000:00:1c.0: setting latency timer to 64
[    1.094969] pcieport-driver 0000:00:1c.0: found MSI capability
[    1.095001] pcieport-driver 0000:00:1c.0: irq 2302 for MSI/MSI-X
[    1.095016] pci_express 0000:00:1c.0:pcie00: allocate port service
[    1.095025] pci_express 0000:00:1c.0:pcie02: allocate port service
[    1.095035] pci_express 0000:00:1c.0:pcie03: allocate port service
[    1.095104] pcieport-driver 0000:00:1c.1: setting latency timer to 64
[    1.095152] pcieport-driver 0000:00:1c.1: found MSI capability
[    1.095184] pcieport-driver 0000:00:1c.1: irq 2301 for MSI/MSI-X
[    1.095199] pci_express 0000:00:1c.1:pcie00: allocate port service
[    1.095211] pci_express 0000:00:1c.1:pcie02: allocate port service
[    1.095221] pci_express 0000:00:1c.1:pcie03: allocate port service
[    1.095290] pcieport-driver 0000:00:1c.4: setting latency timer to 64
[    1.095339] pcieport-driver 0000:00:1c.4: found MSI capability
[    1.095371] pcieport-driver 0000:00:1c.4: irq 2300 for MSI/MSI-X
[    1.095386] pci_express 0000:00:1c.4:pcie00: allocate port service
[    1.095395] pci_express 0000:00:1c.4:pcie02: allocate port service
[    1.095405] pci_express 0000:00:1c.4:pcie03: allocate port service
[    1.095480] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.095559] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.095669] ACPI: AC Adapter [AC] (on-line)
[    1.120412] ACPI: Battery Slot [BAT0] (battery present)
[    1.120471] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    1.260024] ACPI: Lid Switch [LID]
[    1.260060] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.260065] ACPI: Power Button (CM) [PBTN]
[    1.260100] input: Sleep Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    1.260102] ACPI: Sleep Button (CM) [SBTN]
[    1.260532] ACPI: SSDT DFE72CB4, 02C8 (r1  PmRef  Cpu0Ist     3000 INTL 20050624)
[    1.260805] ACPI: SSDT DFE7264A, 05E5 (r1  PmRef  Cpu0Cst     3001 INTL 20050624)
[    1.261075] Monitor-Mwait will be used to enter C-1 state
[    1.261078] Monitor-Mwait will be used to enter C-2 state
[    1.261080] Monitor-Mwait will be used to enter C-3 state
[    1.261091] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.261111] processor ACPI_CPU:00: registered as cooling_device0
[    1.261114] ACPI: Processor [CPU0] (supports 8 throttling states)
[    1.261380] ACPI: SSDT DFE72F7C, 00C4 (r1  PmRef  Cpu1Ist     3000 INTL 20050624)
[    1.261614] ACPI: SSDT DFE72C2F, 0085 (r1  PmRef  Cpu1Cst     3000 INTL 20050624)
[    1.261915] ACPI: CPU1 (power states: C1[C1] C2[C2] C3[C3])
[    1.261929] processor ACPI_CPU:01: registered as cooling_device1
[    1.261932] ACPI: Processor [CPU1] (supports 8 throttling states)
[    1.263655] thermal LNXTHERM:01: registered as thermal_zone0
[    1.263813] ACPI: Thermal Zone [THM] (36 C)
[    1.263856] isapnp: Scanning for PnP cards...
[    1.617901] isapnp: No Plug & Play device found
[    1.625136] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    1.625971] brd: module loaded
[    1.626210] loop: module loaded
[    1.626261] Fixed MDIO Bus: probed
[    1.626266] PPP generic driver version 2.4.2
[    1.626308] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    1.626330] Driver 'sd' needs updating - please use bus_type methods
[    1.626337] Driver 'sr' needs updating - please use bus_type methods
[    1.626368] ahci 0000:00:1f.2: version 3.0
[    1.626379] ahci 0000:00:1f.2: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    1.626414] ahci 0000:00:1f.2: irq 2299 for MSI/MSI-X
[    1.626483] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 3 Gbps 0x5 impl SATA mode
[    1.626486] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ems 
[    1.626491] ahci 0000:00:1f.2: setting latency timer to 64
[    1.626661] scsi0 : ahci
[    1.626728] scsi1 : ahci
[    1.626774] scsi2 : ahci
[    1.626955] ata1: SATA max UDMA/133 abar m2048@0xf6ffb800 port 0xf6ffb900 irq 2299
[    1.626957] ata2: DUMMY
[    1.626959] ata3: SATA max UDMA/133 abar m2048@0xf6ffb800 port 0xf6ffba00 irq 2299
[    1.944023] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.009412] ata1.00: ATA-8: TOSHIBA MK3252GSX, LV011D, max UDMA/100
[    2.009414] ata1.00: 625142448 sectors, multi 8: LBA48 NCQ (depth 31/32)
[    2.010268] ata1.00: configured for UDMA/100
[    2.344019] ata3: SATA link down (SStatus 0 SControl 300)
[    2.360089] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK3252GS LV01 PQ: 0 ANSI: 5
[    2.360163] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    2.360177] sd 0:0:0:0: [sda] Write Protect is off
[    2.360179] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.360199] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.360244] sd 0:0:0:0: [sda] 625142448 512-byte hardware sectors: (320 GB/298 GiB)
[    2.360255] sd 0:0:0:0: [sda] Write Protect is off
[    2.360257] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.360276] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.360279]  sda: sda1 sda2 sda3 sda4
[    2.467456] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.467487] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.467524] ata_piix 0000:00:1f.1: version 2.12
[    2.467530] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    2.467561] ata_piix 0000:00:1f.1: setting latency timer to 64
[    2.467624] scsi3 : ata_piix
[    2.467671] scsi4 : ata_piix
[    2.468199] ata4: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6fa0 irq 14
[    2.468201] ata5: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6fa8 irq 15
[    2.648502] ata4.00: ATAPI: TEAC   DVD+/-RW DVW28SLC, A.06, max UDMA/33
[    2.680420] ata4.00: configured for UDMA/33
[    2.691980] ata5: port disabled. ignoring.
[    2.704115] scsi 3:0:0:0: CD-ROM            TEAC     DVD+-RW DVW28SLC A.06 PQ: 0 ANSI: 5
[    2.732456] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda caddy
[    2.732458] Uniform CD-ROM driver Revision: 3.20
[    2.732521] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    2.732548] sr 3:0:0:0: Attached scsi generic sg1 type 5
[    2.733077] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.733095] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    2.733105] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    2.733109] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    2.733151] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    2.737065] ehci_hcd 0000:00:1a.7: debug port 1
[    2.737071] ehci_hcd 0000:00:1a.7: cache line size of 32 is not supported
[    2.737082] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400
[    2.748008] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    2.748058] usb usb1: configuration #1 chosen from 1 choice
[    2.748079] hub 1-0:1.0: USB hub found
[    2.748085] hub 1-0:1.0: 4 ports detected
[    2.748172] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.748182] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.748185] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.748218] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    2.752137] ehci_hcd 0000:00:1d.7: debug port 1
[    2.752143] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.752154] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000
[    2.764008] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.764060] usb usb2: configuration #1 chosen from 1 choice
[    2.764081] hub 2-0:1.0: USB hub found
[    2.764086] hub 2-0:1.0: 6 ports detected
[    2.764163] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.764176] uhci_hcd: USB Universal Host Controller Interface driver
[    2.764191] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.764196] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    2.764199] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    2.764239] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    2.764265] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f20
[    2.764325] usb usb3: configuration #1 chosen from 1 choice
[    2.764344] hub 3-0:1.0: USB hub found
[    2.764349] hub 3-0:1.0: 2 ports detected
[    2.764417] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.764423] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    2.764426] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    2.764461] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    2.764493] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f00
[    2.764551] usb usb4: configuration #1 chosen from 1 choice
[    2.764570] hub 4-0:1.0: USB hub found
[    2.764575] hub 4-0:1.0: 2 ports detected
[    2.764643] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    2.764648] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.764651] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.764682] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    2.764707] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f80
[    2.764764] usb usb5: configuration #1 chosen from 1 choice
[    2.764783] hub 5-0:1.0: USB hub found
[    2.764788] hub 5-0:1.0: 2 ports detected
[    2.764852] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    2.764858] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.764861] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.764894] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    2.764920] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f60
[    2.764976] usb usb6: configuration #1 chosen from 1 choice
[    2.764995] hub 6-0:1.0: USB hub found
[    2.765006] hub 6-0:1.0: 2 ports detected
[    2.765073] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    2.765078] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    2.765081] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.765114] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    2.765140] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40
[    2.765199] usb usb7: configuration #1 chosen from 1 choice
[    2.765220] hub 7-0:1.0: USB hub found
[    2.765224] hub 7-0:1.0: 2 ports detected
[    2.765336] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.781658] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.781663] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.785028] mice: PS/2 mouse device common for all mice
[    2.801057] rtc_cmos 00:04: RTC can wake from S4
[    2.801081] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    2.801112] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    2.801155] device-mapper: uevent: version 1.0.3
[    2.801217] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    2.801273] device-mapper: multipath: version 1.0.5 loaded
[    2.801275] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.801330] EISA: Probing bus 0 at eisa.0
[    2.801337] Cannot allocate resource for EISA slot 1
[    2.801366] EISA: Detected 0 cards.
[    2.801452] cpuidle: using governor ladder
[    2.801543] cpuidle: using governor menu
[    2.801930] TCP cubic registered
[    2.802006] NET: Registered protocol family 10
[    2.802332] lo: Disabled Privacy Extensions
[    2.802587] NET: Registered protocol family 17
[    2.802601] Bluetooth: L2CAP ver 2.11
[    2.802602] Bluetooth: L2CAP socket layer initialized
[    2.802604] Bluetooth: SCO (Voice Link) ver 0.6
[    2.802606] Bluetooth: SCO socket layer initialized
[    2.802631] Bluetooth: RFCOMM socket layer initialized
[    2.802636] Bluetooth: RFCOMM TTY layer initialized
[    2.802637] Bluetooth: RFCOMM ver 1.10
[    2.802856] Marking TSC unstable due to TSC halts in idle
[    2.803132] Using IPI No-Shortcut mode
[    2.803182] registered taskstats version 1
[    2.803276]   Magic number: 9:11:387
[    2.803279] usb usb5: hash matches
[    2.803294] pci_express 0000:00:1c.4:pcie02: hash matches
[    2.803345] rtc_cmos 00:04: setting system clock to 2009-09-21 15:23:20 UTC (1253546600)
[    2.803348] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.803349] EDD information not available.
[    2.803595] Freeing unused kernel memory: 532k freed
[    2.803720] Write protecting the kernel text: 4116k
[    2.803770] Write protecting the kernel read-only data: 1528k
[    2.827607] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    3.065039] usb 1-1: new high speed USB device using ehci_hcd and address 2
[    3.106295] sky2 driver version 1.22
[    3.106338] sky2 0000:09:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.106350] sky2 0000:09:00.0: setting latency timer to 64
[    3.106400] sky2 0000:09:00.0: Yukon-2 FE+ chip revision 0
[    3.106533] sky2 0000:09:00.0: irq 2298 for MSI/MSI-X
[    3.107073] sky2 eth0: addr 00:1d:09:43:48:97
[    3.136663] ohci1394 0000:03:09.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    3.189393] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[16]  MMIO=[f1bff800-f1bfffff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[    3.277231] usb 1-1: configuration #1 chosen from 1 choice
[    3.655341] PM: Starting manual resume from disk
[    3.655344] PM: Resume from partition 8:2
[    3.655345] PM: Checking hibernation image.
[    3.655487] PM: Resume from disk failed.
[    3.682030] EXT4-fs: barriers enabled
[    3.700044] kjournald2 starting.  Commit interval 5 seconds
[    3.700051] EXT4-fs: delayed allocation enabled
[    3.700052] EXT4-fs: file extents enabled
[    3.702229] EXT4-fs: mballoc enabled
[    3.702233] EXT4-fs: mounted filesystem with ordered data mode.
[    3.897063] usb 3-2: new full speed USB device using uhci_hcd and address 2
[    4.072447] usb 3-2: configuration #1 chosen from 1 choice
[    4.313069] usb 6-1: new full speed USB device using uhci_hcd and address 2
[    4.478092] usb 6-1: configuration #1 chosen from 1 choice
[    4.509520] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[344fc000068b81c1]
[    4.717067] usb 7-2: new full speed USB device using uhci_hcd and address 2
[    4.892318] usb 7-2: configuration #1 chosen from 1 choice
[    4.894267] hub 7-2:1.0: USB hub found
[    4.896225] hub 7-2:1.0: 3 ports detected
[    5.177225] usb 7-2.1: new full speed USB device using uhci_hcd and address 3
[    5.301292] usb 7-2.1: configuration #1 chosen from 1 choice
[    5.377225] usb 7-2.2: new full speed USB device using uhci_hcd and address 4
[    5.507286] usb 7-2.2: configuration #1 chosen from 1 choice
[    5.585224] usb 7-2.3: new full speed USB device using uhci_hcd and address 5
[    5.715290] usb 7-2.3: configuration #1 chosen from 1 choice
[    8.009133] udev: starting version 141
[    8.263173] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[    8.509671] input: PC Speaker as /devices/platform/pcspkr/input/input5
[    8.533223] Bluetooth: Generic Bluetooth USB driver ver 0.3
[    8.533311] usbcore: registered new interface driver btusb
[    8.557611] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[    8.587068] usblp0: USB Bidirectional printer dev 2 if 0 alt 0 proto 2 vid 0x04F9 pid 0x0033
[    8.587086] usbcore: registered new interface driver usblp
[    8.587554] usbcore: registered new interface driver ndiswrapper
[    8.602557] iTCO_vendor_support: vendor-support=0
[    8.603786] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[    8.603994] iTCO_wdt: Found a ICH8M TCO device (Version=2, TCOBASE=0x1060)
[    8.604077] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[    8.654014] acpi device:32: registered as cooling_device2
[    8.654658] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2e/device:2f/input/input6
[    8.657107] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[    8.672506] sdhci: Secure Digital Host Controller Interface driver
[    8.672509] sdhci: Copyright(c) Pierre Ossman
[    8.673746] sdhci-pci 0000:03:09.1: SDHCI controller found [1180:0822] (rev 22)
[    8.673769] sdhci-pci 0000:03:09.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    8.676841] mmc0: SDHCI controller on PCI [0000:03:09.1] using DMA
[    8.677281] ricoh-mmc: Ricoh MMC Controller disabling driver
[    8.677283] ricoh-mmc: Copyright(c) Philip Langdale
[    8.677298] ricoh-mmc: Ricoh MMC controller found at 0000:03:09.2 [1180:0843] (rev 12)
[    8.677312] ricoh-mmc: Controller is now disabled.
[    8.717498] usbcore: registered new interface driver hiddev
[    8.721417] input: Broadcom Corp as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2.2/7-2.2:1.0/input/input7
[    8.721591] generic-usb 0003:0A5C:4502.0001: input,hidraw0: USB HID v1.11 Keyboard [Broadcom Corp] on usb-0000:00:1d.2-2.2/input0
[    8.725513] input: Broadcom Corp as /devices/pci0000:00/0000:00:1d.2/usb7/7-2/7-2.3/7-2.3:1.0/input/input8
[    8.729013] generic-usb 0003:0A5C:4503.0002: input,hidraw1: USB HID v1.11 Mouse [Broadcom Corp] on usb-0000:00:1d.2-2.3/input0
[    8.729028] usbcore: registered new interface driver usbhid
[    8.729046] usbhid: v2.6:USB HID core driver
[    8.780063] Linux video capture interface: v2.00
[    8.815393] Linux agpgart interface v0.103
[    8.989246] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[    9.339727] uvcvideo: Found UVC 1.00 device Laptop Integrated Webcam (05a9:2640)
[    9.352041] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).
[    9.352159] uvcvideo: Failed to query (129) UVC control 1 (unit 0) : -32 (exp. 26).
[    9.352161] uvcvideo: Failed to initialize the device (-5).
[    9.352203] usbcore: registered new interface driver uvcvideo
[    9.352225] USB Video Class driver (v0.1.0)
[    9.493838] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    9.493847] nvidia 0000:01:00.0: setting latency timer to 64
[    9.494533] NVRM: loading NVIDIA UNIX x86 Kernel Module  180.44  Mon Mar 23 14:59:10 PST 2009
[    9.566178] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    9.566214] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    9.683086] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input9
[    9.709314] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input10
[   10.000065] Clocksource tsc unstable (delta = -262844302 ns)
[   10.042017] lp: driver loaded but no devices found
[   10.095945] Adding 3903784k swap on /dev/sda2.  Priority:-1 extents:1 across:3903784k
[   10.627481] EXT4 FS on sda3, internal journal on sda3:8
[   11.560695] type=1505 audit(1253561009.256:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2184
[   11.593728] type=1505 audit(1253561009.288:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2188
[   11.593800] type=1505 audit(1253561009.288:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2188
[   11.593832] type=1505 audit(1253561009.288:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2188
[   11.593861] type=1505 audit(1253561009.288:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2188
[   11.685358] type=1505 audit(1253561009.381:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2193
[   11.685520] type=1505 audit(1253561009.381:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2193
[   11.705309] type=1505 audit(1253561009.401:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2197
[   13.674397] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   13.674400] Bluetooth: BNEP filters: protocol multicast
[   13.743472] Bridge firewalling registered
[   15.195585] ppdev: user-space parallel port driver
[   19.307517] sky2 eth0: enabling interface
[   19.307691] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.032098] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control rx
[   22.032240] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1973.076181] usb 2-2: new high speed USB device using ehci_hcd and address 4
[ 1973.217293] usb 2-2: configuration #1 chosen from 3 choices
[ 2258.081078] CE: hpet increasing min_delta_ns to 15000 nsec
[ 3894.989068] CE: hpet increasing min_delta_ns to 22500 nsec
[ 3971.925010] CE: hpet increasing min_delta_ns to 33750 nsec


```

---

### Post by chili555 on 2009-09-22
It seems that *ndiswrapper* is loading and doing nothing and *iwl3945* is not loading. Although ndiswrapper is not my preferred way of driving an Intel 3945, it looks like you have made a somewhat successful attempt to get it going, so let's go with it for now. First, let's see if the Windows .inf and .sys are loaded correctly. Please let us see:```
ndiswrapper -l
```Where did you get the two files? Can you please provide a link? Thanks.

---

### Post by Darknp21 on 2009-09-22
Hey, I typed the code in and its did not give me any output. Thanks!

---

### Post by chili555 on 2009-09-23
> **Darknp21 said:**
> Hey, I typed the code in and its did not give me any output. Thanks!That suggests that ndiswrapper is not installed properly. Now let's try the native driver:```
sudo modprobe iwl3945
lsmod | grep iwl
iwconfig
```Thanks.

---

### Post by Darknp21 on 2009-09-26
The following are the results from the commands: 

[SIZE=3]**Lsmod|grepiwl**[/SIZE]

```

[FONT=Nimbus Roman No9 L][SIZE=3]iwl3945 [/SIZE][/FONT][FONT=Nimbus Roman No9 L][SIZE=3]97912 [/SIZE][/FONT] [FONT=Nimbus Roman No9 L][SIZE=3]0 [/SIZE][/FONT][FONT=Nimbus Roman No9 L][SIZE=3]
[/SIZE][/FONT]
[FONT=Nimbus Roman No9 L][SIZE=3]mac80211 [/SIZE][/FONT][FONT=Nimbus Roman No9 L][SIZE=3]217592 [/SIZE][/FONT] [FONT=Nimbus Roman No9 L][SIZE=3]1 iwl3945[/SIZE][/FONT][FONT=Nimbus Roman No9 L][SIZE=3]
[/SIZE][/FONT]
[FONT=Nimbus Roman No9 L][SIZE=3]led_class [/SIZE][/FONT][FONT=Nimbus Roman No9 L][SIZE=3]12036 [/SIZE][/FONT] [FONT=Nimbus Roman No9 L][SIZE=3]1 iwl3945[/SIZE][/FONT][FONT=Nimbus Roman No9 L][SIZE=3]
[/SIZE][/FONT]
[FONT=Nimbus Roman No9 L][SIZE=3]cfg80211 [/SIZE][/FONT][FONT=Nimbus Roman No9 L][SIZE=3]38288 [/SIZE][/FONT] [FONT=Nimbus Roman No9 L][SIZE=3]2 iwl3945,mac80211[/SIZE][/FONT][FONT=Nimbus Roman No9 L][SIZE=3]
[/SIZE][/FONT]

```


**[SIZE=4][FONT=Nimbus Roman No9 L]Iwconfig[/FONT][/SIZE]**


```

[FONT=Nimbus Roman No9 L][SIZE=3]lo [/SIZE][/FONT][FONT=Nimbus Roman No9 L][SIZE=3]no wireless extensions.[/SIZE][/FONT][FONT=Nimbus Roman No9 L][SIZE=3]
[/SIZE][/FONT]

[FONT=Nimbus Roman No9 L][SIZE=3]eth0 [/SIZE][/FONT][FONT=Nimbus Roman No9 L][SIZE=3]no wireless extensions.[/SIZE][/FONT][FONT=Nimbus Roman No9 L][SIZE=3]
[/SIZE][/FONT]

[FONT=Nimbus Roman No9 L][SIZE=3]pan0 [/SIZE][/FONT][FONT=Nimbus Roman No9 L][SIZE=3]no wireless extensions.
[/SIZE][/FONT]
```[FONT=Nimbus Roman No9 L][SIZE=3]

Thx
[/SIZE][/FONT]

---

### Post by chili555 on 2009-09-27
Good! Now we have iwl3945 loaded along with it's dependencies. Now let's try:```
sudo ifup wlan0
```Now do you have a wireless interface in Network Manager? Can you connect?

---

### Post by Darknp21 on 2009-09-27
I am not sure if this is what i am supposed to get or not but after typing in the code it gave me the output:

```

Ignoring unknown interface wlan0=wlan0

```

---

### Post by mcooke1 on 2009-09-28
I have the same wireless card in my Dell and also recently installed ubuntu and had problems with connecting to my access point. I found that by changing the security settings in the access point from having both TKIP and AES enabled for WPA2/PSK to having just AES enabled fixed the problem. It works perfectly now and I did not change anything else.

---

### Post by Darknp21 on 2009-10-03
Hey mcooke1 i am not really sure how to do the things that u have mentioned above. Can you please provide some assistance. Thx

---

### Post by Darknp21 on 2009-10-05
Also i cant see wireless in my network manager.... and i cant connect to anything...

---

### Post by Darknp21 on 2009-10-09
bump

---

### Post by speed32219 on 2009-10-09
what is the output of :

cat /etc/network/interfaces

---

### Post by Darknp21 on 2009-10-17
The output of the code is 

```

auto lo
iface lo inet loopback

```


THANK YOU SO MUCH FOR YOUR HELP!!!!

---

### Post by kevinrogers1977 on 2009-10-19
i have a similar problem with intel pro 3945 ,it wont connect automatically some times ,i have to manually uncheak "enalbe wireless" for 5 sec and rein-able the cheakbox, i have to do this 3 time sometimes to make it connect, but if i boot windows 7 first it usally connects.

its worth a try

i have win 7/ubuntu 9.04 duaul boot

---

### Post by Darknp21 on 2009-10-20
I dont have a wireless button to uncheck do u know how i can get that button to appear?

---

### Post by kevinrogers1977 on 2009-10-20
is should be on the toolbar at the top.

looks like a signal meter on a mobile

if not this is the command that launched this applet. copied from start-up application.
"nm-applet --sm-disable"(without quotes) ,run in terminal application,accessories,terminal you may have to put sudo in front and enter password.

how ever for me this problem was solved when i upgrade to 9.10 beta.

---

### Post by Darknp21 on 2009-10-21
I upgrade to 9.10 beta but the wireless option still doesnt show up...and the command that you gave me did not work....

---

### Post by kevinrogers1977 on 2009-10-22
ubuntu hould load the driver for wireless on boot,
 
this is pproberly not happening your computer.
 
see if there is a wireless device by typing "ifconfig" ,(post reasult if possible)
 
if there is "iwconfig" should display result of state of wireless.
 
look for "wlan0","wifi0" or simular device ,maybe 0 will be 1 
 
try ifconfig wlan0 up
 
to bring up wireless device.
 
and cheak it is phycaly turn at a wire switch.
 
 
you may have to cofiger the device manully see ubuntu support for this. there are loads of post how to maually configuer a network device.
maybe a more seneour member can help you more 
p.s i am not expert at ubuntu!

---

### Post by arlwsbuntu on 2009-10-22
nm-applet might also die. And NetworkManager might not work.

so a sequence:

sudo service NetworkManager restart

check if nm-applet is running i.e. if icon is not visible then do

nm-spplet &

(yes! I know it should **not** be started like that, but it is buggy and it dies and you really do not want to restart/reload/relogin to your desktop if you;re having gazillion ssh connections, zillion firefox windows and tens of other projects lying there. nm-applet tends to die).

Also check out possible module parameters for your wifi module, and try adding those to /etc/modules.d/options.

(yes! I do know /etc/modules.d/options is deprecated).

The best way to find out options for your module is either to use string to your module binary (MODULENAME.ko), or try to find out the missing documentation and all the deprecations / zilliards of false information using google. Some of the options might even work!

//arl

---

### Post by mrcet007 on 2009-11-12
install linux-backport-modules from synaptic for ur kernel version.and tell me the result.

---

