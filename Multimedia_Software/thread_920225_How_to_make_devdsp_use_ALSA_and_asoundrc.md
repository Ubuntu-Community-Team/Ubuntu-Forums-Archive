---
title: "How to make /dev/dsp use ALSA and asoundrc?"
date: 2008-09-15
forum: Multimedia Software
---

### Post by BillZwicky on 2008-09-15
OSS apps appear to bypass asoundrc, and on my CA0106 card this results in a much higher volume.  asoundrc fixes the volume for ALSA apps, but OSS apps don't use it.  Even stranger, "options snd-pcm-oss nonblock_open=1" also doesn't work.

The "aoss" helper app works; for example "aoss firefox" will make Flash use ALSA.  But in some cases (like Gnome startup and shutdown) there's no way to sneak the aoss prefix in.  I'd also like sound to "just work" so that I don't need to edit all the shortcuts and insert "aoss".

I've added pcm.dsp and pcm.dsp0 entries to asoundrc, but they have no effect.

How do I make /dev/dsp go through ALSA?

---

### Post by eye208 on 2008-09-15
> **BillZwicky said:**
> The "aoss" helper app works; for example "aoss firefox" will make Flash use ALSA.  But in some cases (like Gnome startup and shutdown) there's no way to sneak the aoss prefix in.  I'd also like sound to "just work" so that I don't need to edit all the shortcuts and insert "aoss".
None of the apps you mention uses OSS. Flash uses ALSA (routed through PulseAudio). Gnome uses PulseAudio. There are hardly any OSS apps left.

---

### Post by BillZwicky on 2008-09-15
Ok, lets keep it simple.  The command "mpg123 -o oss" definitely uses OSS, and definitely bypasses asoundrc.  Note that it's not just bypassing pcm.dsp, it's bypassing the *default* config in asoundrc.

How do I get this command to use asoundrc?

---

### Post by eye208 on 2008-09-15
> **BillZwicky said:**
> Ok, lets keep it simple.  The command "mpg123 -o oss" definitely uses OSS, and definitely bypasses asoundrc.  Note that it's not just bypassing pcm.dsp, it's bypassing the *default* config in asoundrc.

How do I get this command to use asoundrc?
mpg123 -o alsa

Use the -a parameter to specify a particular ALSA PCM device defined in .asoundrc, e.g. "mpg123 -o alsa -a dsp" for pcm.dsp.

---

### Post by markbuntu on 2008-09-15
If you have

libasound2

and

libasound2-plugins

Then all your oss apps should play through alsa if you have System/Preferences/Sound set to alsa instead of autodetect. You can read my guide to get a better understanding of how this all works:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

