---
title: "alsamixer not keeping default sound card"
date: 2014-05-01
forum: Multimedia Software
---

### Post by ronb19495 on 2014-05-01
alsamixer on trusty is not keeping my xonar d2x as default sound output any ideas folks
regards Ron

---

### Post by CraigPid on 2014-05-02
After you set alsamixer the way you want it try "sudo alsactl store"
I'm not sure if that will work for your problem but it does save the volume levels so it's worth a try.

---

### Post by ronb19495 on 2014-05-02
Thanks CraigPid it was ok last night but now its back to usb as default,tried your suggestion not working either must be a bug in alsamixer
regards Ron

---

### Post by CraigPid on 2014-05-03
Do you have a file /etc/modprobe.d/alsa-base.conf ?
In mine I have these lines at the end.

# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2
options snd-ice1712 index=0
options snd-hda-intel index=1,2

As it says in the line with "options snd-usb-audio index=-2"
keeps the usb audio device from loading into slot 0.
Notice that it's -2 not 2
the next line tells my M-Audio card to load in slot  0
and my onboard card & hdmi to load in slots 1 & 2 
Slot 0 being the default card.
If you don't have the file just create it.
I've tried to use this in different distros and it usually works but once or twice
it made one of the cards not show up on boot.If that happens you would just backtrack 
your changes.
Sorry about the other answer but I was at work & didn't have too much time too
think about it.
Oh and you would have to edit alsa-base.conf as sudo.

---

### Post by CraigPid on 2014-05-03
I think the reason it was ok and then went back to usb is that the first module that loads grabs the 1st slot.

---

### Post by ronb19495 on 2014-05-03
ok heres the output from /etc/modprobe.d/alsa-base.conf
 autoloader aliases
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
this is huge its to much for old me the sound card must be causing this I have onboard sound which is disabled in the bios and I have usb headset which is plugged in but turned off in pulseaudio

---

### Post by ronb19495 on 2014-05-03
I think I have fixed the problem ,I disconected usb headset from usb port rebooted and then reset alsamixer rebooted all is ok so far plugged usb headset into front usb port and alsamixer still ok,so what I am thinking when I reinstalled pcie sound card usb headset was still plugged in so it must have made itself default and wouldnt budge till I disconnected it
thanks for your help CraigPid it was your help that made me think about usb headset
regards Ron
I wont mark this as solved yet till I am sure
yes its the usb headset causing this problem when plugged in it is defaul,when usb headset unplugged asus xonar d2x sound card default in alsamixer

---

