---
title: "Poor sound quality // Ubuntu 9.10"
date: 2009-10-24
forum: Multimedia Software
---

### Post by petehinds on 2009-10-24
Hi,

The sound card in my computer is detected by Ubuntu and does play sound however the sound quality is very poor and dominated by a hissing sound. The sound card works fine in Windows as do the speakers. 

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: M66 [M Audio Delta 66], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Card 1 is the card which is being used. Delta 66 is disabled in 'Sound Preferences'.

sudo lspci -v

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
    Subsystem: Intel Corporation Device 0013
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at 88300000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [130] Root Complex Link <?>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

I've tried tweaking the settings in 'alsamixer' without any joy.


Any suggestions would be great.

Thanks!

---

### Post by RichardLinx on 2009-10-24
Hi, see this post: [http://ubuntuforums.org/showpost.php?p=8139087&postcount=2](http://ubuntuforums.org/showpost.php?p=8139087&postcount=2)
I'd also like to take the time to point out that this forum has a search feature in the top right hand corner of this site, don't be afraid to use it. :)

---

### Post by AutoStatic on 2009-10-24
This sounds like a badly initialized soundcard and not a PulseAudio issue. Petehinds, could you post the outcome of **cat /proc/asound/card#*/codec#* | grep -i codec** ?
I have a notebook with a STAC92xx sound device too (HP DV-7-1070) and I still need an extra line in /etc/modprobe.d/alsa-base.conf otherwise IO have crappy sound.

---

### Post by petehinds on 2009-10-25
AutoStatic: Thanks, information below. 

/proc/asound/card0

cat codec#2 | grep -i codec

Codec: SigmaTel STAC9221D A2

---

### Post by AutoStatic on 2009-10-26
Thanks! Sounds a bit like this issue: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/266927](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/266927)
Does that ressemble your issue?

---

### Post by trav2089 on 2010-04-12
Just a friendly suggestion...I am an EX-Windows Xp user...I miss certain things about windows but for now I noticed the sound quality was distorted after ubuntu installation. I have been using "VLC MEDIA PLAYER" FOR AUDIO AND SOME VIDEO...no problems yet so far. Download it and try it...after installation turn volume to 20-40% then click "tools" then go to "Effects and filters"...under  "Audio effects" and "Graphic Equalizer" Click "enable" change preset to which you think sounds better...I use Party Preset. play a bass song for test  at main menu click media then open and find an MP3 .

---

