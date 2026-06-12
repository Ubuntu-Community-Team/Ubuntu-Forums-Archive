---
title: "samsung N130 RTL8192SE wireless fails after reboot in 10.10 maverick"
date: 2010-10-13
forum: Networking &amp; Wireless
---

### Post by roadrash on 2010-10-13
I have just installed 10.10 maverick meerkat on A samsung N130.  I had the wireless working from the live cd so I installed it. The wireless worked on the reboot after install and i was able to enter the wpa key and get net access.  However, the next time I booted it from a cold start the wireless would not connect anymore and keeps asking for the key again.  There is no activity from the lights on the router either so its not even trying to connect even though network manager shows it is.

cam anyone help

here is the output of lspci -v

> 
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
	Subsystem: Samsung Electronics Co Ltd Device c05d
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information: Len=09 <?>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
	Subsystem: Samsung Electronics Co Ltd Device c05d
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f0000000 (32-bit, non-prefetchable) [size=512K]
	I/O ports at 1800 [size=8]
	Memory at d0000000 (32-bit, prefetchable) [size=256M]
	Memory at f0200000 (32-bit, non-prefetchable) [size=256K]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [90] MSI: Enable- Count=1/1 Maskable- 64bit-
	Capabilities: [d0] Power Management version 2
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
	Subsystem: Samsung Electronics Co Ltd Device c05d
	Flags: bus master, fast devsel, latency 0
	Memory at f0080000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: [d0] Power Management version 2

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
	Subsystem: Samsung Electronics Co Ltd Device c05d
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at f0440000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [130] Root Complex Link
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: f0100000-f01fffff
	Prefetchable memory behind bridge: 0000000040000000-00000000401fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Samsung Electronics Co Ltd Device c05d
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Root Complex Link
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: 40200000-405fffff
	Prefetchable memory behind bridge: 00000000f0500000-00000000f05fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Samsung Electronics Co Ltd Device c05d
	Capabilities: [a0] Power Management version 2
	Capabilities: [100] Virtual Channel
	Capabilities: [180] Root Complex Link
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Samsung Electronics Co Ltd Device c05d
	Flags: bus master, medium devsel, latency 0, IRQ 23
	I/O ports at 1820 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Samsung Electronics Co Ltd Device c05d
	Flags: bus master, medium devsel, latency 0, IRQ 19
	I/O ports at 1840 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Samsung Electronics Co Ltd Device c05d
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 1860 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
	Subsystem: Samsung Electronics Co Ltd Device c05d
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 1880 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
	Subsystem: Samsung Electronics Co Ltd Device c05d
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at f0444000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Capabilities: [50] Subsystem: Samsung Electronics Co Ltd Device c05d

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
	Subsystem: Samsung Electronics Co Ltd Device c05d
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information: Len=0c <?>
	Kernel modules: leds-ss4200, iTCO_wdt, intel-rng

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 80 [Master])
	Subsystem: Samsung Electronics Co Ltd Device c05d
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 1810 [size=16]
	Capabilities: [70] Power Management version 2
	Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
	Subsystem: Samsung Electronics Co Ltd Device c05d
	Flags: medium devsel, IRQ 5
	I/O ports at 18a0 [size=32]
	Kernel modules: i2c-i801

02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8192E Wireless LAN Controller (rev 01)
	Subsystem: Askey Computer Corp. Device 7160
	Flags: bus master, fast devsel, latency 0, IRQ 16
	I/O ports at 2000 [size=256]
	Memory at f0100000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Legacy Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Virtual Channel
	Capabilities: [160] Device Serial Number 34-e4-62-fe-ff-b6-26-00
	Kernel driver in use: rtl819xE
	Kernel modules: r8192se_pci, r8192e_pci

03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
	Subsystem: Samsung Electronics Co Ltd Device c04d
	Flags: bus master, fast devsel, latency 0, IRQ 42
	I/O ports at 3000 [size=256]
	Memory at f0510000 (64-bit, prefetchable) [size=4K]
	Memory at f0500000 (64-bit, prefetchable) [size=64K]
	[virtual] Expansion ROM at f0520000 [disabled] [size=128K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Endpoint, MSI 01
	Capabilities: [ac] MSI-X: Enable- Count=2 Masked-
	Capabilities: [cc] Vital Product Data
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Virtual Channel
	Capabilities: [160] Device Serial Number 01-00-00-00-00-00-00-00
	Kernel driver in use: r8169
	Kernel modules: r8169



---

### Post by fight2survive on 2010-10-13
i have the same computer, same wireless card and the same problem...
roadrash, does it keeps asking you for the password over and over again when you try to connect to a network?

---

### Post by roadrash on 2010-10-13
yes it does.
I just connected it to wired connection & did an update which was a kernal update & after a reboot I had got wireless back again.  But as before as soon as I shut down completely & restarted it had stopped again.  I'm starting to wonder if its a module thats present after an install/upgrade but not being loaded at startup.

---

### Post by fight2survive on 2010-10-13
possible, but just by looking at all the recent topics about wireless issues in 10.10 on these forums i guess its a thing in the code of maverick itself that will need to be fixed...

---

### Post by fight2survive on 2010-10-13
that makes me wonder, does the people who create/program/work on ubuntu check out this forums?

---

### Post by roadrash on 2010-10-14
Ok I have found that if I open network manager and delete any stored wireless connections before I shutdown, the next time I boot up I can get connected after entering selecting the connection & entering in the key again.
For some reason it wont connect at startup if its using a ng  connection.
All I can say is there must be a bug in network manager or something.

I also found this site which has some info on getting wireless on the N130 in linux.[http://www.voria.org/forum/viewtopic.php?f=3&t=555&p=4067]("http://www.voria.org/forum/viewtopic.php?f=3&t=555&p=4067")

anyway here is my lsmod output which shows the wireless module is being loaded.

> 
Module                  Size  Used by
michael_mic             1744  8 
arc4                    1165  4 
parport_pc             26058  0 
ppdev                   5556  0 
binfmt_misc             6599  1 
snd_hda_codec_realtek   217980  1 
snd_hda_intel          22107  2 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
joydev                  8735  0 
i915                  291004  3 
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
drm_kms_helper         30200  1 i915
snd_seq_midi_event      6047  1 snd_seq_midi
r8192se_pci           465322  0 
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
drm                   168054  4 i915,drm_kms_helper
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               55847  0 
intel_agp              26360  2 i915
samsung_laptop          3745  0 
psmouse                59033  0 
videodev               43098  1 uvcvideo
r8192e_pci            249279  0 
serio_raw               4022  0 
snd                    49006  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
v4l1_compat            13359  2 uvcvideo,videodev
i2c_algo_bit            5168  1 i915
led_class               2633  0 
video                  18712  1 i915
soundcore                880  1 snd
agpgart                32011  2 drm,intel_agp
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
output                  1883  1 video
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
r8169                  36489  0 
mii                     4425  1 r8169



---

### Post by roadrash on 2010-10-14
I have now filed a bug report in launchpad here: 

[COLOR="Red"][https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/660562]("https://bugs.launchpad.net/ubuntu/+source/network-managerhttps://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/660562")
[/COLOR]
hopefully it will get a fix soon

---

### Post by jacksonz123z on 2010-10-16
Try WICD it fixed the problem for me.

---

### Post by roadrash on 2010-10-23
I found the answer, its not network manager, its a kernel problem.  If I install the driver supplied by realtek it works perfectly.
go here for instructions: [http://ubuntuforums.org/showthread.php?p=10014569](http://ubuntuforums.org/showthread.php?p=10014569)

hopefully a future kernel update might sort it

---

