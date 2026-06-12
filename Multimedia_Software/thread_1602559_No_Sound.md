---
title: "No Sound"
date: 2010-10-21
forum: Multimedia Software
---

### Post by Cycron on 2010-10-21
I am on Ubuntu 10.10 (upgraded from 10.04). And I can't get the audio to work, (it wasn't working on 10.04 either) I tried all the different settings in "Sound Preferences". 

I tried running [ALSA Upgrade Script]("http://%22http://ubuntuforums.org/showthread.php?t=1046137"), it downloaded (sudo bash AlsaUpgrade-1.0.23-2.sh -d) but when I tried to compile (sudo bash AlsaUpgrade-1.0.23-2.sh -c) it said ```
alsa-driver-1.0.23 make failed
```Here's the output of **aplay -l**
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```Output of **lspci**```

00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:06.0 Communication controller: Conexant Systems, Inc. Device 2f40
02:00.0 VGA compatible controller: ATI Technologies Inc RV610 [Radeon HD 2400 XT]
02:00.1 Audio device: ATI Technologies Inc RV610 audio device [Radeon HD 2400 PRO]

```I'm using normal earbuds. 
If you need any more info, just ask. I **need** audio. :(\

**EDIT:**
I tried installing pulseaudio instead of ALSA... no luck...

---

### Post by rosiescape on 2010-10-22
I had a similar problem with 10.10 and an nVidia soundcard. I posted the solution in this forum thread:

[http://ubuntuforums.org/showthread.php?t=1598814](http://ubuntuforums.org/showthread.php?t=1598814)

You'll probably need to change the model to your own system, but this might work for you. Let me know if it does.

---

### Post by Cycron on 2010-10-24
ok... I'll look...

---

### Post by Cycron on 2010-10-24
so where do I add the line in? and what exactly do I put in? here's my alsa-base.conf ```
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
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
```

---

### Post by Cycron on 2010-10-29
**Please help... I really need sound. and I feel so close to getting it.**

---

### Post by rosiescape on 2010-10-29
Put the code line directly after this line in your file:  options snd-usb-usx2y index=-2   You'll need to change the model in the line you're adding to one that suits your system.

---

### Post by Cycron on 2010-10-29
it appears I have two audio devices... ATI and nVidia... one the same as yours...

output of sudo lshw -c sound
```
  *-multimedia            
       description: Audio device
       product: MCP61 High Definition Audio
       vendor: nVidia Corporation
       physical id: e
       bus info: pci@0000:00:05.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list
       configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
       resources: irq:22 memory:fe024000-fe027fff
  *-multimedia
       description: Audio device
       product: RV610 audio device [Radeon HD 2400 PRO]
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:02:00.1
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:45 memory:fdcfc000-fdcfffff

```

---

### Post by Cycron on 2010-10-29
I tried using the line you posted (because we seem to have the same thing... except for this "latency=" thing... what's that? ... putting right where you said and it didn't work... idk what's wrong. :(

what line do i enter exactly?

---

### Post by Cycron on 2010-10-31
I don't understand what exactly my line is... it appears I have **2** audio devices.

---

### Post by Cycron on 2011-05-16
bump? cause I still don't have audio working. :'( :cry:

---

