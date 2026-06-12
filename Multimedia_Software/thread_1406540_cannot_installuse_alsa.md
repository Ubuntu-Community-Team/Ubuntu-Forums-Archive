---
title: "cannot install/use alsa"
date: 2010-02-14
forum: Multimedia Software
---

### Post by pickarooney on 2010-02-14
Having had many problems with pulseaudio on a fresh karmic install, I followed some recommended instructions for removing pulse and using alsa ([http://ubuntuforums.org/showpost.php?p=8630967&postcount=20](http://ubuntuforums.org/showpost.php?p=8630967&postcount=20)). unfortunately, both pulse and alsa have gone and i'm left with oss which seems to work fine. I'd like to have alsa back though.

When I open amarok, it plays the frst song on the playlist then pops up a series of 'could not initialise sound engine' messages, and crashes.

---

### Post by mikewhatever on 2010-02-14
So what's the problem with reinstalling alsa? Can you post the output of the following command:

sudo apt-get install linux-sound-base alsa-base alsa-utils

---

### Post by pickarooney on 2010-02-14
apt-get tells me everything is installed, but I can't use alsa in smplayer or amarok

---

### Post by mikewhatever on 2010-02-14
I've never used neither of the players, but here is another point worth noting, I don't think Xubuntu had pulseaudio installed in the first place.

---

### Post by VertexPusher on 2010-02-14
> **pickarooney said:**
> Having had many problems with pulseaudio on a fresh karmic install
mikewhatever is right: There is no PulseAudio in a fresh Xubuntu install.

---

### Post by pickarooney on 2010-02-14
OK, noted. So today I formatted my hard drive and installed Jaunty. 
I'm still having the two exact same problems - can't use ALSA in smplayer and amarok can't play more than one track before failing to find an audio driver and crashing.

---

