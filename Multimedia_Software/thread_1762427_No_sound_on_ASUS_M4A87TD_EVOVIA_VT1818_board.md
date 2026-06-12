---
title: "No sound on ASUS M4A87TD EVO/VIA VT1818 board"
date: 2011-05-19
forum: Multimedia Software
---

### Post by Wishy2009 on 2011-05-19
I have an ASUS M4A87TD EVO motherboard which has a VIA VT1818 audio chipset but I don't get any sound output. No Linux driver is listed as available from VIA for my chip.

ASUS board specs [http://uk.asus.com/Motherboards/AMD_AM3/M4A87TD_EVO/#specifications](http://uk.asus.com/Motherboards/AMD_AM3/M4A87TD_EVO/#specifications)
VIA driver list [http://www.via.com.tw/en/support/drivers.jsp](http://www.via.com.tw/en/support/drivers.jsp)

Sound works fine fine in 32 bit XP and also in the Splashtop powered ExpressGate 
[http://en.wikipedia.org/wiki/Splashtop](http://en.wikipedia.org/wiki/Splashtop)
which is Linux based. From this I conclude that my hardware set up is OK and that there must be *some* way to get it working on Ubuntu (10.04 64bit although I've tried the 32bit flavour as well with no difference).

I've been through the Comprehensive Sound Problem Solutions Guide sticky and the results of going through the trouble-shooting list are as below.

aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: HDA Generic [HDA Generic]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```lspci -v
```
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
    Subsystem: ATI Technologies Inc SBx00 Azalia (Intel HDA)
    Flags: bus master, slow devsel, latency 64, IRQ 16
    Memory at f9cf8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

```Not listed under VIA at 
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-VIA](http://www.alsa-project.org/main/index.php/Matrix:Vendor-VIA)

Also on suggestion from another thread
/etc/modprobe.d/alsa-base.conf
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
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
```
Heeeeelllllllllllllllllllllllllllllllllllppppppppppppp please!:confused: 

Any suggestions written as if you were talking to a LInux Noob would be much appreciated as .....I am one.:)
Thanks

---

### Post by Wishy2009 on 2011-05-19
Also tried the following to no avail

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
and then....
sudo apt-get install linux-sound-base alsa-base alsa-utils

---

### Post by Wishy2009 on 2011-05-23
Fixed

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/614984/comments/6](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/614984/comments/6) did it for me.:D

---

