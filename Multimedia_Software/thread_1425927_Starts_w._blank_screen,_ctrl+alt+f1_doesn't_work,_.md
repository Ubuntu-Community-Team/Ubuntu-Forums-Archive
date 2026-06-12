---
title: "Starts w. blank screen, ctrl+alt+f1 doesn't work, also, screen goes black now and the"
date: 2010-03-09
forum: Multimedia Software
---

### Post by ayrin83 on 2010-03-09
I have looked around a bit, and I haven't been able to find a solution for this (or even someone else who has posted identical problems).

Essentially, I have two problems, but they are both related to graphics.

I run Karmic with an ATI Technologies Inc RV350 AP [Radeon 9600]. I ran fglrx on the system previously, but it doesn't seem to be supported on the native version of xServer, so currently I'm running radeon.

**1. The graphics doesn't start at all at some start ups.**
I start the computer and the BIOS splash screen appears. Sometimes, it works fine and I can log on to ubuntu with no further problems. 

Usually, however the log on process seems to just stop. The screen shows "In power save mode, move mouse...", but the computer buzzes away happily. However, I can move the mouse as much as I like, nothing happens. Neither does it seem to register the keyboard, pressing ctrl-alt-f1 (or f2 ocr f3...) doesn't do anything.

Usually I just press the reboot-button on the computer and try again, after a few attempts it usually succeeds.

One fairly strange thing in this is that I sometimes only get to the BIOS splash, sometimes to the ubuntu splash (white ubuntu symbol on black background) and sometimes the GRUB-menu shows up (but not at other times). 

**2. The screen goes black for about 2 seconds at times**
At times, usually when I'm moving stuff around or otherwise make the graphics card work a little, the screen goes black for about 2 seconds, then returns. This can be as often as ~once/minute at times. I had this problem when I ran fglrx too, but it didn't happen anywhere near as often.

After changing the resolution from 1600x1200 to 1280x1024, the problem is gone, but I'd prefer being able to run the screen on the higher resolution.

I presume I didn't provide all the necessary information, so please specify what you need to know. Right now, I'm considering downgrading the xserver to a version which supports fglrx for my card, but any suggestions are welcome :).

---

