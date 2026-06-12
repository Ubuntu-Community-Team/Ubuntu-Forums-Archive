---
title: "No sound from Conexant CXT5047, in desperate need of help"
date: 2007-03-22
forum: Multimedia &amp; Video
---

### Post by IamUnsain on 2007-03-22
Hey everyone,

This is my first post on Ubuntu Forums.  However, I have read many other posts and want to thank everyone in advance for all of the great information they give.  I have figured out everything except for how to get the sound working.  First I guess let me give some insight on where I stand:

1)  I have the most up to date Alsa.
2)  Ubuntu recognizes my sound card.
3)  Everything is unmuted in Alsa Mixer.
4)  There is no possible reason I can find for the sound not to work except a couple of odd quirks.

Here's some more stuff:

lshw output:
```
*-multimedia
             description: Audio device
             product: 82801G (ICH7 Family) High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel
             resources: iomemory:d0340000-d0343fff irq:50

```

lspci -v output:
```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device ff31
        Flags: bus master, fast devsel, latency 0, IRQ 50
        Memory at d0340000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

```

aplay -l output:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

/etc/modules contains:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
sbp2
snd-hda-intel
```

/etc/modprobe.d/alsa-base contains:
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
# Prevent abnormal drivers from grabbing index 0

alias snd-card-0 snd-hda-intel
options snd-card-0 index=0
options snd-hda-intel index=0 model=basic
remove snd-hda-intel { /usr/sbin/alsactl store 0 >/dev/null 2>&1 || : ; }; /sbin/modprobe -r --ignore-remove snd-hda-intel

```

**Here's my couple of quirks**:

These were noted when I reloaded alsa using the command "sudo /etc/init.d/alsasound reload"

1)  The output of the command:
```
Shutting down sound driver: !!!alsactl not found!!! done
Starting sound driver: snd-hda-intel done
No mixer config in /etc/asound.state, you have to unmute your card!

```

2)  A box pops up on Ubuntu desktop that says:
> New Audio playback device detected.
To configure your new audio playback device(null) and possibly set it as default device, open System->Preferences->Sound.

THANKS!  :guitar:  If you need any more information to give some help then please let me know.

---

### Post by IamUnsain on 2007-03-24
After trying some stuff, I ended up corrupting my installing of Ubuntu 6.10.  I installed 6.06LTS to see if it would make any difference.  Would delete this thread if I knew how, I'll just post a new one with new information if I can't fix it myself.  ](*,) :cry:

---

