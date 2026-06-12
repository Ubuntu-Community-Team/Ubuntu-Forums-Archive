---
title: "Nvidia Optimus laptop w/ HDMI + Mini-DP and PRIME... get port to work?"
date: 2014-02-24
forum: Multimedia Software
---

### Post by Sir_Brizz on 2014-02-24
Hi all,

This thread title might be absolutely crap but I couldn't think of a better way to put it. I have a laptop with stupid Nvidia Optimus technology inside. It's a Dell XPS 15 (L521x).

I have been trying to get all of the ports on my laptop working without much success. It took me forever just to get the video working in a sensible manner. Right now I'm on 14.04 with the proprietary Nvidia drivers and the nvidia-prime package. I am in Power saving mode (the intel card is all that shows up).

I really want to be able to use both the HDMI out and the Mini-DP out. HDMI works fine, I can plug it and unplug it and the screens respond properly. It still has some issues but they are bearable.

The miniDP port seems entirely useless. I have a Monoprice MiniDP to HDMI adapter and a monitor plugged in there. I can't get any video out to it. If I plug it in, the screen flickers like it knows I did something but the device never shows up in the Display manager or in xrandr -q

Has anyone done this set up? I found a few people saying they got it working by setting an xorg.conf manually somehow, but that doesn't seem like a very portable solution. I use this laptop at the office with two monitors as well as on the road and I need it to be adaptable to both situations.

Are there any crazy xrandr debugging things I can do to even see what is happening when I plug the device in? I have frankly never really done any debugging on xrandr or xorg in general before.

Help?

---

