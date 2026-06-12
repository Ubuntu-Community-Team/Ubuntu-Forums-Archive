---
title: "VLC Full Screen problem with dual head display"
date: 2007-10-31
forum: Multimedia &amp; Video
---

### Post by Matt_E on 2007-10-31
I am using 7.1.  
My setup is a 3.0 P4, and a Geforce 6200 card.
I use dual head display via Twin View - one 19 inch Samsung @ 1280x1024, and one Sceptre Gamer X22WG @ 1680x1050

My problem is with the full screen mode of VLC.  It will bring the full screen video up on the Samsung, always.
I can't move it to the Sceptre monitor for some reason.
When I scroll between desktops/desks, the full screen video will briefly scroll across that screen, but it never stays.
When I move VLC over to the Sceptre (it plays in windowed mode just fine) and then enable full screen, the VLC window will stay on the Sceptre, but the full screen video is now on the Samsung.
Totem handles this just fine, but it's buggy with DVD playback, so I'd rather not use it.
So far my solution has been to use windowed mode on the Sceptre and making it as big as possible.

Any ideas?

---

### Post by Matt_E on 2007-10-31
I just thought of something obvious....the Samsung is my primary display, while the Sceptre is the secondary.
I'll switch that and see if it helps.

---

### Post by Michael_TSM on 2007-11-09
I have exactly the same problem,

But as my second monitor is a television I don't want to switch it to be my primary display.

Does anyone know of a solution to this?

EDIT: This problem also occurs when I try and use FCE Ultra (A Nintendo 8-bit emulator)

**SOLVED:** See Below

---

### Post by Michael_TSM on 2007-11-10
**SOLVED:**
Go to preferences
Then Video
Then Output modules
Then Xvideo
Click the Advanced Options button
Change the "Screen for Fullscreen Option" from "0" to "1"
Then press Save

Now VLC should fullscreen on the second monitor/TV

---

### Post by Ux64 on 2008-05-23
> **Michael_TSM said:**
> **SOLVED:**
Now VLC should fullscreen on the second monitor/TV

It's annoyting to change that several times / day. With Gutsy Gibbon autodetection was working. But when I upgraded to Hardy it stopped working. Now I need to flip that switch back and forth again. ;(

Because only Ubuntu changed, VLC is still the same. I think this is not VLC's fault, it's Ubuntu's fault that dual screen isn't working correctly.

---

