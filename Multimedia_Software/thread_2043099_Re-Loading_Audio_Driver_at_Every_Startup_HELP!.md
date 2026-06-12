---
title: "Re-Loading Audio Driver at Every Startup HELP!"
date: 2012-08-15
forum: Multimedia Software
---

### Post by geekymaestro on 2012-08-15
I thought I had posted this, but it doesn't exist so here goes.

I have a Sound Blaster X-Fi Titanium card and am running 12.04 LTS 64-bit.  Every time I boot into Ubuntu, I have to type the following in the terminal:

```
gstreamer-properties
```

Which then brings up a box where I can select "ALSA" or "Pulse Audio" as the driver and then manually select "Front/WaveIn" for the device.  This works and I am able to get audio from the card. Problem is, I'm having to do this EVERY time.  There has to be a better way.  I'm not a noob with Linux, but I'm not a superuser either.  Any help on how I can get these values to load at startup would be appreciated.

---

