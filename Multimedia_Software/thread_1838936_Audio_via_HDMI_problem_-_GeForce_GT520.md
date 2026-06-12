---
title: "Audio via HDMI problem - GeForce GT520"
date: 2011-09-04
forum: Multimedia Software
---

### Post by anXieTyPB on 2011-09-04
Hi there!

I do try to setup a XBMC machine and the last and most strange problem i have has to do with audio.

I tried so many things to get it working, though...

Here is my current config:

Just installed XBMClive again and did the following:

-removal of any preinstalled NVidia and alsa-drivers / utilities
-installation of Alsa 1.0.24 using this guide: [http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)

-installation of NVidia Drivers by doing this:
```
sudo add-apt-repository ppa:team-iquik/nvidia-vpau
sudo apt-get update
sudo apt-get install nvidia-current libvdpau1
sudo reboot
```


Still there is no sound.

Outputs:

```
xbmc@XBMCLive:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
xbmc@XBMCLive:~$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=1
    HDA NVidia, HDMI 1
    HDMI Audio Output

```

```
xbmc@XBMCLive:~$ uname -a
Linux XBMCLive 2.6.32-33-generic #72-Ubuntu SMP Fri Jul 29 21:08:37 UTC 2011 i686 GNU/Linux

```

```
xbmc@XBMCLive:~$ sudo cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.24.
Compiled on Sep  2 2011 for kernel 2.6.32-33-generic (SMP).

```

```

xbmc@XBMCLive:~$ cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfea7c000 irq 17

```

```

xbmc@XBMCLive:~$  cat /proc/driver/nvidia/version
NVRM version: NVIDIA UNIX x86 Kernel Module  280.13  Wed Jul 27 16:55:43 PDT 2011
GCC version:  gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5)

```


Going to check logfile.

Logfile:
```
Sep  2 23:35:35 XBMCLive kernel: [    0.725797] sd 0:0:0:0: [sda] Write Protect is off
Sep  2 23:35:35 XBMCLive kernel: [    0.725815] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep  2 23:35:35 XBMCLive kernel: [    0.727838] scsi 0:0:1:0: CD-ROM            TEAC     DV-516D          1.06 PQ: 0 ANSI: 5
Sep  2 23:35:35 XBMCLive kernel: [    0.727885]  sda: sda1 sda2 sda3 sda4 < sda5 >
Sep  2 23:35:35 XBMCLive kernel: [    0.781046] sr0: scsi3-mmc drive: 48x/48x cd/rw xa/form2 cdda tray
Sep  2 23:35:35 XBMCLive kernel: [    0.781049] Uniform CD-ROM driver Revision: 3.20
Sep  2 23:35:35 XBMCLive kernel: [    0.781160] sr 0:0:1:0: Attached scsi generic sg1 type 5
Sep  2 23:35:35 XBMCLive kernel: [    0.781247] sd 0:0:0:0: [sda] Attached SCSI disk
Sep  2 23:35:35 XBMCLive kernel: [    0.781257] Freeing unused kernel memory: 668k freed
Sep  2 23:35:35 XBMCLive kernel: [    0.781487] Write protecting the kernel text: 4676k
Sep  2 23:35:35 XBMCLive kernel: [    0.781514] Write protecting the kernel read-only data: 1848k
Sep  2 23:35:35 XBMCLive kernel: [    0.795089] ramzswap: disk size set to 1807032 kB
Sep  2 23:35:35 XBMCLive kernel: [    0.799246] udev: starting version 151
Sep  2 23:35:35 XBMCLive kernel: [    0.844022] Adding 1807028k swap on /dev/ramzswap0.  Priority:100 extents:1 across:1807028k SS
Sep  2 23:35:35 XBMCLive kernel: [    0.856528] Linux agpgart interface v0.103
Sep  2 23:35:35 XBMCLive kernel: [    0.857528] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
Sep  2 23:35:35 XBMCLive kernel: [    0.857562] r8169 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
Sep  2 23:35:35 XBMCLive kernel: [    0.858135] eth0: RTL8168d/8111d at 0xf86fe000, d0:27:88:0b:dc:f8, XID 081000c0 IRQ 27
Sep  2 23:35:35 XBMCLive kernel: [    0.884927] Console: switching to colour frame buffer device 100x37
Sep  2 23:35:35 XBMCLive kernel: [    0.904654] pata_via 0000:04:01.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Sep  2 23:35:35 XBMCLive kernel: [    0.905665] scsi2 : pata_via
Sep  2 23:35:35 XBMCLive kernel: [    0.905756] scsi3 : pata_via
Sep  2 23:35:35 XBMCLive kernel: [    0.905822] ata3: PATA max UDMA/133 cmd 0xec00 ctl 0xe880 bmdma 0xe400 irq 18
Sep  2 23:35:35 XBMCLive kernel: [    0.905824] ata4: PATA max UDMA/133 cmd 0xe800 ctl 0xe480 bmdma 0xe408 irq 18
Sep  2 23:35:35 XBMCLive kernel: [    1.144033] usb 4-2: new full speed USB device using uhci_hcd and address 2
Sep  2 23:35:35 XBMCLive kernel: [    1.326382] usb 4-2: configuration #1 chosen from 1 choice
Sep  2 23:35:35 XBMCLive kernel: [    1.339339] usbcore: registered new interface driver hiddev
Sep  2 23:35:35 XBMCLive kernel: [    1.341514] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.0/input/input3
Sep  2 23:35:35 XBMCLive kernel: [    1.341705] generic-usb 0003:046D:C52E.0001: input,hidraw0: USB HID v1.11 Keyboard [Logitech USB Receiver] on usb-0000:0$
Sep  2 23:35:35 XBMCLive kernel: [    1.344729] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.2/usb4/4-2/4-2:1.1/input/input4
Sep  2 23:35:35 XBMCLive kernel: [    1.344810] generic-usb 0003:046D:C52E.0002: input,hiddev96,hidraw1: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-$
Sep  2 23:35:35 XBMCLive kernel: [    1.344828] usbcore: registered new interface driver usbhid
Sep  2 23:35:35 XBMCLive kernel: [    1.344861] usbhid: v2.6:USB HID core driver
Sep  2 23:35:35 XBMCLive kernel: [    1.520618] EXT4-fs (sda1): mounted filesystem with ordered data mode
Sep  2 23:35:35 XBMCLive kernel: [    4.851885] udev: starting version 151
Sep  2 23:35:35 XBMCLive kernel: [    4.919989] vga16fb: mapped to 0xc00a0000
Sep  2 23:35:35 XBMCLive kernel: [    4.919992] vga16fb: not registering due to another framebuffer present
Sep  2 23:35:35 XBMCLive kernel: [    4.934402] Adding 976888k swap on /dev/sda5.  Priority:-1 extents:1 across:976888k
Sep  2 23:35:35 XBMCLive kernel: [    4.953287] intel_rng: FWH not detected
Sep  2 23:35:35 XBMCLive kernel: [    5.014366] lp: driver loaded but no devices found
Sep  2 23:35:35 XBMCLive kernel: [    5.057292] r8169: eth0: link up
Sep  2 23:35:35 XBMCLive kernel: [    5.057302] r8169: eth0: link up
Sep  2 23:35:35 XBMCLive kernel: [    5.084490] snd_hda_intel 0000:01:00.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
Sep  2 23:35:35 XBMCLive kernel: [    5.084493] hda_intel: Disabling MSI
Sep  2 23:35:35 XBMCLive kernel: [    5.456726] nvidia: module license 'NVIDIA' taints kernel.
Sep  2 23:35:35 XBMCLive kernel: [    5.456729] Disabling lock debugging due to kernel taint
Sep  2 23:35:35 XBMCLive kernel: [    6.268508] HDMI status: Codec=0 Pin=4 Presence_Detect=0 ELD_Valid=0
Sep  2 23:35:35 XBMCLive kernel: [    6.332505] HDMI status: Codec=0 Pin=5 Presence_Detect=0 ELD_Valid=0
Sep  2 23:35:35 XBMCLive kernel: [    6.460756] input: HDA NVidia HDMI/DP as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card0/input5
Sep  2 23:35:35 XBMCLive kernel: [    6.460802] input: HDA NVidia HDMI/DP as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card0/input6
Sep  2 23:35:35 XBMCLive kernel: [    6.461015] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Sep  2 23:35:35 XBMCLive kernel: [    6.461051] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
Sep  2 23:35:35 XBMCLive kernel: [    6.462364] NVRM: loading NVIDIA UNIX x86 Kernel Module  280.13  Wed Jul 27 16:55:43 PDT 2011
Sep  2 23:35:35 XBMCLive kernel: [    6.926087] lirc_dev: IR Remote Control driver registered, major 61
Sep  2 23:35:35 XBMCLive kernel: [    6.928613] lirc_mceusb: Windows Media Center Edition USB IR Transceiver driver for LIRC 1.90
Sep  2 23:35:35 XBMCLive kernel: [    6.928615] lirc_mceusb: Daniel Melander <lirc@rajidae.se>, Martin Blatter <martin_a_blatter@yahoo.com>, Dan Conti <dcon$
Sep  2 23:35:35 XBMCLive kernel: [    6.928638] usbcore: registered new interface driver lirc_mceusb
Sep  2 23:35:38 XBMCLive kernel: [    9.240604] HDMI hot plug event: Codec=0 Pin=5 Presence_Detect=1 ELD_Valid=0
Sep  2 23:35:38 XBMCLive kernel: [    9.252013] HDMI status: Codec=0 Pin=5 Presence_Detect=1 ELD_Valid=0
Sep  2 23:35:38 XBMCLive kernel: [    9.260174] HDMI hot plug event: Codec=0 Pin=5 Presence_Detect=0 ELD_Valid=1
Sep  2 23:35:38 XBMCLive kernel: [    9.264017] HDMI status: Codec=0 Pin=5 Presence_Detect=1 ELD_Valid=1
Sep  2 23:35:39 XBMCLive kernel: [   10.044012] HDMI: detected monitor Philips FTV
Sep  2 23:35:39 XBMCLive kernel: [   10.044014]   at connection type HDMI
Sep  2 23:35:39 XBMCLive kernel: [   10.044017] HDMI: available speakers: FL/FR
Sep  2 23:35:39 XBMCLive kernel: [   10.044022] HDMI: supports coding type LPCM: channels = 2, rates = 44100 48000 88200 176400 192000, bits = 16 20 24
Sep  2 23:35:39 XBMCLive kernel: [   10.044026] HDMI: supports coding type AC-3: channels = 6, rates = 44100 48000 88200, max bitrate = 640000


```

Neither speaker-test -Dplughw:0,7 nor speaker-test -Dplughw:0,3 do work. The commands themselves are being executed properly i guess, my TV is just not making any noise, though. I really do'nt have any clue...


Original Posting @ XBMC.org:
[http://forum.xbmc.org/showthread.php?t=109142&page=2](http://forum.xbmc.org/showthread.php?t=109142&page=2)


Hopefully somebody might help me here :>

---

### Post by BicyclerBoy on 2011-09-05
I think XBMC live is built on 10.04 & therefore the nvidia-current is not supporting the GT520.
You need to add the xorg-edgers or x-swat team launchpad ppa for nVidiaXXX..

Try
speaker-test -c 2 -r 48000 -D hw:1,7

Your display only supports multi-channel via AC3 digital pass-thru'.

With X server screen active, HDMI devices connected & turned on...
From a terminal window run:

cat /proc/asound/card1/codec#0.0
cat /proc/asound/card1/codec#1.0
(first one should be mostly blank)

---

### Post by grandsatrap on 2011-10-01
My GeForce GT220 does not play any sound through HDMI either. It is either (i) the video card, (ii) the cable - No. (iii) Ubuntu Lucid Lynx.

I am using analog output from the old fashioned speaker output from the mother board.  I've just upgraded my kernel . Maybe that will fix it.

Maybe this thread will help us: [http://ubuntuforums.org/showthread.php?t=1836421](http://ubuntuforums.org/showthread.php?t=1836421)

---

### Post by BicyclerBoy on 2011-10-01
The GT220 is completely different problem.

The GT520 had a different audio codec arrangement & also needed a much later video driver.

The GT220 works with the std ubuntu nvidia driver package & alsa 1.0.24 from iQuik ppa.

post your 
aplay -l
Might be better to start a new thread..

---

