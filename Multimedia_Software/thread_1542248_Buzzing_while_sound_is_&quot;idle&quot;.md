---
title: "Buzzing while sound is &quot;idle&quot;"
date: 2010-07-30
forum: Multimedia Software
---

### Post by YUMESUKI on 2010-07-30
xubuntu 9.10 64bit
Kernel 2.6.31-22
MSI 890GXM-G65 with Realtek ALC889 integrated sound
Connected with analog "front" output (HDMI & IEC958 not tested)

I  get a rather annoying buzzing sound from my speakers (but not my  headphones) after 10 seconds of no output.  When I hit 'Stop' on Exaile,  MPlayer, etc. I have 10 seconds of silence and then the buzzing will  suddenly start.  The same goes for event sounds, buzzing stops for the  event sound then exactly 10 seconds later- BUZZZZZZZ:(

All inputs are set to mute (via terminal alsamixer)
Played around with other ALSA settings (also via alsamixer)
Buzzing continues even if ALL inputs and outputs are set to MUTE or MIN
I modified alsa-base.conf...
[COLOR=RoyalBlue]Changed the variables[/COLOR] THEN [COLOR=Red]removed the line[/COLOR]:
# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=10 power_save_controller=N
[COLOR=SeaGreen]Inserted a line[/COLOR]:
options snd-hda-intel model=3stack

Although 'options snd-hda-intel model=3stack' "fixed" my low volume issue, I still have buzzing after 10 seconds of silence.

---alsa-base.conf---
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
install  snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && {  /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe  --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install  snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS  && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install  snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS  && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install  snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS  && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ;  /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install  snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS  && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install  snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS  && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install  snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS  && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install  saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS  && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
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
[COLOR=SeaGreen]options snd-hda-intel model=3stack[/COLOR]
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
[COLOR=Red]# Power down HDA controllers after 10 idle seconds
options snd-hda-intel power_save=[COLOR=RoyalBlue]10[/COLOR] power_save_controller=[COLOR=RoyalBlue]N[/COLOR][/COLOR]
---END---

A few other notes...
This is the 2nd of 2 xubuntu 9.10 installs on this system, both with the same issue.
In  my previous install I had also installed 'gnome-media'.  Used gnome's  mixer applet and pulseaudio to control sound.  It was a bit of a  workaround, the buzz was still there but somewhat quieter.  Honestly, I  would much rather not do the same this time around as it introduced  other instabilities and degraded sound quality.  Pulseaudio would also  end up consuming 'large' amounts of memory after several days of uptime.

I do hope someone can help out...
Thanks in advance.

---

### Post by YUMESUKI on 2010-11-11
BZZZZZZZZZZZZZZ

Problem exists still . . .

Is there no one who has any ideas?

---

