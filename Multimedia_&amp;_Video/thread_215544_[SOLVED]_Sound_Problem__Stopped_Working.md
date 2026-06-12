---
title: "[SOLVED] Sound Problem / Stopped Working"
date: 2006-07-14
forum: Multimedia &amp; Video
---

### Post by Malac on 2006-07-14
[SIZE=2][COLOR=Black]My on-board sound seems to have stopped working today, I can't remember whether this happened when I booted up this morning or at some point during the last few hours.
I've tried rebooting and checking the bios, it is enabled.
I am getting the Ubuntu Drums when I login but the volume control  has a red "no-entry" sign on it if I choose "Open Volume Control" I get an error message
[/COLOR][/SIZE][SIZE=1][COLOR=Black]```
No volume control GStreamer plugins and/or devices found
```[/COLOR][/SIZE][SIZE=2][COLOR=Black]
"Preferences" gives me :
[/COLOR][SIZE=1][COLOR=Black]```
The volume control did not find any elements and/or devices to control.
This means either that you don't have the right GStreamer plugins installed,
or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking
the speaker icon on the panel and selecting "Remove From Panel" from the menu
```[/COLOR][/SIZE][/SIZE][SIZE=2][COLOR=Black]
System->Preferences->Sound has no cards listed in the default card pulldown.
I can't use any players as they all say no card available.
I've installed every GStreamer plugin I can find in Synaptic to no avail.
All worked fine yesterday.
I have included some listings in the hope they will help.
cat /proc/asound/modules output:
[/COLOR][/SIZE][SIZE=2][COLOR=Black]```
0 snd_intel8x0
```[/COLOR][/SIZE][SIZE=2][COLOR=Black]
/etc/modprobe.d/alsa-base listing:
[/COLOR][/SIZE][SIZE=2][COLOR=Black]```
# autoloader aliases
install sound-slot-0 modprobe snd-card-0
install sound-slot-1 modprobe snd-card-1
install sound-slot-2 modprobe snd-card-2
install sound-slot-3 modprobe snd-card-3
install sound-slot-4 modprobe snd-card-4
install sound-slot-5 modprobe snd-card-5
install sound-slot-6 modprobe snd-card-6
install sound-slot-7 modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd modprobe --ignore-install snd $CMDLINE_OPTS && { modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { modprobe -Qb snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq $CMDLINE_OPTS && { modprobe -Qba snd-seq-midi snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 modprobe --ignore-install saa7134 $CMDLINE_OPTS && { modprobe -Qb saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
```[/COLOR][/SIZE][SIZE=2][COLOR=Black]
[/COLOR][/SIZE][SIZE=2][COLOR=Black]cat /dev/sndstat output:[/COLOR][/SIZE]
[SIZE=2][COLOR=Black]```

Sound Driver:3.8.1a-980706 (ALSA v1.0.10rc3 emulation code)
Kernel: Linux P700 2.6.15-26-686 #1 SMP PREEMPT Fri Jul 7 19:48:22 UTC 2006 i686Config options: 0

Installed drivers:
Type 10: ALSA emulation

Card config:
Intel 82801BA-ICH2 with AD1885 at 0xe800, irq 201

Audio devices:
0: Intel 82801BA-ICH2 (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
7: system timer

Mixers:
0: Analog Devices AD1885
```[/COLOR][/SIZE]

---

### Post by bogaboga on 2006-07-14
I solved it this way:

I completely shut off the system and rebooted it. When this was done, the system worked perfectly. Hope this helps.

---

### Post by Malac on 2006-07-14
Solved it.
The problem was my User permissions were somehow screwed up.
I just went into Users and Groups and set everything to on, logged out and back in again and all was well.
Thanks for the help.

---

