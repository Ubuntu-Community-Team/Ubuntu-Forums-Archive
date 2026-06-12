---
title: "Wrong soundchip drivers - speakers don' t mute?"
date: 2011-01-05
forum: Multimedia Software
---

### Post by OttoMann on 2011-01-05
Hello!

I am wondering if I have the right sound drivers installed , because when I plug in the phones in their jack the speakers continue to play together with the phones.
I tried to fix things and made a MESS (even installed some alsa-driver which I now think is not the right one for my hardware - I don't know how to get rid of it and get the right one back).

I am aware of other threads with the same problem; tried the suggested solutions but no improvement.

Installed is Ubuntu 10.04 LTS (dual-boot with WinXp; in windows everything is OK with sound), PAE cernel; updated today.

This are some configurations
lspci -v:

00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
    Subsystem: Micro-Star International Co., Ltd. Device a422
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at ffef8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

  	 	 	 	p { margin-bottom: 0.08in; }  Aplay -l:
 **** List of PLAYBACK Hardware Devices ****  
 card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]  
   Subdevices: 0/1  
   Subdevice #0: subdevice #0  
 card 0: SB [HDA ATI SB], device 1: ALC883 Digital [ALC883 Digital]  
   Subdevices: 1/1  
   Subdevice #0: subdevice #0  
 card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]  
   Subdevices: 0/1  
   Subdevice #0: subdevice #0  
 
and the content of /etc/modprobe.d/alsa-base.conf:

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
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
options snd-hda-intel model=auto

Sorry for the long post.

---

### Post by OttoMann on 2011-01-07
Problem "solved":\

I decided  to install Ubuntu 10.10 and the sound works as it should.

---

