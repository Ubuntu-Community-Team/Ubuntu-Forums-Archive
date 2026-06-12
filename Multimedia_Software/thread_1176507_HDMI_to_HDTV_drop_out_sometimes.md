---
title: "HDMI to HDTV drop out sometimes"
date: 2009-06-02
forum: Multimedia Software
---

### Post by diamondnular on 2009-06-02
Hi folks,

I need help and advice for my system. I have a HTPC with GTX 260 video card running Jaunty. Recently I got a new Sharp Aquos LC40E77U that I want to run as my monitor. In order to connect to the TV, I used the DVI to HDMI adapter on the video card, then a HDMI from the card to the TV.

Currently I leave xorg.conf as default, meaning it recognizes the TV and change the resolution itself. The maximum resolution xorg sets for the TV is 1650x1050. I always have to manually use nvidia-settings to change the resolution to the maximum capability of my TV (1920x1080) once I get booted in to Desktop. Also the frequency I can set here is 60Hz or 24Hz only, I do not see 120Hz there to set.

So far it goes just fine, but I have sometimes some frame drops (the screen goes black, no indicator light, no signal for about half of a second) but sound is fine (sound is connected separately). The dropout increases when I try to play Steam games (for example, condition zero etc...). The dropout also increases on some applications (especially on XBMC when browsing, but once XBMC runs any movie, it is fine). 

Also note that if I use DVI to VGA connector, I do not have such frame drops, but the resolution is really low (1024x768). And I tried with some different HDMI cables with the same issue, so HDMI cable is not the problem.

Sorry for such a long description, but I am trying to make it as clear and detail as possible. So here comes the questions:

1. anybody with HDMI connection has ever suffered such frame drops?
2. what can cause such phenomena: the bad resolution, the refresh rate or something else?
3. I want to set fix resolution (1920x1080) in xorg.conf, but with no luck. Googling or searching here give quite a lot of results, but following them give no success. For example, when I tried adding ```
Modes "1920x1080_60.00"
```, the xorg.0.log says its the wrong resolution. What should I do?

Thanks in advance. Any input for any question will be greatly appreciated.

D.

---

