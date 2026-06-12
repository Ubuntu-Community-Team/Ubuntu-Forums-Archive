---
title: "No Sound"
date: 2009-10-11
forum: Multimedia Software
---

### Post by gareththegeek on 2009-10-11
I can't seem to get any sound to work on my system.
My system is Xubuntu 9.04 stock kernel with ubuntustudio audio packages installed.
I checked pcm and master volume in alsamixer

Please help.

```
gareth@xubuntu:~$ aplay -l 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: M44 [M Audio Delta 44], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
gareth@xubuntu:~$ lspci -v
...
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
	Subsystem: Giga-byte Technology Device a002
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at fa100000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
...
04:02.0 Multimedia audio controller: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller (rev 02)
	Subsystem: VIA Technologies Inc. Device d633
	Flags: bus master, medium devsel, latency 32, IRQ 18
	I/O ports at d000 [size=32]
	I/O ports at d100 [size=16]
	I/O ports at d200 [size=16]
	I/O ports at d300 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: ICE1712
	Kernel modules: snd-ice1712

```

```
gareth@xubuntu:~$ cat /etc/modprobe.d/alsa-base.conf
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
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2

options snd-hda-intel model=5stack
options snd-ice1712 model=delta44

options snd-hda-intel index=0
options snd-ice1712 index=1
```

---

### Post by antonkedrov on 2009-10-11
hi. please post screenshot of your audiomixer settings. i have the same sound card on my desktop. i can't config my microphone, but output sound work fine.

---

### Post by madsmeg on 2009-10-11
Have you gone through alsamixer in the terminal and made sure there is nothing muted that shouldnt be?

---

### Post by Stochastic on 2009-10-11
Moved to Multimedia & Video.

---

### Post by gareththegeek on 2009-10-11
alsamixer -c 0
[IMG]http://img527.imageshack.us/img527/2406/alsamixer1.png[/IMG]

alsamixer -c 1
[IMG]http://img27.imageshack.us/img27/455/alsamixer2.png[/IMG]

cheers

---

### Post by madsmeg on 2009-10-11
Try unmuting everything, sometimes the set up is wrong, and make sure all volumes are maxed.

---

