---
title: "intel_8x0 soundcard not detected after upgrade to Dapper"
date: 2006-06-02
forum: Multimedia &amp; Video
---

### Post by bjtuna on 2006-06-02
I upgraded from Breezy to Dapper and everything seems fine except that my sound no longer works. 

'lsmod' shows that the snd_intel8x0 module isn't being loaded. I can load it manually with 'modprobe snd_intel8x0' and that seems to load fine. 

I try to restart ALSA and get:

```

/etc/init.d/alsa-utils start
 * Setting up ALSA...  * warning: 'alsactl restore' failed with error message 'alsactl: load_state:1236: No soundcards found...'... Invalid card number.

```

Here's my /etc/modprobe.d/alsa-base:

```

cat /etc/modprobe.d/alsa-base
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
#options snd-bt87x index=-2
#options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
#options snd-via82xx-modem index=-2

```

and:

```

cat /proc/asound/cards
0 [ICH6           ]: ICH4 - Intel ICH6
                     Intel ICH6 with AD1980 at 0xdfebfe00, irq 23


```

---

### Post by bjtuna on 2006-06-05
Nevermind it's working, if anyone wants to know how I fixed it, just ask and I'll post what I know.

---

### Post by Ben Branch on 2006-06-05
[QUOTE=bjtuna]Nevermind it's working, if anyone wants to know how I fixed it, just ask and I'll post what I know.[/QUOTE]

I've got an intel_8x0 that stopped working too ... tried a number of things,
but so far no joy ...  would greatly appreciate any tips! Thanks in advance.

Ben

---

### Post by bjtuna on 2006-06-05
Ok i lied, it doesn't totally work. if I add 'snd-intel8x0' to /etc/modules, I can get sound through programs that can use OSS sound, like BMP or XMMS. Things that require ALSA are still borked; ie. alsamixer still gives me an error:

```

alsamixer: function snd_ctl_open failed for default: No such device

```

---

