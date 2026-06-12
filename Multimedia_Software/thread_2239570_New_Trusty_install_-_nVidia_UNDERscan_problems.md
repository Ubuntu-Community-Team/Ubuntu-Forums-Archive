---
title: "New Trusty install - nVidia UNDERscan problems"
date: 2014-08-14
forum: Multimedia Software
---

### Post by kernalkorn on 2014-08-14
My Ubuntu on a 720P Philips 32" has always had a slight underscan.  This is over HDMI output from nVidia Asus "silent" 210.  16:9 desktop would leave small black bands top and bottom and pan over if the cursor was run beyond the edge.  The condition became much worse with 14.04 and now shows weird distracting artifacts off the edge of the desktop.  The Ubuntu SETTINGS > DISPLAYS apparently does not have pixel-by-pixel matching or a slider or "fit to screen" capability.  Or does it?  There may be an nVidia 210 utility buried in there somewhere that might help. The Philips 32PFL3505 is a very primitive early model without much adjustment. Any suggestions?

---

### Post by trag on 2014-08-15
add a VGA/HDMI adapter in your setup. Audio will still be sent via hdmi but video output will be converted from HDMI to VGA before going into your Monitor. Set your monitor settings to VGA from HDMI, all your over/under scan problems will go away.
good luck
Trag

---

### Post by kernalkorn on 2014-08-17
Thanks for reply.  I'm not quite clear on this.  The Philips is an LCD TV and does not have VGA input.  it has S-video, composit, component, and 3x HDMI. So this is a hardware thingie that turns an HDMI into a VGA, but what it the output connector to TV?  That would be great if something like this would "fit to screen".   I'll start researching on string "HDMI to VGA converter".  DVD Movie output over HDMI from Win7 Media center with this old outfit is perfect.  Just a very slight underscan showing the whole 16:9 screen with no artifacts or anomalies.  It just the Ubuntu I-net sessions that have the wobbly borders with what looks like the jittering corners of browser pages around the edges of the wall paper background.

---

### Post by kernalkorn on 2014-08-18
I tried DVI  instead of HDMI and it went from slight underscan to huge overscan.  I'll look intio a VGA  (from nvidia output) to HDMI (TV input) converter which might be more accurate "fit to screen".

---

