---
title: "No audio outside of the frontend"
date: 2011-01-14
forum: Mythbuntu
---

### Post by reformy on 2011-01-14
Hi all
In the last few weeks, something changed in my mythbuntu machine (backend+frontend). Watching in the frontend is OK, but playing videos outside of it, using vlc or any other player, has no audio. In addition, vlc doesn't close normally, but rather waits a minute, then crashes.

I have no idea how to check this. Can someone point me to the basic things to check for this (audio codecs? volume control? i don't know where to look).

Thanks
Yair

---

### Post by iitywygms on 2011-01-15
go here and read up.
[http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)
I would not try the upgrade until you try the suggested fixes.
Specifically.
Before reporting "NO SOUND" problems - check if your alsamixer-channels are activated and unmuted (gnome-mixer/volume-control/preferences)!!
Very often there are headphone-jack, Toslink, SPDIF or microphone issues reported. Usually this has something to do with wrong alsamixer settings or more seldom with a wrong model-id assigned to your sound-driver in /etc/modprobe.d/alsa-base.conf .
If you're lacking certain controls in alsamixer or your driver is not even being loaded, you should check-out your model-id in attached HD-Audio-Models.txt.
I strongly recommend to try similar model-id's matching your codec to checkout if your faulty function gets working.
I'd guess 80% of the reported problems (group: other than alsamixer issues) over here are related to the model setting in alsa-base.

I searched for days and this finally fixed all sound issues for me.
I have no asound.conf or asoundrc and everything works as it should.

I had the same issue as you. I had to add my model to alsa-base.conf before it would work.

---

