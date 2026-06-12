---
title: "Need to disable headphone detection in alsa or to force the speakers on"
date: 2010-05-05
forum: Multimedia Software
---

### Post by morph_89 on 2010-05-05
Hello, this is my first post, im running lucid, and my headphones plug  is broken, it always detects it is plugged, so the speakers are always  off... if i install oss v4, that does not support headphone detection,  my internal speakers work flawlessly.  

But I want to try the alsa ones, plus i coudn't make all my media keys  to  work as i intended when i had oss installed...

here is some information that might be relevant:

lspci
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition  Audio Controller (rev 02)

lsmod | grep snd
snd_hda_codec_conexant    22577  1 
snd_hda_intel          21877  1 
snd_hda_codec          74201  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6  snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5  snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54148  14  snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ls -l /dev/snd
total 0
drwxr-xr-x  2 root root      60  2010-05-05 21:08 by-path
crw-rw----+ 1 root audio 116, 8 2010-05-05  21:08 controlC0
crw-rw----+ 1 root audio 116, 7 2010-05-05 21:08  hwC0D0
crw-rw----+ 1 root audio 116, 6 2010-05-05 20:14 pcmC0D0c
crw-rw----+  1 root audio 116, 5 2010-05-05 20:14 pcmC0D0p
crw-rw----+ 1 root  audio 116, 4 2010-05-05 20:13 pcmC0D1p
crw-rw----+ 1 root audio 116, 3  2010-05-05 21:08 seq
crw-rw----+ 1 root audio 116, 2 2010-05-05  21:08 timer


i've also tried adding to alsa-base.conf this: 
options snd-hda-intel model=laptop enable=1 index=0

but didnt worked...
i've being reading about the alsa configuration but i can't find  anything arround that helps me, any ideas?

Thanks in advance

---

### Post by lidex on 2010-05-05
Can you post the output of these terminal commands for me please:
```
uname -a
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by morph_89 on 2010-05-06
Hi, thanks for taking interest on my post.

CODE:
> 
uname -r

2.6.32-22-generic

root@mateo-laptop:~# cat /proc/asound/version

Advanced Linux Sound Architecture Driver Version 1.0.21.

root@mateo-laptop:~# head -n 1 /proc/asound/card*/codec#*

Codec: Conexant CX20549 (Venice) 

my laptop is an hp dv pavillion 6265us

---

### Post by lidex on 2010-05-06
Make sure to remove any custom entries in alsa-base.conf first. Now update your kernel:
```
sudo apt-get update
sudo apt-get upgrade
```
Now reboot so we can work with the latest kernel.
Install alsa backports:
```
sudo apt-get install linux-backports-modules-alsa-lucid-generic
``` Reboot again.
Check your levels in alsamixer.
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

---

### Post by morph_89 on 2010-05-06
I did that but it didnt change anything. Is there a new config file i should look into? in between the alsamixer options my speakers are not displayed, so i cant change it from there.

---

### Post by lidex on 2010-05-06
We need to try some options in alsa-base.conf. Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=hp-dv6736  
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.

There are other options to try, but each has to be done on it's own, unless specified:
```
options snd-hda-intel model=laptop-hp
options snd-hda-intel model=laptop-hpsense 
options snd-hda-intel model=dell-m4-3 enable_msi=1
options snd-hda-intel model=model=hp-dv5 enable_msi=1
options snd-hda-intel model=dell-m4 enable_msi=1
```

Reboot after making changes and check alsamixer.

---

### Post by morph_89 on 2010-05-06
Thanks, I've tried every option separately but didn't had any luck; alsamixer stays the same after every reboot, i only have as playback options Master, PCM, S/PDIF S/PDIF (default) and the mics...


I've also try removing the following line;
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2

but didnt changed anything either... 


when i press F6 to select sound card my only options are default and HDA INTEL, they are both exactly the same...


any ideas?

---

### Post by lidex on 2010-05-06
> **morph_89 said:**
> Thanks, I've tried every option separately but didn't had any luck; alsamixer stays the same after every reboot, i only have as playback options Master, PCM, S/PDIF S/PDIF (default) and the mics...


I've also try removing the following line;
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
but didnt changed anything either... 
when i press F6 to select sound card my only options are default and HDA INTEL, they are both exactly the same...
any ideas?

That line should remain.
OK. Try this option:
```
options snd-hda-intel model=hp-dv5 enable_msi=0

```

Or (longshot):
```
options snd-hda-intel model=auto
options snd-hda-intel model=laptop-eapd
```

---

### Post by morph_89 on 2010-05-06
Just tried the three options, none of em worked :( alsamixer remains the same, this is my alsa-base.conf in case if its of any relevance:

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
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
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
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
options snd-hda-intel model=laptop-eapd

---

### Post by lidex on 2010-05-07
Try gnome-alsamixer. Go to 'Edit>Soundcard Properties' and play around with that. On the soundcard tab also. You're looking for something along the lines of jack sense. Also see this page:
[https://www.redhat.com/archives/fedora-list/2005-January/msg05487.html]("https://www.redhat.com/archives/fedora-list/2005-January/msg05487.html")

---

### Post by morph_89 on 2010-05-10
Thanks lidex for your help. Being trying for a couple of hours different options but none let to the solution. I finally got tired and reinstalled oss v4 drivers with pulseaudio, configured the media keys to control the oss volume and pulseaudio to load the oss modules. There might be a solution for making the alsa drivers work, but i don't think its going to be worth the trouble, for me, since audio works with oss just fine. 

Thanks again for your time

---

