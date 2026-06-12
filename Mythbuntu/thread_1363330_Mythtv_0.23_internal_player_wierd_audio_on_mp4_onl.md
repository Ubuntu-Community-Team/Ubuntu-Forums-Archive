---
title: "Mythtv 0.23 internal player wierd audio on mp4 only"
date: 2009-12-24
forum: Mythbuntu
---

### Post by bergqvistjl on 2009-12-24
Hi guys, whenever i try and play an mp4 file (their all 720p HD by the way) using the internal player, the audio seems to play at a really slow speed (like the speed and pitch have been reduced by half), but when i play the file using mplayer, its fine. This wouldnt be a problem but as mythweb has switched to using storage groups for the videos, i cant play anything using mplayer now, unless i load the file manually. Any ideas/possible ways of solving it? Im running mythbuntu 9.10 x64 with the UK 0.23 autobuilds.

---

### Post by SiHa on 2009-12-24
Storage groups aren't compulsory (in 0.22 anyway, I imagine 0.23 is the same). You can either remove the location in the backend setup, or just add another directory that you want to use in the frontend setup, and put your mp4's in there so you can use mplayer.

---

### Post by bergqvistjl on 2009-12-24
well in the latest version of mythweb ive got, it explictly says that i need to use storage groups otherwise mythweb wont recognise the videos, which i want as its easier to edit metadata, particulary video plots.

---

### Post by munzli on 2010-01-12
been trying to solve the exact same problem... happens with apple's 720p quicktime trailers too and i'm not using storage groups

---

### Post by munzli on 2010-01-17
seems like we've got to live with this problem... the internal player has it's own version of ffmpeg which just doesn't like the aac stream in mp4s. use mplayer as alternate player (don't forget the "-ao alsa" option if video stays paused)

---

