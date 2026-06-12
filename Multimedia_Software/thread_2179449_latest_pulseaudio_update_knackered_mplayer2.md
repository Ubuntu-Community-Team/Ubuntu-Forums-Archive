---
title: "latest pulseaudio update knackered mplayer2"
date: 2013-10-08
forum: Multimedia Software
---

### Post by lvm on 2013-10-08
Latest pulseaudio update (1:1.1-0ubuntu15.4) increased mplayer's CPU usage to unacceptable levels - from 30-40% to 100% and dropping frames on the same video. Forcing mplayer to use alsa brings CPU usage back to normal but mplayer doesn't work with alsa directly very well... What should I do to roll back pulseaudio to the previous version - 15.3 I presume? 

12.04

---

### Post by kostkon on 2013-10-08
The update all it did was fixing [this problem]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1169143").

Maybe you could recheck the audio settings in mplayer and also make sure that it's actually using the pulseaudio backend.

You could also reset pulseaudio by deleting the ~/.pulse folder and then logging out.

---

