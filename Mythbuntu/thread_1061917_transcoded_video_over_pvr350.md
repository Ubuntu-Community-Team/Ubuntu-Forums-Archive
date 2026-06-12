---
title: "transcoded video over pvr350 ?"
date: 2009-02-06
forum: Mythbuntu
---

### Post by Eric Boring on 2009-02-06
HI,

I'm using a Hauppauge pvr 350 for playback (and recording) on my combined front/backend. I want to transcode my recordings to save space. When I do this, they play fine on my remote frontends, but playback looks fuzzy and stutters on the pvr 350. Can I set the transcoder to a different bitrate or something to improve playback and save space?

Thanks,

Josh

---

### Post by Eric Boring on 2009-02-08
Bump. Anyone?

---

### Post by ian dobson on 2009-02-10
Hi,

From what I understand the PVR350 has a hardware MPEG-2 decoder and if you transcode a video, mythtv creates a nuv video file. So the PVR350 can't use the hardware decoder so it works like a normal "dumb" frame buffer. 

If you want to transcode make sure the output of the transcoder is mpeg2.

Maybe you can use the --mpeg2 command line option for mythtranscode.

Regards
Ian Dobson

---

