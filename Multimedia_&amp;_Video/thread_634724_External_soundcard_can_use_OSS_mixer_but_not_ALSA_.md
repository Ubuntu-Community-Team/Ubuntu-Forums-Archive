---
title: "External soundcard can use OSS mixer but not ALSA mixer"
date: 2007-12-08
forum: Multimedia &amp; Video
---

### Post by ZOMGxuan on 2007-12-08
I am using a Creative Sound Blaster Digital Music SX, which is an external (USB) soundcard.
After much tinkering i was finally able to set it as the default sound card. How ever, even though it is working with ALSA, under the Default Mixer Tracks Device in Sound Preferences, the only things listed are HDA Intel (ALSA mixer) and USB Mixer (OSS Mixer). Obviously i would want to use the USB mixer, but why is it OSS and not ALSA? Furthermore i am only getting one track on it, PCM-2, as compared to the many tracks under HDA Intel.

[[IMG]http://img458.imageshack.us/img458/6421/screenshotsoundpreferenpx1.th.png[/IMG]](http://img458.imageshack.us/my.php?image=screenshotsoundpreferenpx1.png)

the following are the outputs when trying to run amixer and alsamixer.

```
tanzx@ubuntu-desktop:~$ amixer
amixer: Mixer default load error: Invalid argument
tanzx@ubuntu-desktop:~$ alsamixer

alsamixer: function snd_mixer_load failed: Invalid argument
tanzx@ubuntu-desktop:~$ alsamixer -c 0

alsamixer: function snd_mixer_load failed: Invalid argument
tanzx@ubuntu-desktop:~$ alsamixer -c 1

```

card 0 is the usb card, alsamixer works for card 1, which is HDA Intel.

I want to know whether this is a problem with the drivers or the card itself, since my card is not listed in the ALSA homepage. I want this card to work with ALSA mixer, so please any suggestions?

---

### Post by ZOMGxuan on 2007-12-13
can no one help me? Otherwise I shall just have to get another soundcard.

---

