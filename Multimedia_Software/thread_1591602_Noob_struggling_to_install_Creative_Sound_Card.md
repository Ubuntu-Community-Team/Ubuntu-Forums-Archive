---
title: "Noob struggling to install Creative Sound Card"
date: 2010-10-09
forum: Multimedia Software
---

### Post by fatwilly6 on 2010-10-09
I am running Ubuntu 10.10 and am trying to get a studio set up going including Midi. I have struggled to get my M-Audio Audiophile to work (see [http://ubuntuforums.org/showthread.php?p=9926686](http://ubuntuforums.org/showthread.php?p=9926686) ) but since I have got nowhere with that particular issue I decided to put a Creative Soundblaster Live! Card with front panel & midi ports (pci) back in the machine.

Although recognised in lspci
dmt@dmt-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge (rev 01)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
00:08.0 RAID bus controller: Promise Technology, Inc. PDC20378 (FastTrak 378/SATA 378) (rev 02)
00:0a.0 Ethernet controller: 3Com Corporation 3c940 10/100/1000Base-T [Marvell] (rev 12)
00:0d.0 Unassigned class [ffff]: Creative Labs SB Live! EMU10k1 (rev ff)
00:0d.1 Unassigned class [ffff]: Creative Labs SB Live! Game Port (rev ff)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc R360 NJ [Radeon 9800 XT]
01:00.1 Display controller: ATI Technologies Inc RV350 NJ [Radeon 9800 XT] (Secondary)

the card will not appear in aplay or arecord.

I have tried running modprobe

dmt@dmt-desktop:~$ sudo modprobe snd-emu10k1
dmt@dmt-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Line6USB [Line6-USB], device 0: TonePort UX2 [TonePort UX2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 1: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Line6USB_1 [Line6-USB], device 0: TonePort UX2 [TonePort UX2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

but to no avail.

Any ideas?

I have looked at many threads but none seem to address this issue - thanks
:(

---

### Post by fatwilly6 on 2010-10-09
> **fatwilly6 said:**
> 
00:0d.0 Unassigned class [ffff]: Creative Labs SB Live! EMU10k1 (rev ff)
00:0d.1 Unassigned class [ffff]: Creative Labs SB Live! Game Port (rev ff)


could this be the problem??

---

### Post by cchhrriiss121212 on 2010-10-09
I would say that those lines are certainly signifying the issue here. The only thing I could find with a similar output is [this]("http://ww.ubuntuforums.org/showthread.php?t=929506") from 2 years back which was solved by a reinstall of the OS.

First you could try booting a live CD environment, and checking to see if the aplay/lspci output shows the same thing.

---

### Post by fatwilly6 on 2010-10-10
Card didn't show up when I booted from CD so I put the card in another slot and altered /etc/modprobe.d/alsa-base.conf to include up to 4 sound cards & added some emu10k1 options as per various threads. Now I get 

sudo lshw -C multimedia
[sudo] password for dmt: 
  *-multimedia:0 UNCLAIMED
       description: Multimedia audio controller
       product: SB Live! EMU10k1
       vendor: Creative Labs
       physical id: d
       bus info: pci@0000:00:0d.0
       version: 07
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=20 mingnt=2
       resources: ioport:a800(size=32)
  *-multimedia:1
       description: Multimedia audio controller
       product: VT8233/A/8235/8237 AC97 Audio Controller
       vendor: VIA Technologies, Inc.
       physical id: 11.5
       bus info: pci@0000:00:11.5
       version: 60
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: driver=VIA 82xx Audio latency=0
       resources: irq:22 ioport:1000(size=256)


and

lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge (rev 01)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:07.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
00:08.0 RAID bus controller: Promise Technology, Inc. PDC20378 (FastTrak 378/SATA 378) (rev 02)
00:0a.0 Ethernet controller: 3Com Corporation 3c940 10/100/1000Base-T [Marvell] (rev 12)
00:0d.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
00:0d.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)

but 

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Line6USB [Line6-USB], device 0: TonePort UX2 [TonePort UX2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 1: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Line6USB_1 [Line6-USB], device 0: TonePort UX2 [TonePort UX2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

despite sudo modprobe snd-emu10k1 being accepted . . .

---

### Post by fatwilly6 on 2010-10-10
So I re-enabled the Via on board sound, game, midi ports & parallel port in BIOS, removed the Line6 toneport USB device, installed pulseaudio, rebooted and the Creative Card appeared and works. I then plugged the Line6 toneport in & that too worked.

I will post alsa-base.conf for reference tomorrow but the only change I made to that was to allow 8 soundcards and specify index=1 for the Creative card.

Tomorrow's task - see if I can get Midi & Jack working!!

:guitar::P

---

### Post by newfuturevintage on 2010-10-13
In case any one else is having problems of this nature, I thought I'd put my experience here.

Fresh install of 10.10.  

Creative Live! CT4830, which, if I'm not mistaken, is a Live! Value card.

It was working fine outputting analog, but when I went to test its digital output, and plugged a mini plug into it's spdif output jack, I began to get a bunch of snatting via the analog  output and rhythmbox refused to play.  Same with any other audio program.

Rebooted the machine, and still no audio.  I also got the same:

> 00:0d.0 Unassigned class [ffff]: Creative Labs SB Live! EMU10k1 (rev ff)message when running lspci.

Shut down the machine, removed the card and rebooted.  Shut down again, reinstalled the card and rebooted.  Back in business!

---

### Post by fatwilly6 on 2010-10-22
> **fatwilly6 said:**
> 
I will post alsa-base.conf for reference 
<br><br>
```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# actual card's number [default=1]
options snd cards_limit=10
# card(s) specific options
options snd-emu10k1 index=3 extin=0x3fc3 extout=0x1fff
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
options snd-ice1712 model=audiophile
```

---

