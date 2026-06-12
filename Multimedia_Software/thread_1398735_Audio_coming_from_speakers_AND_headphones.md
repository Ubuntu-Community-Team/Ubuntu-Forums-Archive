---
title: "Audio coming from speakers AND headphones"
date: 2010-02-04
forum: Multimedia Software
---

### Post by sleepee on 2010-02-04
hey everybody..
alright, so i know this is a pretty common issue and has a lot of topics on it already, but i just can't seem to find a solution that works for me...

so my problem is that i can't disable the speakers on my laptop when i plug in my headphones.
in other words, i get sound from both the headphones and the speakers, when the expected behavior is to disable the speakers when headphones are plugged in, and enable the speakers when headphones are unplugged..

i've been looking around the forum and google, and i found a way to adjust the speaker and headphone volume manually in alsamixer.
To adjust the headphone volume on alsamixer, i can raise or lower volume using the "Front" volume bar.
To adjust the speaker volume, i raise or lower volume on the "Speaker" volume bar.

so, it's cool to know that i can do this manually, but i'm sure there's an option i can put in alsa-base.conf to automate this.
i just can't seem to find that option...

anyway, i'm using Ubuntu 9.10 64-bit...and here's my alsa-base.conf file

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
options snd-intel8x0 ac97_quirk=1 buggy_irq=1 enable=1 index=0
options snd-hda-intel model=3stack enable=yes
options snd-hda-intel model=auto position_fix=1 enable=yes
options snd-hda-intel enable_msi=1
options snd_hda_intel model=hp-dv5
# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=10 power_save_controller=N
```and my aplay -l output:

```
sleepee@sleepee-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```i also include some pics from my alsamixer to show what im talking about...
thanks in advance.

---

### Post by Yellow Pasque on 2010-02-05
> options snd-hda-intel model=3stack enable=yes
options snd-hda-intel model=auto position_fix=1 enable=yes
options snd-hda-intel enable_msi=1
options snd_hda_intel model=hp-dv5


I guess this is the stuff you tried? What model laptop do you have? When you plug the headphones in, the speakers should shut up. It's called "jack sensing" and it's often an issue with the model= keyword.

---

### Post by sleepee on 2010-02-05
> **Temüjin said:**
> I guess this is the stuff you tried? What model laptop do you have? When you plug the headphones in, the speakers should shut up. It's called "jack sensing" and it's often an issue with the model= keyword.

wow, i totally forgot about posting my laptop model...
i have a hp dv7 3080

and i actually added those lines because of another sound problem i had.  i had no sound coming from my speakers, only through the subwoofer, so i had to upgrade alsa, add those lines and it got fixed...
well, partially... because i still have this jack sensing issue.

but i couldve sworn that those were the right options to put in..  maybe i overlooked something...

---

### Post by sleepee on 2010-02-05
ok... it's fixed!!!
all i did was upgrade alsa to 1.0.22.1, the latest version...
i actually used the upgrade script and followed the instructions from this thread:
[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

now, no more speaker sound with the headphones in... and when i take them out, the sound output goes back to the speakers
Perfect!!!
:D

---

### Post by bigmike09890 on 2010-02-28
> **sleepee said:**
> 
all i did was upgrade alsa to 1.0.22.1, the latest version...
i actually used the upgrade script and followed the instructions from this thread:
[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)


Thank you. I've been looking for a fix for a while now and this did the trick. It works perfectly on a hp dv6 1230us

---

