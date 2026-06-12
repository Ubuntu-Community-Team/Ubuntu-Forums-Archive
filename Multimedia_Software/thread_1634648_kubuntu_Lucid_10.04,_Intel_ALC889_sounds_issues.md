---
title: "kubuntu Lucid 10.04, Intel ALC889 sounds issues"
date: 2010-11-30
forum: Multimedia Software
---

### Post by sharkcohen on 2010-11-30
I have an Intel DX58SO motherboard with the ALC889 onboard sound, running kubuntu 10.04, and I am not getting analog sound.  Strangely, spdif is working great, but I need analog to work, too.  I've been in alsamixer, nothing is muted.  That's the extent of my troubleshooting knowledge for sound issues.  If anyone can help, that would be great.

```

sharkcohen@sharkdesk:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
sharkcohen@sharkdesk:~$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
sharkcohen@sharkdesk:~$ lsmod | grep snd
snd_hda_codec_realtek   279040  1 
snd_hda_intel          25773  17 
snd_hda_codec          85759  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
snd_mixer_oss          16299  1 snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    71187  46 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8052  1 snd
sharkcohen@sharkdesk:~$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.21.

```

---

### Post by sharkcohen on 2010-12-01
bump

---

### Post by lidex on 2010-12-02
Need a little more info please.
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by sharkcohen on 2010-12-02
Thanks lidex, here you go:


[http://www.alsa-project.org/db/?f=b5679ecacc7241d3d1a7cd024734d9a281133002](http://www.alsa-project.org/db/?f=b5679ecacc7241d3d1a7cd024734d9a281133002)

---

### Post by lidex on 2010-12-02
> **sharkcohen said:**
> Thanks lidex, here you go:


[http://www.alsa-project.org/db/?f=b5679ecacc7241d3d1a7cd024734d9a281133002](http://www.alsa-project.org/db/?f=b5679ecacc7241d3d1a7cd024734d9a281133002)

Try this. Edit your alsa-base.conf to change the model from 'auto' to 'intel-x58'
```
kdesudo kate /etc/modprobe.d/alsa-base.conf
```

---

### Post by sharkcohen on 2010-12-04
Tried it, but unfortunately it didn't help.

---

### Post by lidex on 2010-12-04
> **sharkcohen said:**
> Tried it, but unfortunately it didn't help.

You rebooted after?
What do you get for this:
```
cat /etc/modprobe.d/alsa-base.conf
```

---

### Post by sharkcohen on 2010-12-05
No, I didn't reboot, but I did reload alsa and restart X.  I can try rebooting.  I'll also post back with the contents of alsa-base.conf.

---

### Post by sharkcohen on 2010-12-05
I tried rebooting.  Before the X server starts, I get a buzzing sound out of my speakers that are plugged into one of the analog jacks, but after the X server starts, that goes away and I have no analog sound.  spdif is still working.

Here's my alsa-base.conf, the only line I added to it was the line for snd-hda-intel at the bottom, the rest has been there since the OS was installed.

```

sharkcohen@sharkdesk:~$ cat /etc/modprobe.d/alsa-base.conf
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
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin
/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
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

# let's try to get this sound working
options snd-hda-intel model=intel-x58

```

---

### Post by lidex on 2010-12-05
Now I would suggest updating your alsa install. You can follow the link in my sig.

---

### Post by sharkcohen on 2010-12-06
Will do, thanks lidex.

---

