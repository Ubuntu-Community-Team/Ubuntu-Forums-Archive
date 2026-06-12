---
title: "MythTV Color Calibration"
date: 2009-01-27
forum: Mythbuntu
---

### Post by Weidbrewer on 2009-01-27
Is there any sort of program (or even a video to play) that I can use to calibrate the color of the TV signal through my card?  I know how to adjust the colors, but it would nice if I had something to judge my adjustments against rather than, "Eh, good enough."

Thanks in advance for any help.

---

### Post by yonkiman on 2009-02-01
> **Weidbrewer said:**
> Is there any sort of program (or even a video to play) that I can use to calibrate the color of the TV signal through my card?

I've given some thought to the same issue.  For digital HDTV signals (received digitally, they are never analog in your system) you can assume that the digital data itself is correctly color balanced, so you could find (or create) a test image with color bars, grayscales, etc. that could help you align the image.  One of those "tune your TV" (Video Essentials, etc.) DVDs would work pretty well.

But for ANALOG TV signals that are received by a tuner and converted to digital inside your PC, things are different.  The analog tuner itself may introduce contrast, brightness, color, and tint errors (I know my PVR-150 does) before the signal is digitized, and there's wide variation from analog station to analog station (particularly on cable TV).  So in that case, a test pattern on your PC is not going to account for those sources, which are the main source of bad color in my system.

Ideally you'd want each station to broadcast a test signal so you could adjust the parameters for each station (MythTV lets you do that, which is great).  But unfortunately few if any stations transmit test patterns.  So as far as I know you just have to do it by eye, either once for each tuner or (if you have the time) once for each channel you care about.

I suspect that someone could write some software that could monitor a channel for some time and come up with some statistical analysis that could suggest optimal settings.  Better still would be interactive software that asked the user to identify faces and other "known" objects that have a relatively narrow range of color.  But I'm not aware of any software that does this.  It would be interesting to write; I could consult if anyone's interested (I'm an adequate basic programmer, but that's as far as I can go).

Hope this helps somewhat...

-Fred

---

### Post by Weidbrewer on 2009-02-01
Yeah, you certainly did give it some thought.  I appreciate the help.

Yes, right now it is an analog signal coming in.  One thing that I suppose that I can do to at least get in the ball park is to go low tech.  Take that test signal you were talking about and run it in through the VCR I have hooked up (Putting old home movies on the HD) and see if that can get me a baseline.

Thanks for the help!

---

