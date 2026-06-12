---
title: "Sound is working but max volume is really weak."
date: 2006-06-17
forum: Multimedia &amp; Video
---

### Post by morticul on 2006-06-17
My sound card is working but at maximum volume the sound is very weak. In alsamixer, I have two controls : Master and PCM. They both are at 100%. Using all the mixers I could, I didn't find any other control. 

I'm using a laptop so plugging an amplifier is not a solution. However, on Windows XP, the sound is about 10 times louder. I guess that alsa is using some kind of generic driver and is not able to control the card properly.  

Personnaly, I think that not being able to pump up the volume during a very good song, is worst than not having sound ](*,) 

my laptop is a HP dv8230ca (ca = canada, dv8230us is the same). Here is the output of aadebug

```

alex@ubuntu:~$ ./aadebug
ALSA Audio Debug v0.1.0 - Sat Jun 17 12:53:07 EDT 2006
http://alsa.opensrc.org/index.php?page=aadebug
http://www.gnu.org/licenses/gpl.txt

Kernel ----------------------------------------------------
Linux ubuntu 2.6.15-25-686 #1 SMP PREEMPT Wed Jun 14 11:34:19 UTC 2006 i686 GNU/Linux

Loaded Modules --------------------------------------------
snd_hda_intel          20468  6
snd_hda_codec         151056  1 snd_hda_intel
snd_pcm_oss            56448  0
snd_mixer_oss          20544  2 snd_pcm_oss
snd_pcm                96708  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              26884  2 snd_pcm
snd                    60004  14 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
snd_page_alloc         11304  2 snd_hda_intel,snd_pcm

Modprobe Conf ---------------------------------------------
Warning: module config file does not exist
This means any kernel modules will not be auto loaded
See your linux distro docs on how to create this file

Proc Asound -----------------------------------------------
Advanced Linux Sound Architecture Driver Version 1.0.10rc3 (Mon Nov 07 13:30:21 2005 UTC).
0 [Intel          ]: HDA-Intel - HDA Intel
                     HDA Intel at 0xd2400000 irq 66
 16: [0- 0]: digital audio playback
 24: [0- 0]: digital audio capture
  0: [0- 0]: ctl
 33:       : timer
cat: /proc/asound/hwdep: No such file or directory
00-00: HDA Generic : HDA Generic : playback 1 : capture 1
cat: /proc/asound/seq/clients: No such file or directory

Dev Snd ---------------------------------------------------
controlC0  pcmC0D0c  pcmC0D0p  timer

CPU -------------------------------------------------------
model name      : Genuine Intel(R) CPU           T2300  @ 1.66GHz
cpu MHz         : 1662.536
model name      : Genuine Intel(R) CPU           T2300  @ 1.66GHz
cpu MHz         : 1662.536

RAM -------------------------------------------------------
MemTotal:      1033204 kB
SwapTotal:     1951888 kB

Hardware --------------------------------------------------
0000:00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 03)


```


Please help me !

---

### Post by brk3 on 2006-08-16
Exact same probelem, is killing me. Why why, I really hope this gets fixed soon :confused:

---

### Post by sredman on 2006-08-21
I had the same problem after getting all of the Various media codec installed.  Through some fiddling i found that the XINE movie player volume was all the way down.  I set it in the middle, and now there is volume.  Only issue now is that the master volume in Ubuntu does not control the volume. :(

---

### Post by naaman on 2007-01-05
Hey guys,

After an exhaustive search, I believe I have greatly improved the volume and sound quality of my HP Pavillion dv5129TX by installing the latest alsa-drivers (alsa-driver-1.0.14rc1) along with alsa-lib and alsa-utils.

I have re-written [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) to guide n00bs and l33t h4x0r5 alike on how I got it to work under the "Update to the latest version of alsa" section.

The definitive sign that the snd-hda-intel module was properly identifying my card was the change of how ALSA identified my codec:

BEFORE:
head -1 /proc/asound/card0/codec*
Codec: Generic 14f1 ID 5047

AFTER:
head -1 /proc/asound/card0/codec*
Codec: Conexant CXT5047

Thanks to Sébastien Wains - [www.wains.be](www.wains.be) - for his blogging of his solution.


Naaman.

---

### Post by morticul on 2007-01-06
> **naaman said:**
> Hey guys,

After an exhaustive search, I believe I have greatly improved the volume and sound quality of my HP Pavillion dv5129TX by installing the latest alsa-drivers (alsa-driver-1.0.14rc1) along with alsa-lib and alsa-utils.

Naaman.

Hey thanks for the reply :D 

I was expecting that the most recent drivers would help but I was too lazzy to compile them. Shame on me :???:

It was also way much simpler than I thought. To my surprise, it was a flawless configure, make, install and a simple reboot. 

now I also have :
head -1 /proc/asound/card0/codec*
Codec: Conexant CXT5047

The sound is now louder and I have one more channel in my alsa mixer. But I feal that it is not as loud as my WinXp partition (i.e.: The max volume doesn't hurt my ears). Unfortunately I can't make a real test, beacause each time I boot my WinXp, it crash at start up and I have no intention on reinstalling it [-( 

so thanks very much naaman and long live Ubuntu !

---

