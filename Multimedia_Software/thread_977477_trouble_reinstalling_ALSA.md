---
title: "trouble reinstalling ALSA"
date: 2008-11-10
forum: Multimedia Software
---

### Post by Kymus on 2008-11-10
While following the directions to [reinstall ALSA]("http://ubuntuforums.org/showpost.php?p=5131958&postcount=2"), I encountered something that doesn't make much sense to me..

the results I saw were much different from what was posted.

The example given for finding the codec was:


```
aplay -l
cat /proc/asound/card0/codec#* | grep Codec
```


yet my results are completely different:


```
kymus@Shouxing:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
Subdevices: 1/1
Subdevice #0: subdevice #0

```

regardless, I went forward.

the example mentions modifying the line *options snd-hda-intel model=*  in  *etc/modprobe.d/alsa-base*, but after opening *etc/modprobe.d/alsa-base*, I didn't find anything with the word "model" in it...

So now, I am unsure as to how to proceed :confused:

---

### Post by Kymus on 2008-11-12
bump

[img]http://www.stlawrenceotoole.org/school/wp-content/computer_frustration.gif[/img]

---

### Post by Kymus on 2008-11-13
bump

---

### Post by Yellow Pasque on 2008-11-14
The model= line is for snd-hda-intel ("High Def") devices only. nvidia CK804 device is an AC97 card (snd-intel8x0).

---

### Post by Kymus on 2008-11-14
> **Temüjin said:**
> The model= line is for snd-hda-intel ("High Def") devices only. nvidia CK804 device is an AC97 card (snd-intel8x0).

Thank you for the input Temüjin!

I think I must be dense though, because I am getting easily confused here... (i blame the Chinese food leftovers I just had for lunch)

Using the list you provided in your guide, as well as the information you just gave me, what is the codec I am using? Also, what line do I edit in *alsa-base*?

here is a copy and paste from my terminal:

```
kymus@Shouxing:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

and here is the contents of alsa-base:

> # autoloader aliases
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

---

### Post by Yellow Pasque on 2008-11-14
> Also, what line do I edit in alsa-base?
Don't edit anything. The provided list does not apply to your sound device.

---

### Post by Kymus on 2008-11-14
> **Temüjin said:**
> Don't edit anything. The provided list does not apply to your sound device.

Hmm.. I see.

So then my next question is.. do you have any suggestions as to how I can reinstall ALSA?

---

### Post by Kymus on 2008-11-14
**edit**: I looked over the original instructions..

by "reinstall", I mean, re-enable; so that ALSA is as it was before stopping it and attempting to install OSS

---

