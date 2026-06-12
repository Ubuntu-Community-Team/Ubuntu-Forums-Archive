---
title: "Buzzing static audio problem!"
date: 2009-02-05
forum: Multimedia Software
---

### Post by Schmetzl on 2009-02-05
Argh, I've been holding out on posting about this, searching the forums for answers for what seems like ages now - I know I am not the only one with this problem - but after having this same problem with Ubuntu 8.04 and now with Xubuntu 8.10 on my (older) laptop I figure I'll give it a try.

When I open audio files with any audio program or Firefox (as well as YouTube etc), the sound plays but with a LOUD buzzing, clicky static sound over top.  This doesn't happen when I play videos files with Movie Player though.

I have tried fooling around with the mixer, changing all the levels but the only one that seems to make a difference is the PCM level: of course when I cut the PCM level the buzzing goes away but so does the sound I am trying to listen to.

Any ideas?

---

### Post by Ptero-4 on 2009-02-05
maybe you need to open (requires admin privileges) /etc/modprobe.d/alsa-base (if you use alsa) and add option snd-hda-intel model=3stack at the bottom. Then restart alsa (/etc/init.d/alsa restart).

---

### Post by Schmetzl on 2009-02-06
Hi there, thanks for the reply.
Like this:

---

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
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
options snd-hda-intel model=3stack

---

???  Not sure if that's what you meant but it doesn't fix the problem.  What is this supposed to do?

---

### Post by Ptero-4 on 2009-02-06
Yeah. That was what I meant.
What it does is to "fix" some oddities in "intel-based" "high definition audio" soundchips (included in lots of laptops). Thing is, it only works if you´re using alsa (ubuntu 7.04 and later have pulseaudio enabled by default instead of alsa). If it didn´t work you might need to reboot (just to be sure) and if it still won´t work chances are you´re using pulseaudio.

---

### Post by Schmetzl on 2009-02-08
Hi there.

Well, no improvements for the audio files, it's still buzzing (using Listen, Rhthymbox, etc - video files sound fine though.  That's what I don't understand...

This is a Xubuntu 8.10 that I just installed, I looked for Pulseaudio and couldn't find it (looks like it's not installed actually), and the "sound" settings manager (Xfce) doesn't give an options about Alsa/PulseAudio etc like normal Ubuntu does....

Any other ideas?

Thanks.

---

