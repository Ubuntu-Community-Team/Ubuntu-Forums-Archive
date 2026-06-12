---
title: "Linux Sound &amp; X11"
date: 2014-03-28
forum: Multimedia Software
---

### Post by Flaggmann on 2014-03-28
Does anyone have a link to a good tutorial site for linux audio that can explain how jack audio, pulse audio, alsa  all tie together?

 I have jack up and running with patches in and presumably jack patching has full control; yet when I patch an external audio oscillator tone output into the line in on the sound card it is still audible on the localhost's speakers.

 I have it set up so that jack audio streams to icecast, using darkice/snow to a pc in another room which is where I expect the sound to be heard since jack patching only has that icecast output enabled. The mics are muted and the line in is selected as capture device in alsamixer yet the localhost speakers output the tone and it also appears in the streamed output. This is not good if one wants to stream a live station and use a mic as well as a player.

Hence my reason for looking for a good explanation on the overall audio big picture.

Also a good tutorial on the updated X11 configs and changes since they have eliminated the xorg.conf use now.

Thanks

---

