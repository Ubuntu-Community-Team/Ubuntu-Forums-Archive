---
title: "Good Processor for 1080p Videos (boxee)"
date: 2009-06-11
forum: Multimedia Software
---

### Post by Darkdelusions on 2009-06-11
I am currently trying to put an HTPC together using boxee and running into a few snags when it comes to 1080p video. When I play 1080p video under boxee it seem to be maxing out my processor cause the video to be jitter or cause the audio to be outta sync. 

Since linux does not support gpu decoding of video I am left replacing the processor. My Current spec are below and would like a recommendation on a new processor to help me get to  1080p content to play correctly. The 2 giger that is in there now is what I had laying around the house and works great for standard def stuff but i would like to take to the next level.

Right now I am pushing audio and video threw the HDMI port on the board.

Board: M3N78-VM with GF8200
Processor: 2 gig Athlon single core processor
Ram: 4 gig of Cosair XMMS 
HD: 2 500 gig sata drives

---

### Post by mark_vinton on 2009-08-03
Linux does support VDPAU(GPU offloading) and I run a boxee system w/ a 2.4 ghz P4.  I purchased an nvidia 8400gs PCI card for around 45 bucks and it works great.  utilizes around 10-15 percent of my processor.  Might want to look into it.  Basically, anything utilizing mplayer can utilize VDPAU w/ the proper nvidia drivers.

---

### Post by binbash on 2009-08-03
Nvidia drivers do support VDPAU

---

