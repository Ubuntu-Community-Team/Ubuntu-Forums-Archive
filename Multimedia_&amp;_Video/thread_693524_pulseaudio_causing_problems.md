---
title: "pulseaudio causing problems"
date: 2008-02-11
forum: Multimedia &amp; Video
---

### Post by anathema415 on 2008-02-11
Hi Guys,

I'm having a problem with sound on my machine. I installed Second Life today and it had no sound. In order to get that working I had to install ESD and PulseAudio. Now the sound in Second Life works fine. The system sounds work fine. However I can't get any sound to work in video files (.avi) with any player but the totem movie player. My preferred player is VLC. When I run VLC here's what I get. 

> VLC media player 0.8.6c Janus

** (.:6555): CRITICAL **: clearlooks_style_draw_focus: assertion `height >= -1' failed
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
[00000340] oss audio output error: cannot open audio device (/dev/dsp)
[00000340] main audio output error: couldn't find a filter for the conversion
[00000340] main audio output error: couldn't create audio output pipeline


I uninstalled Everything pulse and VLC sound works fine, but not secondlife. So i reinstalled pulse along with the gstreamer plugin and Jacks. Still no luck. How can I make both programs happy?

Thanks

---

### Post by anathema415 on 2008-02-11
No one?

---

### Post by Giannis68 on 2008-02-11
[http://wiki.debian.org/SoundFAQ](http://wiki.debian.org/SoundFAQ)
How to enable ALSA OSS emulation? A1: kernel mode emulation: 
 apt-get install alsa-oss
 modprobe snd_pcm_oss
 modprobe snd_mixer_oss

---

### Post by anathema415 on 2008-02-11
No luck...

---

### Post by Giannis68 on 2008-02-11
put your username in audiogroup
sudo gedit /etc/group
tape:x:26:
sudo:x:27:
[COLOR=Red]audio:x:29:[/COLOR][COLOR=Navy]yourusername[/COLOR],otherusername
save and logoff

---

### Post by anathema415 on 2008-02-11
It's already there

---

### Post by misty soul on 2008-02-12
Did you try to change the settings in VLC ?
for example Preferences/sound/output modules, which can be set to predefined, alsa, oss and more.
If you change it to ALSA and have configured Alsa/PulseAudio to work together (editing /etc/pulse/default.pa and /etc/asound.conf), then perhaps it would work better.

---

### Post by anathema415 on 2008-02-13
I gave up on the pulse audio and just installed ESD. Now I have no problems.

---

### Post by misty soul on 2008-02-18
Trying to solve your problem, I encountered the same one. My previous advice about alsa setting did not help either (the messages window still displayed errors about /dev/dsp that could not be open).

I finally succeded after having noticed some plugins were not installed by default. This one did the trick:
```
apt-get install vlc-plugin-esd
```

---

