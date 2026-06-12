---
title: "[SOLVED] Audigy 4 volume problem"
date: 2007-11-21
forum: Multimedia &amp; Video
---

### Post by JohnLM_the_Ghost on 2007-11-21
I have encountered strange problem.

During solving another bug I have produced one more.

Initially I tried making my Audigy to be default soundcard instead of Onboard one.
Following this - [http://alsa.opensrc.org/index.php/MultipleCards]("http://alsa.opensrc.org/index.php/MultipleCards")
I tried advices for both Dapper and Edgy, and the last one seemed sucessful. Though I'm using Dapper Drake.

Well new problem is:
There appeared one more souncard in Volume Control and the Volume is locked to its highest.

I have now disabled Onboard Soundcard in BIOS, so it doesn't show up in list below.

Volume Control lists them as follows:
0: Audigy 4 [SB0400] (Alsa Mixer)
1: SigmaTel STAC9750,51 (OSS Mixer)

I understand these two are the same one Soundcard but diffrent mixers.
Programs I use are configured to use ALSA but now they are not affected by Volume sliders on ALSA mixer and sliders in OSS are locked to their positions (They snap back when i try to adjust them)
Moreover, I have a lot less sliders than i used to have before in ALSA mixer.
There are MASTER, TONE, BASS, TREMBLE, PCM and others missing.

I  tried to revert back config files i had edited to solve the initial problem, I have also tried to reinstall fresh sound drivers as suggested in this - [http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449") - post. No Luck at all.

Some help would be most appreciated.
Thanks in advance.

edited:
I understand this problem is my own fault and its not too common. But I'm not too happy having this bug. I have added some extra info in case it helps.

call 'cat /proc/asound/modules' reports:
```
0 snd_emu10k1
```
so you can see there's now only one Souncard.

call 'cat /proc/asound/cards' reports:
```
0 [Audigy2        ]: Audigy2 - Audigy 4 [SB0400]
                     Audigy 4 [SB0400] (rev.0, serial:0x10211102) at 0xc800, irq 225
```
hmm... irq 255 seems pretty strange, never noticed that before.

call 'cat /etc/modprobe.d/alsa-base' returned
```
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
```
This should be all default

I want to restore default ALSA driver and settings I had and preferably get rid of OSS mixer because I hadn't one before and suspect it has something to do with this.
Only solution now is probably reinstalling the whole system, but I wouldn't be too happy if it comes to that.

Please share even the sligthest idea what could be wrong and how to fix it!

---

### Post by JohnLM_the_Ghost on 2007-11-24
:\

---

### Post by JohnLM_the_Ghost on 2007-12-01
How i could be this silly! Fixed it quite easily!
I was browsing through Synaptic Package Manager before i reinstall to save markings.
Then i had this quick idea of reinstalling any and every package what had anything to do with sound system and ALSA... and everything went to normal again!

---

