---
title: "Stupid Kino Question"
date: 2011-01-31
forum: Multimedia Software
---

### Post by rsgrimes on 2011-01-31
Hi,

I have a 4.1 GByte raw video file from my Sony digicam.  Using Kino, I can export it to a 1.2 GByte MPEG file, but that's still way too big.  I could not find any options for making the file smaller (e.g. lower the resolution, set the bit rate, etc.)  

I've tried mencoder, but my wife couldn't play the result on her Windows machine.  Looked at ffmpeg, but that's way too complicated for me.

Seems like an obvious, common operation!  Am I missing something?  I don't want/need anything fancy - I just want it smaller.

Thanks!

---

### Post by BicyclerBoy on 2011-01-31
Handbrake
You can set the target file size..
It'll take some horsepower tho'.
Can get it fresh from the developer's ppa.

Guessing your videos are HD m2ts mpeg2-ts h264 stuff.

Leave them as H264 mpeg4/10 for best file size if the other PC can play them.
May need to use a less CPU intensive playback option tho.

Or Avidemux2

---

### Post by FakeOutdoorsman on 2011-02-01
> **rsgrimes said:**
> I don't want/need anything fancy - I just want it smaller.

Smaller as in file size, resolution, or both? Is there are particular output format that you require?

[Handbrake installation instructions](http://ubuntuforums.org/showpost.php?p=10415050&postcount=6).

---

### Post by rsgrimes on 2011-02-04
Thanks for the replies - I'm trying it out now.

For reference, I want a smaller file size; I can't email gigabyte files!  To that end, I would accept a smaller video size to get that.

FWIW - I also realized I should have said "Kino Stupid Question" - I wasn't applying stupid to Kino!

Thanks,
-Bob

---

