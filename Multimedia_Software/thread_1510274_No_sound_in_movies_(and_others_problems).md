---
title: "No sound in movies (and others problems)"
date: 2010-06-15
forum: Multimedia Software
---

### Post by skit111 on 2010-06-15
Hello.
I have some problems with the sound in Ubuntu 10.04 64bit. I can't turn on sound in movie-players. I use ALSA. In the preferences of MPlayer, VLC and SMPlayer (and others players) in the audio section, there is set to ALSA, but there is no sound.
I can hear the music only in Audacious and others music-players.
Additionally, after each time the system restarts, I must type in the console:
```
sudo /etc/init.d/alsasound start
```
for turn on the sound.
Next issue: there is no sound in the internet browsers (I noticed that on Firefox, Opera, Chrome), I mean youtube, vimeo, etc. shows the video but without sound.

Can anyone help me?

P.S. Sorry about my English, but my mother language is Polish.

---

### Post by cchhrriiss121212 on 2010-06-15
Ubuntu uses pulse audio for everything by default, so did you try to remove pulse for some reason?
The system will start to use ALSA for everything by default if you remove pulse completely.

---

### Post by lovinglinux on 2010-06-28
Run the following commands:

```
rm -fr ~/.pulse ~/.asound*
sudo rm /etc/asound.conf
```

Reboot, then go to "System >> Preferences >> Sound" and configure sound again.

See if that helps.

---

