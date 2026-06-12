---
title: "Installed new monitor with Built In Webcam/Mic and now sound not working"
date: 2007-12-13
forum: Multimedia &amp; Video
---

### Post by damphoux on 2007-12-13
Just upgraded to a new monitor from Dell with Monitor Integrated Webcam.  Got the monitor and webcam working fine last night and didn't notice until today that now the sound on my regular Audigy sound card and speakers is not working.  My other sound device, a USB Headset I use with Skype is working fine.

When I open alsamixer all it shows only 

[INDENT]Card: Monitor Integrated Webcam
Chip: USB Mixer
View: [Playback] Capture All

     BLANK SCREEN 
[/INDENT]

And the blank screen is where it used to show my Audigy mixer controls, sliders, etc.

```
$ sudo nano /etc/modules
```

Shows
[INDENT]
fuse
lp
sbp2
snd-emu10k1[/INDENT]

with snd-emu10k1 being my sound driver.

```
$ cat /proc/asound/modules
```

shows
[INDENT] 0 snd_usb_audio
 1 snd_usb_audio
 2 snd_emu10k1
[/INDENT]

Index 2 being my Audigy card.   One of the This is where I get confused.   I edit

```
sudo nano /etc/modprobe.d/alsa-base
```

and it looks like all hell broke loose in this file.  Lots of "ignores" and indexes that don't seem to exist:

[INDENT]  GNU nano 2.0.6         File: /etc/modprobe.d/alsa-base                        

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
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd$
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --q$
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe$
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --q$
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modp$
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS &$
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS &$

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbi$

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq$
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
[/INDENT]

Any help is appreciated.  I'm sure the auto loading of the driver for the USB Monitor Integrated Webcam screwed me up, but I am knowledgeless on how to fix it.  Obviously the ultimate goal is to get it all working.

Mike

---

