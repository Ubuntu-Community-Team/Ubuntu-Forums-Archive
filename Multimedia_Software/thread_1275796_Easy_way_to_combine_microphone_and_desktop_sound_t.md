---
title: "Easy way to combine microphone and desktop sound through pulseaudio?"
date: 2009-09-26
forum: Multimedia Software
---

### Post by HighfireX on 2009-09-26
As the title states, I'm trying to record both the desktop sound and microphone sound at the same time when using gtk-recordmydesktop and pulseaudio. I've been using 'pulse' as the source of my audio. 

The quality of the audio is good, however I am usually forced to choose the stream for the recording (ie. If I want microphone sound, I would switch recording stream to hda nvidia. When I want desktop sound, I would switch the stream to monitor of hda nvidia)

I do not have a good time configuring JACK seeing as first I couldn't see the pulseaudio jack sink and source (turns out I had to put 'load module module-jack-sink #AND# module-jack-source on the /etc/pulse/default.pa file). Pulseaudio then would not work with JACK, stating something about stale pids and zombies. A test video sounded very fuzzy and cut off.

Anyone have any suggestions?

---

### Post by dfszb on 2011-01-11
Here you can find good description on how to do it: 
- [http://www.linux.com/learn/tutorials/367395:weekend-project-record-from-skype-calls-and-other-apps-on-linux](http://www.linux.com/learn/tutorials/367395:weekend-project-record-from-skype-calls-and-other-apps-on-linux)

check for the section that discusses /etc/pulse/default.pa setting, and then use parecord to record from the mywiretap.monitor source.

---

