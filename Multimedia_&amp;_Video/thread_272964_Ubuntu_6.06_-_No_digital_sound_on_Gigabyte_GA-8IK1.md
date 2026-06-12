---
title: "Ubuntu 6.06 - No digital sound on Gigabyte GA-8IK1100 motherboard"
date: 2006-10-07
forum: Multimedia &amp; Video
---

### Post by Giardap on 2006-10-07
Hi,
I have just installed Ubuntu 6.06 from the DVD in the Official Ubuntu Book, but am unable to get digital sound out.
System info- 2.8GHz Pentium IV Northgate, 80 GB Seagate ATA 100 hard drive,2 GB dual DDR RAM, on a Gigabyte GA-8IK1100 motherboard with integrated Realtek AC'97 audio. The relevant chipset govening audio is Intel 82801ER ICH5.

My SPDIF out is a RCA jack ( not TOSLINK) into Creative Cambridge Soundworks THX digital speakers 2.1. These work fine in Windows XP. 

Also I can get digital sound out with SUSE Linux 10.1 on this same box. I have tweaked Alsamixer ad nauseam. Also when I check the Alsamixer sound card grid, on the Alsamixer website, under Intel, I do not see this chipset listed (yet it works under SUSE Linux 10.1)
I have successfully installed Ubuntu on 2 other machines (one with digital sound) in the past - but this one has stumped me! ( and this is my 3rd attempt on this machine)

I like Ubuntu, but without sound it's a redundant OS from my perspective.

Any suggestions as to how I might get digital sound out please in Ubuntu 6.06?


Thanks.

---

### Post by Giardap on 2006-10-07
Some more info:
0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH 5R) AC'97 Audio Controller (rev 02)

xxxxxxx@sandra-ubuntu:~$ lsmod | grep snd
snd_intel8x0           33692  1
snd_ac97_codec         93216  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm

---

