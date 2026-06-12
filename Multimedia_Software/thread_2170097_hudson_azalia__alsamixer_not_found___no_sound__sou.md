---
title: "hudson azalia / alsamixer not found /  no sound / sound card not displayed in phonon"
date: 2013-08-24
forum: Multimedia Software
---

### Post by tomski2 on 2013-08-24
hi all


hope that somebody can help because i read many posts and tried many stuff but i still have no sound working on my ubuntu.
FYI, I wrote in bold the important commands, so that it is easier to read my thread.

**lspci -v | grep -A7 -i "audio"**
tomski@liberty:~/Documents$ lspci -v | grep -A7 -i "audio"00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI Device 9902
        Subsystem: Advanced Micro Devices [AMD] nee ATI Device 9902
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at f0344000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel modules: snd-hda-intel

00:04.0 PCI bridge: Advanced Micro Devices [AMD] Family 15h (Models 10h-1fh) Processor Root Port (prog-if 00 [Normal decode])
--
00:14.2 Audio device: Advanced Micro Devices [AMD] Hudson Azalia Controller (rev 01)
        Subsystem: Toshiba America Info Systems Device fb47
        Flags: bus master, slow devsel, latency 32, IRQ 3
        Memory at f0340000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel modules: snd-hda-intel

i have **Gstreamer**, **Pulseaudio** and **Alsa** installed.

I see no sound card in phonon
i cannot play a sound
sound is not muted and is set to maximum
Music and Video do play without sound
no sound card seen in BIOS menu (everything in Bios is enabled)

tomski@liberty:~/Documents$ **alsamixer**
cannot open mixer: No such file or directory

>>> exactly the same with sudo

**cat /proc/asound/cards**
cat: /proc/asound/cards: No such file or directory

**sudo kate /etc/modprobe.d/alsa-base.conf**
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

# Added by TOMSKI after reading a post on a forum
options snd-hda-intel model=generic


I did **export to alsa **(recommended an a post, dont remember exactly where):
[http://www.alsa-project.org/db/?f=2f60c00911b191e4480175325258e303c0dd5c6d](http://www.alsa-project.org/db/?f=2f60c00911b191e4480175325258e303c0dd5c6d)


I hope that somebody can help because I tried since 2 weeks to get this fixed.
That would be cool!

---

