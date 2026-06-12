---
title: "VLC GPU Acceleration"
date: 2012-09-28
forum: Multimedia Software
---

### Post by jacobroecker on 2012-09-28
I need to enable vlc to use GPU Acceleration.  VLC doesn't seem to have that option displayed under Preference ->Simple ->Input & Codecs where it should be.

System Specs:  
Dual Core Atom D525 (not powerful enough to do HD)
4GB of memory
512MB Next-Generation nVidia Ion

VLC is latest from Repos at 1.06
Ubuntu is 10.04 LTS

---

### Post by UltimateCat on 2012-09-28
This page about codecs and vlc might help

[http://www.ubuntugeek.com/install-multimedia-codecs-and-vlc-media-player-without-internet-connection-offline-in-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/install-multimedia-codecs-and-vlc-media-player-without-internet-connection-offline-in-ubuntu-10-04-lucid-lynx.html)

Hope that helps-

---

### Post by BicyclerBoy on 2012-09-28
VLC lucid 1.0.6 is ancient..
Find a ppa for a later version..
This gets 1.1.13..prob still too old.
[https://launchpad.net/~lucid-bleed/+archive/ppa/+index?field.series_filter=lucid&batch=75&memo=75&start=75](https://launchpad.net/~lucid-bleed/+archive/ppa/+index?field.series_filter=lucid&batch=75&memo=75&start=75)
(After checking: this ppa is no better than lucid universe version)

VLC 2.0.1 here:
[https://launchpad.net/~lucid-bleed/+archive/lucidbleed-exp?field.series_filter=lucid](https://launchpad.net/~lucid-bleed/+archive/lucidbleed-exp?field.series_filter=lucid)

(after checking this ppa: the VLC 2 build failed in July & there is no other build offered)


If your build of VLC can use va-api then you could take advantage of the vdpau backend for vaapi library package.
vdpau-va-driver

Then you get va-api on your nvdia vdpau h/w..
VLC does not support vdpau directly.

Otherwise the only GPU acceleration is just post decode shader & presentation stuff.

Note the ION GPU is more picky about supported formats..

Note: mplayer or smplayer prob works much better than vlc on your h/w

---

