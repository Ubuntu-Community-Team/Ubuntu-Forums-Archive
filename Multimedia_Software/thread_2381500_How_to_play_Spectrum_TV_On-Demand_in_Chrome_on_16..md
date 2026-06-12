---
title: "How to play Spectrum TV On-Demand in Chrome on 16.04.3"
date: 2018-01-01
forum: Multimedia Software
---

### Post by accounts0 on 2018-01-01
So when I try to play any of the content available through the Spectrum TV website, I just get a black screen where the video should be. I tried changing the User Agent to a current Windows Chrome build, but it didn't do any good. It also makes no difference if the Flash Player settings have the "Enable hardware acceleration" checkbox checked.

It works fine in a Win7 VM, but I'd rather be able to play at the higher screen resolution I get on the host.

Ubuntu version: 16.04.3 LTS
Google Chrome Stable version: 63.0.3239.108-1
Adobe Flash version: 28,0,0,126
TWC Player version: 1.7.0
* PSDK version: 1.4.38.891

* I don't know what this is, but its in the info displayed when right-clicking the screen

---

### Post by accounts0 on 2018-01-04
When I run a video in Chrome on the Win7 VM, I can only get the display resolution to exceed the Win7 desktop settings if I use the VirtualBox display window, which scales the remote resolution to whatever the VirtualBox display window is set to- be it maximized or whatever. However at these larger sizes, the stream stutters as if there's a lack of resources at some point. This goes away if I don't maximize everything & use a size that's around less than half of my primary display on the host.

If I connect to the VM via RDP in Remmina's display window, I'm unable to exceed the resolution set in the Win7 desktop settings & end up with a black border between the Win7 desktop's resolution & the Remmina window, if I maximize it. I can do scaled mode in the Remmina window, but it looks all blurry & is too awful to use.

In both cases, I'm unable to go fullscreen in whatever the player is embedded in Chrome- or it sputters. I can make it run smoothly if I use <2/3 Win7 screen at the 1/2 host screen sized viewport- via RDP or the VirtualBox display window.

Ideally I'd be able to watch on the Linux based host & forego all the unnecessary abstraction.

EDIT:

It seems now that however I go about watching in the VM, I end up with a terrible 1-3 second delay between the content & the sound coming from the host. Also between hitting pause in the guest & when it actually stops both audio & video on the host.

---

