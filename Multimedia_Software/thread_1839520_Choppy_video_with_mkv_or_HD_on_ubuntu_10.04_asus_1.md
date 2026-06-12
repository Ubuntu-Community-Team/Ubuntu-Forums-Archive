---
title: "Choppy video with mkv or HD on ubuntu 10.04 asus 1000he"
date: 2011-09-05
forum: Multimedia Software
---

### Post by dutty.persian on 2011-09-05
I've reinstalled fresh 10.04 on my sister's asus eee 1000he. For some reason, high definition videos, (more than 480i) are super choppy, as in extremely low frame rate. These can be HD youtube videos as well (720p and up).

Anything with a lower resolution is fine.

I've done a search for this and don't quite get what I'm looking for. Most problems with other ubuntu users are for ATI cards and their proprietary drivers.

As far as I know, the intel GMA 950 graphics card does not have a proprietary driver and the card should be able to play 1080p movies no problem. As a matter of fact, on the netbook netbook edition 11.04, high def movies worked fine. I switched to 10.04 because 11.04 was causing way too many problems.

Can anyone steer me in the right direction?

---

### Post by dutty.persian on 2011-09-06
bump

---

### Post by papibe on 2011-09-06
I'm afraid there's no easy and transparent HD playbay in Ubuntu (at least as today).

You need to install the appropriate acceleration driver for your card, then use a player that supports it.

I'm fairly experienced using and setting up Nvidia cards, but not Intel's. So please take this as general guidelines.

AFAIK, you can play HD by using VAAPI. To install the library for your card:
```
$ sudo apt-get install i965-va-driver
```
To test that the library is working, install this:
```
$ sudo apt-get install vainfo
```
To test it:
```
$ vainfo
```
VLC can use the VAAPI library, but you need to setup a few options. I believe it's enabled in 'Input and Codecs' - 'Use GPU acceleration'

I hope it helps,
Regards.

---

### Post by BicyclerBoy on 2011-09-06
Intel have only just made graphics chips that work.
GMA500 Pouslbo X4500 bought  Power VR, tungsten graphics driver.
HD2000 3000 sandybridge, likely Power VR devices.

I my experience the GMA950 can not play 1080p H264 (with an atom CPU).
It just manages 576i H264.

The later atom PineTrail CPU/GPU chip is the one to buy, the old GME945 chipset atom was rubbish when it was released.

There is some small possibility it could do better with mpeg2 because it has some h/w decode support.
There is a **very smal**l possibility that VAAPI could help but this is unlikely.

I would try the xorg-edgers launchpad ppa so you are closer to leading edge i915 driver etc.

---

### Post by dutty.persian on 2011-09-06
you're right about 1080p, but on 11.04, i was able to stream 720p tv shows from my NAS and youtube. Now, the max I can view is 480p. does 11.04 have special drivers?

---

### Post by BicyclerBoy on 2011-09-06
The intel driver i915 should be used by 11.04.
I only used 10.04 on intel i3 graphics for couple days (~1 year ago), terrible..

The driver, kernel & Xorg all play an important part in performance (or lack of).
The i915 driver (& Xorg) in 10.04 will be older than the version in 11.04.

The video driver should show up in dmesg, lsmod, or cat /var/log/Xorg.0.log
Check 
glxinfo | grep OpenGL

xorg-edgers is at 1.4 Mesa 7.12-devel (for 11.04)

It is difficult/wrong to compare playback on just resolution (as I did), what really matters is the video codec (h/w or s/w decode) & bitrate.

945GME GMA950 only has partial h/w decode for mpeg2. (wikipedia)

---

