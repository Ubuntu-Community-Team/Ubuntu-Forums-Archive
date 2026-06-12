---
title: "Help with a log entry"
date: 2009-02-02
forum: Mythbuntu
---

### Post by Caps18 on 2009-02-02
I looked in the mythfontend.log and found a few repeating problems.

> 2009-02-01 18:00:32.697 NVP: prebuffering pause
2009-02-01 18:00:32.698 VideoOutputXv Error: Child          F   was already marked as available.
[mpegvideo_xvmc @ 0xb731bce8]mb incr damaged
[mpegvideo_xvmc @ 0xb731bce8]ac-tex damaged at 26 62
[mpegvideo_xvmc @ 0xb731bce8]00 motion_type at 27 63
[mpegvideo_xvmc @ 0xb731bce8]ac-tex damaged at 8 64
[mpegvideo_xvmc @ 0xb731bce8]invalid mb type in P Frame at 30 65
[mpegvideo_xvmc @ 0xb731bce8]00 motion_type at 37 66
[mpegvideo_xvmc @ 0xb731bce8]mb incr damaged
2009-02-01 18:00:32.751 VideoOutputXv Error: Child          F   was already marked as available.
2009-02-01 18:00:32.755 VideoOutputXv Error: Child        D     was already marked as available.
2009-02-01 18:00:32.755 NVP: prebuffering pause


> [mpeg2video @ 0xb72eace8]mb incr damaged
[mpeg2video @ 0xb72eace8]ac-tex damaged at 1 65
[mpeg2video @ 0xb72eace8]00 motion_type at 5 66
[mpeg2video @ 0xb72eace8]00 motion_type at 5 67
[mpeg2video @ 0xb72eace8]00 motion_type at 24 59
[mpeg2video @ 0xb72eace8]00 motion_type at 23 60
[mpeg2video @ 0xb72eace8]ac-tex damaged at 4 61
[mpeg2video @ 0xb72eace8]ac-tex damaged at 17 62


> 2009-02-01 20:11:09.589 NVP: prebuffering pause
2009-02-01 20:11:09.644 NVP: prebuffering pause
2009-02-01 20:11:09.672 NVP: prebuffering pause
2009-02-01 20:11:09.695 NVP: prebuffering pause
2009-02-01 20:11:09.721 NVP: prebuffering pause
2009-02-01 20:11:09.752 NVP: prebuffering pause
2009-02-01 20:11:09.846 NVP: prebuffering pause
2009-02-01 20:11:09.921 NVP: prebuffering pause
2009-02-01 20:11:09.947 NVP: prebuffering pause
2009-02-01 20:11:09.987 NVP: prebuffering pause
2009-02-01 20:11:10.022 NVP: prebuffering pause
2009-02-01 20:11:10.052 NVP: prebuffering pause
2009-02-01 20:11:10.253 NVP: prebuffering pause
2009-02-01 20:11:10.314 NVP: prebuffering pause

This NVP: prebuffering pause line is being written to the log every few thousandths of a second, so something must be wrong.  Can you give me some idea of what it might be?

Thanks

The only thing I can think of was that I was recording two shows and watching another one at the time.  But I think it was doing it even outside of the time I was recording/watching anything.  I checked and these are showing up when nothing is being done with the computer.

---

### Post by liquidhot on 2009-02-02
> **Caps18 said:**
> This NVP: prebuffering pause line is being written to the log every few thousandths of a second, so something must be wrong.  Can you give me some idea of what it might be?

[Fix for Pre-buffering Pause](http://letmegooglethatforyou.com/?q=prebuffering+pause)

---

