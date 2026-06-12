---
title: "[SOLVED] Update to 0.21 XvMC mythvideo watch recordings problem"
date: 2008-03-18
forum: Mythbuntu
---

### Post by tr1plej on 2008-03-18
First things first, This is not the "mythvideo don't auto update because they merged it with mythdvd" problem.  I figured that out and fixed it right away.

So after I let mythbuntu update to 0.21 and I used synaptic to update mythvideo, I am unable to play some of my HDTV recording.  When I go to play some, but not all, of my HDTV recordings I just get a black screen.  If I press Esc I can exit, but if I press anything else I can no longer exit and I have to restart the computer.  If I set it not to use XvMC they play but the video and audio are jerky.  Also the recordings play fine in Xine, VLC, and Mplayer.

Edit: So I figured out that the HDTV recordings I can player are 720p; the ones I can't play are 1080i.  I can watch the 1080 LiveTV channels just fine, but not the recordings.


P.S. If I can't fix it: Is there an easy way to downgrade back to 0.20, or can someone point me to a website that has the old .deb files

---

### Post by superm1 on 2008-03-18
You need to go and change your deinterlacer to one that your system can handle.

---

### Post by tr1plej on 2008-03-18
Ok, so I had it set on the CPU+ Playback profile when I was having these problems.  It looked like it should work.  For sh!ts and giggles I decided to make a new profile and set it to  use XvMC for everything and wa-la!  It now works.

---

