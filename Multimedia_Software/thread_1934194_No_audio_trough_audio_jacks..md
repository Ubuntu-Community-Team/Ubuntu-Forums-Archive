---
title: "No audio trough audio jacks."
date: 2012-03-01
forum: Multimedia Software
---

### Post by Valemas on 2012-03-01
Dear everyone reading this,

After changing my harddisk of my Dell studio 17 inch laptop, and not having acces to W7, I decided to try Ubuntu.
Loved it from the start, not hard to use, Libre software.
But something didn't work from the start, having tried a lot of things, I decided to try here for some more specific advice.

My problem: 
I got a Dell Studio 1749 and on the left side are 3 audio jacks, the mic input one works, the 2 audio output ones are recognized but dont play sound to my headphones or speakers, the audio does stop playing trough my internal speakers and in the settings in the gnome control panel change to Analog Headphone. 

Side note: When I put the audio jack in the 2nd port it gives sound for about 0.0001s and then just goes mute.
I've checked alsa if it's on mute, and it wasnt. Reinstalled alsa, upgraded alsa. Put something about intel in the alsa-config file. 

Sidenote2: I don't know anything about Ubuntu, I truly suck at this and I'm learning as I go (got WoW working, yay) but this just has me puzzled.

Any help would be appreciated, and if there is anything you need me to upload, explain how (if it's hard ;) ) and I'll do it.

Thanks in advance!

edit: I'm running Ubuntu 11.10.

---

### Post by Yellow Pasque on 2012-03-01
Please give detailed info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by Valemas on 2012-03-02
Ofcourse:
[http://www.alsa-project.org/db/?f=e696a17b4252728a14ed30f9b3452142957ae37a](http://www.alsa-project.org/db/?f=e696a17b4252728a14ed30f9b3452142957ae37a)

---

### Post by jonnyboysmithy on 2012-03-02
With my computer I had to go to the sound preferences and under hardware select a different profile.. see attached screen shot.
Have you played around with that?

---

### Post by Yellow Pasque on 2012-03-02
Use model=dell-m6

---

### Post by Valemas on 2012-03-02
> **Temüjin said:**
> Use model=dell-m6
I already had that in my alsa-base.conf file.
Currently it looks like this:
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
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
options snd-hda-intel model=dell-m6
```

---

### Post by Valemas on 2012-03-02
> **jonnyboysmithy said:**
> With my computer I had to go to the sound preferences and under hardware select a different profile.. see attached screen shot.
Have you played around with that?
Yeah I have tried that, switching to speaker mode with headphones plugged in, changing the output from duplex to analog, etc. etc.

---

