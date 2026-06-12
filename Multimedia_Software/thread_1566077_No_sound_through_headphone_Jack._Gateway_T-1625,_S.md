---
title: "No sound through headphone Jack. Gateway T-1625, STAC9250"
date: 2010-09-01
forum: Multimedia Software
---

### Post by GoodyBH on 2010-09-01
I am not getting any sound output from my headphone jack. I realize this has been a common problem for many people, but i have searched and searched forums and cannot find anything that works. The line "*options snd*-*hda*-*intel model=eapd* probe_mask=1 position_fix=1" added to the alsa_base.conf file seemed to solve the problem for people with Sigmatel Stac9250 soundcards. This did not work for me. I am a new ubuntu user running lucid lynx with the most current version of alsa (1.0.23).

Thanks,

Goody

---

### Post by lidex on 2010-09-02
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

---

### Post by GoodyBH on 2010-09-03
[http://www.alsa-project.org/db/?f=a8ea4552d65a5fbbd736b0b6cb8145120987d633](http://www.alsa-project.org/db/?f=a8ea4552d65a5fbbd736b0b6cb8145120987d633)

Output.

---

### Post by lidex on 2010-09-05
If you would please follow the alsa-upgrade link in my sig to get v. 1.0.23
Report your progress.

---

### Post by GoodyBH on 2010-09-06
Followed all the steps from the link in your sig. Alsa is completely updated to 1.0.23. Still I get no sound. I've been working on this all night and it seems it probably has to do with setting the correct model and options for 
options snd-hda-intel model = ??

[FONT=Arial]Everyone with the Stac9205 codec seems to be getting their headphone jack to work by setting the model to [/FONT]"eapd", but this is not working for me.

Here is a copy of my Alsa_Base.conf file:

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
options snd-hda-intel model=eapd probe_mask=1 position_fix=1

# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2

[FONT=Arial]am I overlooking something?

-Goody
[/FONT]

---

### Post by lidex on 2010-09-15
*Goody:*
Please remove that line from alsa-base.conf
```
options snd-hda-intel model=eapd probe_mask=1 position_fix=1
```
Replace with this:
```
options snd-hda-intel probe_mask=1
options snd-hda-intel enable=1 index=0 model=lenovo
```
Or this:
```
options snd-hda-intel enable_msi=0 model=eapd
```

---

