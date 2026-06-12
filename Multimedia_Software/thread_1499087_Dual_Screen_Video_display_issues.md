---
title: "Dual Screen Video display issues"
date: 2010-06-01
forum: Multimedia Software
---

### Post by PurplePalex on 2010-06-01
Spec: Ei Systems 3090 uk laptop, just installed with Lucid Lynx, using VGA out to connect to (very old) Packard Bell SlimView S525.

Issue: while connecting and getting the screen to display as dual monitor is no issue what so ever, when attempting to view video files (.avi,.wmv etc.) there is no visual component displayed. There is audio, and the program resizes the window to fit the normal resolution of what it is playing, except it only displays a black screen. Have tried both VLC Media player and Movie Player (that shipped with the release). There is an odd one pixel high thing happening on the top line of the screen though, like the video is playing, just not in the right place.

Help?

---

### Post by redtela on 2010-06-12
I found this by googling for the same problem.

It's related to a long running gnome issue IIRC (I last saw it in 8.10). I've confirmed it still happens on my NC10. Basically, if the screen resolutions on your two monitors are different, you can't play movies. If you use a single monitor or the resolution is the same in both, it works fine.

Another workaround (untested by me) is apparently to use KDE - but I've never liked KDE personally.

I've not gone to the lengths of testing, but apparently it's only the vertical resolution that matters. My NC10 runs 1024x600 with the external on 1280x1024.

If anyone knows of a fix in Gnome, I'd appreciate a post too. :)

EDIT: OK, so I've done a little more playing, and I've fixed it, on my system (your results may vary). Here's how:
System > Preferences > Multimedia Systems Selector. Go to the Video tab. On there, my settings for "Default Output" are:
Plugin: X Window System (No Xv).
Device: Unsupported (default and only option, greyed out).
Pipeline: ximagesink (default option, greyed out).

Have a play with your settings & hit the test button. You'll know it works when the test window has visible output. I found that setting the options to Plugin=X Window System(X11/XShm/Xv), Device=Intel(R) Video Overlay and leaving the default Pipeline worked in the test window, but the colours were incorrect when playing back AVI. So if it works in test, open an avi file before you hit close. :)

---

### Post by PurplePalex on 2010-07-01
Thank for the help, You are indeed right about the same resolution work around.

Your fix though confuses me. Very n00b at Ubuntu. I had to faff for a little to find the multimedia selector etc (type gstreamer-properties in at the terminal works), the took the settings you suggested, but no dice. No video for the .avis at all.

Thanks anyway!

---

### Post by daedulus75 on 2010-07-16
> **redtela said:**
> I found this by googling for the same problem.
EDIT: OK, so I've done a little more playing, and I've fixed it, on my system (your results may vary). Here's how:
System > Preferences > Multimedia Systems Selector. Go to the Video tab. On there, my settings for "Default Output" are:
Plugin: X Window System (No Xv).
Device: Unsupported (default and only option, greyed out).
Pipeline: ximagesink (default option, greyed out).

Have a play with your settings & hit the test button. You'll know it works when the test window has visible output. I found that setting the options to Plugin=X Window System(X11/XShm/Xv), Device=Intel(R) Video Overlay and leaving the default Pipeline worked in the test window, but the colours were incorrect when playing back AVI. So if it works in test, open an avi file before you hit close. :)

Worked like a charm for me - thanks! I'm a total n00b and I kept retreating to Windows 7 to play video on my TV, rather than watching some terribly distorted image using UNR. No more of that!

---

### Post by redtela on 2010-08-14
Apologies for not seeing these posts sooner. I don't tend to check the account often.

It's a bit of a faff to continue using the workaround of changing monitor resolutions to watch .avi's, I admit, but short of playing with the settings, I'm not entirely sure what to suggest.

All I can tell you is that I installed v4l manually to try & work around the issue, but it didn't help much. Try: sudo apt-get install v4l-conf v4l2ucp dov4l

Once you've installed them, have a play around with those & gstreamer-properties to see what trial & error will bring. v4l-conf is a tool to configure video4linux, v3l2ucp is a "control panel" for it, and dov4l is an app to query/set settings for v4l.

Don't be afraid of "breaking" anything playing around, as the worst of problems here can be solved with "rm -rf ~/.gcon*" - resetting Gnome back to default config.

Good luck - and in the mean time, I've been meaning to shake the bug reports for this issue (autodetect clearly isn't working right out of the box).

---

### Post by PurplePalex on 2010-11-04
I ran the sudo etc and it seemed to work out no problems, but after that I'm confused. I thought the line would install new apps I could get at via the normal GUI, but I can't seem to find them. Did I get something wrong so it didn't work, or is opening that stuff up a little more complicated?

---

