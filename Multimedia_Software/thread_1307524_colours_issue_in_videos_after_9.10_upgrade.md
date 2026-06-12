---
title: "colours issue in videos after 9.10 upgrade"
date: 2009-10-31
forum: Multimedia Software
---

### Post by Irishpolyglot on 2009-10-31
Hi everyone! I've upgraded to 9.10 and I'm glad to report that (unlike the 9.04 upgrade), I only have minor issues and this is one of them.
Any video I open up has almost every single colour in it as just wrong - it's almost like a negative image, but white is still white. The image is still crisp and all videos open fine. This happens in both Movie Player and VLC.
I'm on a Dell XPS M1730, with Nvidia drivers version 185.
I'm sure it's something simple - thanks for any advice!

---

### Post by The_Major on 2009-10-31
Same problem on a HP laptop. Must be an overlay problem

---

### Post by The_Major on 2009-10-31
Fixed, for some reason the HUE correction in the players was full off, just drag the slider to the middle and hey presto! (You access the settings in prefrences / display)

Mark

---

### Post by Irishpolyglot on 2009-10-31
OK, so your suggestion solves the problem... but only until I close the video program. Then it's back to as it was before.
I actually have a different interface than the normal one, called the "Nvidia X Server settings" that I get redirected to instead of the default, but it has the same settings.
The issue is with the Hue, that's for certain - but it's already in the middle when I open up the settings. Moving it anywhere and moving it back to 0 solves the problem! (EDIT: actually simply opening the Video settings solves the colours issue). The video has the right colours once more.
But then once I close the video player and open it up again the problem is back! It seems the setting for 0 Hue is off by default and can't stay there when I tell it to.
I'd love to find a solution other than constantly opening up the video settings every time I want to watch a video...
This issue is only for video files. Youtube videos are rendering correctly.

---

### Post by The_Major on 2009-10-31
its the settings in movie player I changed and it fixed it I have played several videos with no problems, I didnt need to alter my nvidia settings at all.

---

### Post by Irishpolyglot on 2009-10-31
That's done it! The hue was all the way on the left and bringing it to the middle has permanently fixed the problem. It's weird because I was having this issue on both Movie Player and VLC, but in making the alteration in just Movie Player's settings, VLC is working too.
Anyway thanks for the hint!

---

