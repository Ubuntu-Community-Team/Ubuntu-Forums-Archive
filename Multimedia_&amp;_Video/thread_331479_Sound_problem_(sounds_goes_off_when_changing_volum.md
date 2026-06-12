---
title: "Sound problem (sounds goes off when changing volume)"
date: 2007-01-04
forum: Multimedia &amp; Video
---

### Post by Kjellstroem on 2007-01-04
I have a weird sound problem.

My sound card is the same hda-intel ICH7 (rev2) sound card as is the topic of another post:
[http://www.ubuntuforums.org/showthread.php?t=305712](http://www.ubuntuforums.org/showthread.php?t=305712)

My problem is weird though. Sound works somewhat (right speaker works, left speaker has only a high-pitched sound). If I try to change ANY sound settings the sound is immediately turned off. Things like adjusting the v olume even the slightest in any of the music players and the sound gets turned off.

I can restart the sound by using "sudo alsaconf", but that's about it. How can I get the sound to always work and how can I get rid of the high-pitched sound in the left speaker?

I'm new to Ubuntu so I don't know exactly what info to post but here's some:

"sudo alsaconf" shows the correct driver.

"sudo /etc/init.d/alsasound reload" gives me:
```
Shutting down sound driver: ERROR: Module snd_hda_intel is in use
ERROR: Module snd_hda_codec is in use by snd_hda_intel
ERROR: Module snd_mixer_oss is in use
ERROR: Module snd_pcm is in use by snd_hda_intel,snd_hda_codec
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd is in use by snd_hda_intel,snd_hda_codec,snd_mixer_oss,snd_pcm,snd_timer
done
ALSA driver is already running.
```

lspci:  Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

cat /proc/asound/version says: Advanced Linux Sound Architecture Driver Version 1.0.14rc1.
"alsamixer -h": AlsaMixer v1.0.13
alsa configurator: v1.0.13

---

