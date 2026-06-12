---
title: "Sound Card Permissions"
date: 2006-06-04
forum: Multimedia &amp; Video
---

### Post by capi on 2006-06-04
Okay, so basically, I'm actually think I've found the problem for my sound. First, since I'm not certain on this I'll give you my some command outputs at the end of the post(there also in another thread if you search my post history) . . .

Now, at first I thought the card wasn't being detected at all, but it seems as if the permissions on it got messed up or something. I found by accident that if I use alsamixer in a shell I get. . .

```
alsamixer: function snd_ctl_open failed for default: No such device

```

but, if I simply use sudo it works! Taking it a step further if I go into system->sound I get no card, however if I launch #sudo gnome-control-center and go into sound I get my card.

The Question:
**_How do I change the permissions of my sound card(or whetever is causing this), so that a non-rot user can see and use it?_**

If I'm wrong, which i might be, here is some output.

```
$ lspci | fgrep 'audio'
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)


$ lsmod | grep snd
snd_hda_intel          18964  0
snd_hda_codec         142640  1 snd_hda_intel
snd_intel8x0m          17804  0
snd_intel8x0           33692  1
snd_ac97_codec         92704  2 snd_intel8x0m,snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  1
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  6 snd_hda_intel,snd_hda_codec,snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  9 snd_hda_intel,snd_hda_codec,snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  2 snd
snd_page_alloc         10632  4 snd_hda_intel,snd_intel8x0m,snd_intel8x0,snd_pcm

$ /etc/modprobe.d/alsa-base
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
#options snd-intel8x0m index=-2
options snd-via82xx-modem index=0


```

---

### Post by capi on 2006-06-04
nvm, Found the answer
```

sudo adduser capi audio
```

---

### Post by ktulu1115 on 2006-06-11
I had the same problem, and eventually figured out the same answer you came to.

What doesn't make sense to me is that if you keep an existing /home partition and add a previous account to your new Dapper install as a new user, there seems to be a bug in adding that user to the correct groups - namely 'sound'.  There's a few others that it's not added to either by default.  Just thought I'd point that out in case you run into similar problems with other hardware.

---

### Post by jonkulp on 2008-01-12
Thank You!!!!

---

