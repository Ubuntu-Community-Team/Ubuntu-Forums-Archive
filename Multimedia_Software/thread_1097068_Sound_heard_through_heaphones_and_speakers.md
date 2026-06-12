---
title: "Sound heard through heaphones and speakers"
date: 2009-03-15
forum: Multimedia Software
---

### Post by nmayorga on 2009-03-15
Hullo,

I've got Ubuntu 8.10 installed on a Desktop Sony Vaio VGC-LV1S. Its sound chip is a Realtek ALC889. Sound is working fine but when I plug my headphones in, the front speakers are not disabled.

I've searched through the forums but ALC889 ain't exactly the most popular keyword therein.

I'd appreciate any help.

Thanks in advance.

Cheers,

         Nacho:guitar:

P.S. I've already tried (unsuccessfully) a number of tweaks such as changing the model on the /etc/modprobe.d/alsa-base to vaio, alc889, and a host of other imaginative options :-)

---

### Post by ilcontegis on 2009-04-07
Hi man,
Same problem here with a Vaio TT50B
```
Intel [HDA Intel], dispositivo 0: ALC889 Analog [ALC889 Analog]

```
No way to make the mic work and no way to put away the sound when I plug the headphones.

---

### Post by markbuntu on 2009-04-07
Edit your /etc/modprobe.d/alsa-base file and add

snd-hda-intel model=vaio

to the end of the file. This works for many sony vaio models.

---

### Post by nmayorga on 2009-04-08
Hi markbuntu, :guitar:

Thanks for your message. Nevertheless, I had tried that already but it does not work on my Vaio VGC-LV1S: headphones do not work separately from the front speakers and trying to mute the latter does the same on the former ones.

Cheers,

         Nacho.

---

### Post by D3M3NTU on 2009-04-08
Wish i could help you ..i bearly solved my problem on my own cause the others from the forum would not help me....same problem i had but i have a MSI laptop...and i tryed all the msi model from HDA and one of them worked. I sugest to try all models from hda audio models.txt ( snd-hda-intel model=hippo, or snd-hda-intel model=hippo-assamd) .Im not an expert on linux , i have linux for a week or 2...but its worth a try you have nothing to lose, and if you tryed already i wish you luck to solve your problem cause i know it annoying. 

Good luck.

---

### Post by ilcontegis on 2009-04-08
> **markbuntu said:**
> Edit your /etc/modprobe.d/alsa-base file and add

snd-hda-intel model=vaio

to the end of the file. This works for many sony vaio models.

my alsa-base is empty, but i have everything in alsa-base.conf

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
options snd-hda-intel model=vaio
```

as you can see in the alsa-base.conf I have as well the line that you said, unfortunately it does not work.

---

### Post by curson on 2009-06-23
I have a Sony Vaio VGC-JS2E, audio is flawless, but I have the same problem here as the original poster. Tried both with:

options snd-hda-intel model=sony-assamd

and

options snd-hda-intel model=vaio

in /etc/modprobe.d/alsa-base.conf, but with NO good result.
It's quite annoying :P even if not necessary CRITICAL... hope to keep this thread awake and eventually get some revealing news soon.

---

### Post by starfish5 on 2009-08-04
I'd really love to try these solutions, but when I try to save the file I get denied.  When I type /etc/modprobe.d/alsa-base.conf into terminal I get permission denied.  What am I missing here?  I'm new.

---

### Post by martinbaselier on 2009-08-04
You need to be root, to be able to safe. 
in a terminal type or paste this:
**sudo gedit /etc/mopdprobe.d/alsa.conf**

---

