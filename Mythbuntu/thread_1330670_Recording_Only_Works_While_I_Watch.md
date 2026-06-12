---
title: "Recording Only Works While I Watch"
date: 2009-11-18
forum: Mythbuntu
---

### Post by jMon54 on 2009-11-18
For the past few days, I have been dealing with a most puzzling issue.  My recorded programs start out with a very pixelated picture, the kind I get when reception is poor, and after a few minutes of unwatchable video the recording stops entirely.

The puzzle is that if I watch while the program is being recorded, it records fine.  It is only when I am not present and it is doing its own thing that the problem is there.

The logs are showing many instances like this:

2009-11-18 15:11:08.138 [mpeg2video @ 0x7f43ca35e820]00 motion_type at 1 39
2009-11-18 15:11:08.162 [mpeg2video @ 0x7f43ca35e820]slice mismatch
2009-11-18 15:11:08.179 [mpeg2video @ 0x7f43ca35e820]mb incr damaged

2009-11-18 15:05:02.809 NVP(0): prebuffering pause
2009-11-18 15:05:02.810 [mpegvideo_vdpau @ 0x7fee23ba3820]Missing picture start code
2009-11-18 15:05:02.930 GetNextFreeFrame() served a busy frame B. Dropping. AUUUUUUUUUUUUUuUL

I tried turning off recording previewing and I changed from VDPAU High to VDPAU normal in my playback settings. And I ran database repair and optimization utilities.

Any help would be appreciated.

---

### Post by renkinjutsu on 2009-11-18
i don't use myth, but for me, vdpau (mplayer) only works when X is running, and it doesn't handle well with switching back and forth between framebuffer and X or framebuffer to framebuffer

---

### Post by jMon54 on 2009-11-18
> **renkinjutsu said:**
> i don't use myth, but for me, vdpau (mplayer) only works when X is running, and it doesn't handle well with switching back and forth between framebuffer and X or framebuffer to framebuffer

Wow!  That is very useful info for me.  You see, I just recently got Mythwelcome running on my computer to wake it up for recordings and turn it off when done.  It does so without going into the frontend.  Does that mean it is not starting X?  I wonder...?  I will have to see what happens by testing recording without Mythwelcome involved.

Thanks for sharing your knowledge.

---

### Post by renkinjutsu on 2009-11-19
I don't know much about vdpau, but i've used it to watch videos with mplayer, and i'm assuming it behaves the same way.

Please report back with your results!

---

