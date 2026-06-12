---
title: "Sound problems"
date: 2009-01-11
forum: Multimedia Software
---

### Post by miazma on 2009-01-11
Hello,

I've tried the following howto to disable pulseaudio: [alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/]("http://idyllictux.wordpress.com/2008/10/29/alsa-instead-of-pulseaudio-for-ubuntu-810-intrepid-a-non-destructive-way/"), but it didn't work (no sound), so now I tried to undo all the changes made, but

```

johannes@luna:~$ aplay -l
**** Liste von PLAYBACK Geräten ****
ALSA lib conf.c:3009:(snd_config_update_r) Cannot access file /usr/share/alsa/alsa.conf
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL hw:0
aplay: device_list:224: control open (0): No such file or directory

```

...

Well, I just reinstalled libasound2 (sudo apt-get install --reinstall libasound2) and now I'm getting sound ;-)

greetings,
Johannes

---

### Post by liptak15 on 2011-12-06
Thank you, it helped me a lot.

---

