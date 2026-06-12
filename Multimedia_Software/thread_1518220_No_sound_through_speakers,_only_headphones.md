---
title: "No sound through speakers, only headphones"
date: 2010-06-26
forum: Multimedia Software
---

### Post by blackmath on 2010-06-26
Hi, this one has definitely been asked before I know, but I've had no luck after following the obvious guides via google. After updating my kernel my sound stopped working. I followed the sound problems guide in the sticky thread at the top of this forum and I've now got it to the point where I get sound through the headphones but not through the laptop speakers. [Here]("http://www.alsa-project.org/db/?f=c94620a5c45f4b4029606f14c2ac8d1def6c5146") is my sound info (output from alsa-info.sh thingy). I've added various lines to the end of my alsa-base.conf but no luck. 

Any ideas ?

---

### Post by lidex on 2010-06-26
Remove any and all custom entries (those you've added) from alsa-base.conf as well as any config files you may have added. Now reboot and post the output of these commands:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by blackmath on 2010-06-27
Firstly, thankyou for replying. Did exactly what you said:

```

me@m11x:~$ uname -a
Linux m11x 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux
me@m11x:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
me@m11x:~$ dpkg -l | grep 'alsa'
ii  alsa-base                            1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-modules-2.6.32-22-generic       1.0.22.1+dfsg-0ubuntu3+2.6.32-22.36             ALSA modules for kernel 2.6.32-22-generic
ii  alsa-source                          1.0.22.1+dfsg-0ubuntu3                          ALSA driver sources
ii  alsa-utils                           1.0.22-0ubuntu5                                 ALSA utilities
ii  alsamixergui                         0.9.0rc2-1-9                                    graphical soundcard mixer for ALSA soundcard
ii  bluez-alsa                           4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                   0.10.28-1                                       GStreamer plugin for ALSA
me@m11x:~$ head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Realtek ID 665

==> /proc/asound/card1/codec#0 <==
Codec: Nvidia ID d

==> /proc/asound/card1/codec#1 <==
Codec: Nvidia ID d

==> /proc/asound/card1/codec#2 <==
Codec: Nvidia ID d

==> /proc/asound/card1/codec#3 <==
Codec: Nvidia ID d
me@m11x:~$ 

```

Also, it's an Alienware m11x which has 2 headphone jacks, only one of which is outputting sound (the one nearest the mic jack) - the other one used to work too but not since the speakers stopped working.

edit: added my alsa-base.conf which I removed additions from as instructed before rebooting:

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

---

### Post by lidex on 2010-06-27
According to alsa documentation, v 1.0.23 has support for that codec. Use the alsa-upgrade link in my sig.

---

### Post by blackmath on 2010-06-27
thanks - I followed the instructions given in your link and upgraded, everything installed without any problems, but still the same - only output through 2nd headphone jack. After testing according to the instructions I went on to add the line ```
options snd-hda-intel index=-2 model=alienware
``` to my alsa-base.conf as suggested in the link, but that made no difference after rebooting.

No :guitar: for me!

---

### Post by lidex on 2010-06-27
No, don't think you want that index=-2 option in there. Remove it. This is how it should look:
```
options snd-hda-intel model=alienware
```

You added to ```
/etc/modprobe.d/alsa-base.conf
``` correct?

---

### Post by blackmath on 2010-06-27
hi - ok maybe need to edit the instructions cus it says:
> 
3. Lookup your model in HD-Audio-Models.txt and change entry accordingly:
options snd-hda-intel index=-2 model=XXXXX


rebooting...

---

### Post by blackmath on 2010-06-28
...no luck after rebooting with ```
options snd-hda-intel model=alienware
``` in ```
/etc/modprobe.d/alsa-base.conf
```.

---

### Post by blackmath on 2010-06-28
also tried ```
options snd-hda-intel index=0 model=alienware
``` still nothing. 
Anyway, thanks for your help so far! I wish Ubuntu had a 'restore my system to how it was before the update' feature.

---

### Post by blackmath on 2010-06-30
update: I just checked it wasn't a hardware fault by booting with a different OS (Haiku!) and the sound worked in that, so it's definitely a Linux configuration problem.

---

### Post by blackmath on 2010-07-15
After getting really angry about the silence of my laptop I completely removed all alsa and pulseaudio related libs and packages, restarted, found I had inadvertently broken X's config and removed gdm, so had to reinstall my graphics driver and ubuntu-desktop. That solved it! Now I have sound.

---

### Post by lidex on 2010-07-15
Glad you got it working. Persistence pays off sometimes. ;)

---

