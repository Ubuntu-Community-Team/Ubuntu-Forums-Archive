---
title: "Changing order of sound cards with aplay -l"
date: 2007-05-01
forum: Multimedia &amp; Video
---

### Post by krul on 2007-05-01
Sometimes the order of my two sound cards are swapped.

I've two sound cards (one on-board and one SoundBlaster Audigy). Sometimes after booting the order changes; card 0 will be the on-board and card 1 the Audigy. This mixed things up as the sound configuration (/etc/asound.conf) file is hard coded referring to the specific sound card.

How can I force linux to use always the same order??

```

aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by krul on 2007-05-04
--bump--

---

### Post by trotur on 2007-05-04
> **krul said:**
> Sometimes the order of my two sound cards are swapped.

I have had same problem in every version of ubuntu. I wish that the default sound card could be chosen as early as during the installation progress. Let's see whether it will be possible some day...

However, to force the order of sound cards do this:

1. Check from [http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/) which modules your cards use. I think that your Audigy uses snd-ca0106 (or perhaps snd-emu10k1) and on-board snd-intel8x0. To be sure, run lsmod and ensure that output contains modules snd_ca0106 (or snd_emu10k1) and snd_intel8x0.

2. Edit your alsa config
```
sudo gedit /etc/modprobe.d/alsa-base
```

3. Add following lines at the end of the file
```
options snd-intel8x0 index=-2
options snd-ca0106 index=-1
```
or if your Audigy needed snd-emu10k1, replace above "snd-ca0106" with "snd-emu10k1"

4. Reboot and test sound. Now card 0 should be Audigy and card 1 on-board.

---

### Post by krul on 2007-05-04
Thank you [trotur]("http://ubuntuforums.org/member.php?u=276986") ! This will hopefully do the trick.

I rebooted my machine and at the order for now is correct, but I'll have to see if it will remains for future reboots.
You were right about the modules of the Audigy and Intel. Perfect, I'm really happy with this, finally my sound is **always** working. :guitar:

---

### Post by trotur on 2007-05-05
You're welcome.

---

### Post by krul on 2008-04-24
Just have another computer with onboard soundcard and had to use:

```

options snd_hda_intel index=-2
options snd-ca0106 index=-1

```

Just for future reference/others.

---

### Post by MemoryDump on 2008-04-24
would this be the same thing for users using PulseAudio as well?

this is my alsa-base:

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
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
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
#options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388

options snd-intel8x0 index=-2
options snd_emux_synth index=-1

```
I commented out the first "options snd-intel8x0m index=-2" since I didn't want it loading twice and I didn't see any entries for my Audigy2 card.
Perhaps this is why my sound has been screwy with Pulse :(

I want my Audigy card to always be my primary sound.

---

