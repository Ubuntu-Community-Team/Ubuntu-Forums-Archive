---
title: "No Audio"
date: 2006-12-15
forum: Multimedia &amp; Video
---

### Post by CA405 on 2006-12-15
I am running Ubuntu 6.10 Edgy and I cannot get any audio out of my speakers no matter what device I try using.  I have an Intel 82801DB-ICH4 soundcard on my Sony Vaio.

---

### Post by kaan on 2007-02-18
I too have a similar problem. I am using Edgy 6.10 and have the EMPIA EMP202 chip onboard my Intel 845 Series mainboard. I get no sound, and I can see at boot up:

```
$ cat /var/log/dmesg | grep 17179587.896000
[17179587.896000] AC'97 0 access is not valid [0xffffffff], removing mixer.
[17179587.896000] Unable to initialize codec #0
[17179587.896000] ACPI: PCI interrupt for device 0000:00:1f.5 disabled
[17179587.896000] Intel ICH: probe of 0000:00:1f.5 failed with error -5

```

Here is some more information:

```
$lsmod | grep -i snd 
snd_intel8x0           34844  0 
snd_ac97_codec         97696  1 snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
snd                    58372  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm

```

---

### Post by kaan on 2007-02-19
I was able to fix my problem by loading the oss driver i810_audio instead of the alsa intel8x0. To try it out all you have to do is "modprobe i810_audio". If there are no errors in dmesg then log out and log in again and you should have sound. To make it permanent you need to remove(or comment out) "blacklist i810_audio" from /etc/modprobe.d/blacklist-oss and add "blacklist intel8x0" to /etc/modprobe.d/blacklist.

However there are still a few problems: 

- Every time a media file opens I get  beep. 
- There is no sound in flash in firefox.
- I can't run two applications that use sound at the same time.
- There are no system sounds (which seems normal, since they use esd).

My newer question would be then is there a way to use an oss driver as though it were an alsa driver? I know the reverse is possible.

---

### Post by tinx on 2007-02-19
I recently installed ubuntu. The problem is that when I plug in the external speakers there is no sound. The sound card is Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04). I already turned off the IEC input but with no result. It seems that the system was not able to detect the sound card. I tryed

lspci -v

in the root menu and it showed: Unknown device 1173.


The same problem occurs with video: no sound when external speakers are plugged in. Can you help? Thank's.

---

### Post by xavivars on 2007-03-04
I have exactly the same problem as you.

I can't hear anything when headphones are plugged in, but sound works well if they're not in.

---

