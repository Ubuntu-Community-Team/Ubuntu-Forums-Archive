---
title: "Pulseaudio overdoing the vacuuming (a2dp source sink + android)"
date: 2015-05-31
forum: Multimedia Software
---

### Post by frankerooney on 2015-05-31
Hi all,
  Ubuntu 14.10 - successfully created an a2dp sink with ubuntu on my laptop, and am connecting an android tablet to it ok, but unless the android tablet starts to play straight after connecting, pulseaudio gets a bit keep and sets the profile to "off", and a2dp as unavailable, which android doesn't like and promptly disconnects :

: [pulseaudio] core.c: Hmm, no streams around, trying to vacuum.
I: [pulseaudio] sink-input.c: Freeing input 0 "Loopback from Hudl 2"
D: [bluetooth] module-bluetooth-device.c: IO thread shutdown requested, stopping cleanly
D: [bluetooth] module-bluetooth-device.c: IO thread shutting down
I: [pulseaudio] source.c: Freeing source 2 "bluez_source.60_02_92_86_3C_21"
I: [pulseaudio] card.c: Changed profile of card 2 "bluez_card.60_02_92_86_3C_21" to off
D: [pulseaudio] card.c: Setting card bluez_card.60_02_92_86_3C_21 profile a2dp_source to availability status no

How can I stop pulseaudio's extreme urge to clean stuff up like this?

I've tried not loading not loading the module-suspend-on-idle

### Automatically suspend sinks/sources that become idle for too long
#load-module module-suspend-on-idle

.. but it doesn't seem to be this causing the issue.
Any ideas?

Thanks

Andy

---

### Post by frankerooney on 2015-05-31
Ah, ok so I had been messing with PA 5 and bluez 5 from this PPA :
deb [http://ppa.launchpad.net/kubuntu-ppa/utopic-bluez5/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/utopic-bluez5/ubuntu) utopic main

it behaves much better and keeps a stable connection. Now, to balance things out, audio stutters on some of my devices, which wasn't happening before. Tried disabling the idle module, nothing doing

:-(

I love Linux to bits, but sometimes it drives me nuts.

---

### Post by frankerooney on 2015-06-01
Ok, so it's sorted now. Bluez 5 is the dogs whatsisname, my android device I was trying was nearly out of power and throttling the cpu I think. S'ok now.
Trying pulseaudio 6 next to try and bring back headset type functionality. Anyone any experience with AVRCP?
TTFN

---

