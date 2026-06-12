---
title: "Ubuntu crashes when using an external monitor"
date: 2009-09-21
forum: Multimedia Software
---

### Post by GenePayne on 2009-09-21
I've been running Ubuntu successfully on my Lenovo Thinkpad T61 for a year now (currently running 9.04).

I recently tried to switch to using an external monitor with this laptop (it has a VGA output port). I hooked it up to an LG W2353V 23" widescreen LCD monitor. My laptop has an nvidia Quadro NVS 140M graphics card.

The display looks great on the external monitor. I have tried it in both dual monitor mode (using my laptop screen) and the LCD monitor alone. It runs fine... for a while. However it will not run more than an hour at most before crashing. The mouse cursor hangs, and the system just resets.

The crashing seems to be related to events like resizing a window or opening a new window. I suspect the nvidia driver as the culprit, but I'm not sure.

Any thoughts?

---

### Post by GenePayne on 2009-10-06
Update on this problem:
I have run about 32 hours successfully without a crash now. I disabled compiz by choosing no visual effects (System -> Preferences -> Appearance -> Visual Effects -> None).

So apparently compiz is preventing my system from working with an external monitor. Does anyone have any idea why? Could it be that compiz or the nvidia video driver just can't handle resolution this high? I highly doubt this, since I'm just running on a 23" widescreen LCD at 1920 x 1080. There must be many people running at this high or higher.

Next, I will try re-enabling compiz with a minimum of the features installed, and then one-by-one enable features to see if one of them is related to my system crashing.

---

### Post by GenePayne on 2009-10-16
I have tried a few times to run with compiz and as few as possible of its features enabled, but it still crashes. I guess I can't use compiz with two monitors.

Anyone else have any problems with running compiz on dual monitors?

---

### Post by mjpoetic on 2010-04-07
I know this is pretty late, but check this site out for the workaround:

[http://codebaboon.com/dual-monitor-desktop-effects-810#comments](http://codebaboon.com/dual-monitor-desktop-effects-810#comments)

It refers to arranging the two monitors to be one on top of the other in a virtual space

---

### Post by GenePayne on 2010-04-26
Thanks for the reply. I looked into this fix, but it isn't the problem I'm having. My GL_MAX_TEXTURE_SIZE is 8192, so it seems big enough to work.

This problem seems to apply to those who can't even start compiz. I'm able to get compiz to work at first--it works for maybe an hour but then the system just crashes.

---

