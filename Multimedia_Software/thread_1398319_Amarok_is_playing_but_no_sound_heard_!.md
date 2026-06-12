---
title: "Amarok is playing but no sound heard !"
date: 2010-02-04
forum: Multimedia Software
---

### Post by bdsatish on 2010-02-04
I'm running Kubuntu 8.04.3 Hardy. All was working fine till yesterday. My SMPS (power supply) had some issue. So I replaced it and re-started Ubuntu in recovery mode. Just to be sure all is fine, I hit "Fix the X server". Then "Resume normal boot". Now the audio is gone :(  Amarok (or Kaffiene, VLC or mpg123) can open an MP3 file. The slider is moving, the song is playing but nothing heard. Firefox or any browser is not accessing my soundcard. The audio button on speakers is not muted.
 
Of course, I tried all that is listed in the "Comprehensive Sound Problem Solutions Guide" in the Forum Sticky, but could not get it to work.

Here's some commands and their output
```
bdsatish@mathmachine:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
Do I have two soundcards or is it only one repeated twice ?
I opened alsamixer, but all sliders are at their maximums. No one is muted.

```
bdsatish@mathmachine:~$ sudo lsof | grep /dev/snd/
kmix       9631   bdsatish   10u      CHR      116,0                11682 /dev/snd/controlC0

```

Yes, only Kmix is open. 
```
bdsatish@mathmachine:~$ ps ax|grep arts
 9607 ?        S      0:12 /usr/bin/artsd -F 10 -S 4096 -s 306 -m artsmessage -c drkonqi -l 3 -f
10285 pts/1    R+     0:00 grep arts

```

Here's the list of soundcards I have
```
bdsatish@mathmachine:~$ asoundconf list
Names of available sound cards:
I82801DBICH4

```

I also checked that I'm in the audio group

```
bdsatish@mathmachine:~$ grep 'audio' /etc/group
audio:x:29:bdsatish,guest

```

I even tried this, as a last resort

```
sudo modprobe snd-intel8x0
```

Still no audio. I restarted my PC. No effect. I then edited  /etc/modprobe.d/alsa-base and added the following lines:

```

options snd-intel8x0 index=0
options snd-intel8x0 ac97_quirk=3

```

This did not help either. What can go wrong ?!!

Here is my ALSA information:

[http://www.alsa-project.org/db/?f=bc6a45aa53e1b009a8f423de171d7d0d96d25f00]("http://www.alsa-project.org/db/?f=bc6a45aa53e1b009a8f423de171d7d0d96d25f00")

obtained by executing

```
wget -O alsa-info.sh http://alsa-project.org/alsa-info.sh && bash ./alsa-info.sh

```

Please help !!

---

