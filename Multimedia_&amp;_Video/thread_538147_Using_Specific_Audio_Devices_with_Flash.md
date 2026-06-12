---
title: "Using Specific Audio Devices with Flash"
date: 2007-08-29
forum: Multimedia &amp; Video
---

### Post by MenZa on 2007-08-29
I'm currently having some problems with Flash; I'm assuming the issue is that Flash is attempting to output sound to my built-in soundcard, which unfortunately isn't working. I'm therefore using an external sound card, which seems to work fine.

However, Flash doesn't give me any sound, and I'm assuming the whole problem I'm experiencing is due to it outputting to the wrong channel---so can anyone tell me how to instruct Flash on outputting my sound to ALSA device 1, rather than 0?

If not, how can I completely deactivate device 0? Editing /proc/asound/cards?

Here's my /proc/asound/cards

```

 0 [SI7012         ]: ICH - SiS SI7012
                      SiS SI7012 with AD1888 at 0xe800, irq 17
 1 [default        ]: USB-Audio - C-Media USB Headphone Set  
                      C-Media USB Headphone Set   at usb-0000:00:03.0-3, full speed

```

Thanks!

---

### Post by Phurious on 2007-08-31
Not sure if it is your problem but:
```
sudo gedit /etc/modprobe.d/alsa-base
```
Set the index to "0" for which ever sound card you wish to use and save.

---

### Post by MenZa on 2007-09-01
So you're saying I am to open /etc/modprobe.d/alsa-base, scroll down to the bottom where I can see a variety of different drivers (snd-bt87x, saa71134-alsa), etc. in the following syntax:

options <device> index=-2

And find the one I need (I assume snd-intel8x0m) and change its index to 0 like that? I'd like it confirmed.

Cheers :)

---

### Post by Phurious on 2007-09-02
Confirmed.  Those are the steps I had to take to get my USB sound device working.

---

### Post by MenZa on 2007-09-02
Unfortunately, this didn't appear to work for me. Here's my alsa-base:

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
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --Qb snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=0 		# Here's the relevant bit (card I changed)
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
```

The reason I've picked out that card, is that I remember reading something about it on the alsa wiki (with this particular card).

---

