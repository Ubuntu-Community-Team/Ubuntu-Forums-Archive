---
title: "Poor Video performance on Asus Zenbook Prime UX31A"
date: 2012-12-16
forum: Multimedia Software
---

### Post by PikoMedia on 2012-12-16
Hi,
I've got this very annoying video performance issue on my fairly new Asus Zenbook Prime UX31A running ubuntu 12.10.

Graphics (youtube, vlc, mplayer, and even sometimes the desktop) is sluggish and lags terribly. With vlc reducing the window size seems to reduce the problem, but given that the same media runs smooth and nice on my 8 year old(!) FS Amilo Si-1520 with Ubuntu 10.04, I can only deduce that something is running in a degraded mode.

The problem is not limited to vlc, but for now vlc's output when running for ex an avi is my only lead:

"xcb_xv vout display error: no available XVideo adaptor"

This post (french) [http://forum.pcastuces.com/sujet.asp?f=8&s=13645](http://forum.pcastuces.com/sujet.asp?f=8&s=13645) suggests to manually set video output in vlc to "X11 XCB". Doing so, it seems to have helped for VLC, but how do I fix this for the other media such as streaming video off the web? I use chrome, and from a quick look at the parameters, I couldn't find any obvious control equivalent to vlc's X11 XCB option.

Any ideas? Any logs I can pull to help to understand this better?
Thanks

---

### Post by BicyclerBoy on 2012-12-16
AFAIK std *buntu distros have the SNA (& ivybridge) iGFX switched to safe/slow mode.

To make HD4000 work you need a very recent kernel (12.10 should be okay) & the recent build of intel driver.
All this is available from xorg-edgers ppa.

You might like to install VA-API packages:
vainfo
libva-intel-vaapi-driver
libgstreamer-vaapi*

VLC has native VA-API decode support.
AFAIK you can still use XVideo or openGL rendering with VA-API.

---

### Post by PikoMedia on 2012-12-16
Thanks BicylerBoy for sharing your insight. I'm a long-time ubuntu user, but my intimate knowledge of what's under the hood is limited. So I have a couple of questions on your sugestions:

> **BicyclerBoy said:**
> AFAIK std *buntu distros have the SNA (& ivybridge) iGFX switched to safe/slow mode.

To make HD4000 work you need a very recent kernel (12.10 should be okay) & the recent build of intel driver.
All this is available from xorg-edgers ppa.

Meaning adding xorg-edgers to sources.list, I suppose? Any known stability issues with that?

> **BicyclerBoy said:**
> 
You might like to install VA-API packages:
vainfo
libva-intel-vaapi-driver
libgstreamer-vaapi*

I hope installing the VAAPI packages is reversible (with out too much hassle) in case it has stability issues. Any experience to share on that? 

> **BicyclerBoy said:**
> 
VLC has native VA-API decode support.
AFAIK you can still use XVideo or openGL rendering with VA-API.

---

### Post by BicyclerBoy on 2012-12-16
Wise words spoken from past experience ??

Xorg-edgers ppa, by very nature, is always in a state of change.
I have used it for couple years & only had cause to grumble in a couple of instances.
The newer kernel (3.5 for 12.04)  broke the BCM4312 wifi driver (fix req. tweak 2 lines of code).
The kernel version 3.7 is provided for *buntu12.10
[https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=quantal](https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=quantal)

VA-API is not new but the latest driver exposes new capabilities.
You choose the video decode/renderer from player's setup.
So I don't see any problems with VA-API install per se.

Un-winding the xorg-edgers ppa installation could get messy but they recommend:
sudo ppa-purge xorg-edgers

---

### Post by PikoMedia on 2012-12-16
Indeed, I've had my fair share of "adventures" while installing and uninstalling packages in the past, so I tend to be conservative when I try things out. But I'll check it out.

---

