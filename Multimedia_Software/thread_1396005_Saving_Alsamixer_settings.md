---
title: "Saving Alsamixer settings"
date: 2010-02-01
forum: Multimedia Software
---

### Post by futureismo on 2010-02-01
Apologies if this has been covered elsewhere, I've done a search and couldn't find a solution.
I'm on Ubuntu 9.10 with 5.1 speakers and when I run alsamixer after the computer has booted my PCM is usually at a very high level, which causes poor sound quality and noise. I adjust the settings and exit and my problem is that I cannot save these settings. I have tried running
```
sudo alsactl store
```and
```
sudo alsactl store 0
```and neither of these work, the settings are always reset on rebooting. I have only a basic understanding of audio on Linux so does anyone have any suggestions to solve this? Or any other alternatives. Thanks.

---

### Post by VertexPusher on 2010-02-02
PulseAudio resets ALSA volume levels every time it is launched. Actually you are quite lucky; I've seen cases where it consistently muted the master output channel on startup.

You can remove PulseAudio by entering the following commands in a terminal window:
```
sudo apt-get install gstreamer0.10-alsa gnome-alsamixer
sudo apt-get purge pulseaudio gstreamer0.10-pulseaudio vlc-plugin-pulse
```

---

### Post by futureismo on 2010-02-02
Surely that would cause me even greater sound problems in programs such as Skype? Is there no other solution, I find it difficult to understand the Linux sound server situation but are ALSA and Pulseaudio essentially conflicting? If removing pulseaudio is the only feasible solution I guess I'll have to do so but I thought I might bump this to see if there are any other ideas.

---

### Post by futureismo on 2010-02-08
For anyone interested, I found a solution to this problem.

I wrote a script using the amixer command 
```
amixer sset PCM 55%
amixer sset Center 100%
amixer sset Surround 100%
amixer sset Front 100%
```
Which changes all the settings which are not by default what I want.
I saved this as amixersettings.sh in /home/louis/bin and then ran chmod to make it executable. ```
chmod +x amixersettings.sh
``` 
I then went to system, preferences, startup applications and added a new application entitled amixersettings which runs this command on start up. ```
bash amixersettings.sh
``` Only a workaround but I thought I may as well post in case it helps anyone. I'll mark the thread as closed.

---

