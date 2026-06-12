---
title: "Problem with Totem and Firefox"
date: 2008-03-16
forum: Multimedia &amp; Video
---

### Post by arbulus on 2008-03-16
I'm having a problem watching video on the web with Firefox.  When i try to open a video, .wmv, .avi, quicktime, mpeg, anything, the Totem plugin opens up in firefox and the video starts, but I cannot see it, i can only hear it.  When I right click and say "Open in Movie Player" Totem will launch but the same thing happens there: no video and just audio. 

Anyone else having this problem or know how to fix it?  I have all the codec packs installed (gstreamer, medibuntu).

---

### Post by arbulus on 2008-03-17
Upon further investigation, I've discovered that I cannot watch video in anything at all.  Even when i download a video file, no matter the format, and open it in Totem, VLC, anything, all I get is the audio, I can't see it. 

If it helps, I have an ATI Raedon Xpress Series video card and I'm using the 8.43.2 driver.

---

### Post by arbulus on 2008-03-17
Ok, so I just discovered something I guess I should have checked from the beginning.  
This is all taking place on a Dell Inspiron 1501 laptop.  Attached to this laptop is a 22" widescreen monitor. Normally, I have the laptop lid closed as it sits on my desk behind the monitor.  But I just, out of curiosity, opened the laptop's lid and realized that I can see the video on the laptop's monitor, but not on the external monitor. 

This is actually an interesting situation.  When I plugged the external monitor the the lappy originally, I was trying to set the resolution, but realized that I couldn't get it any higher than what displays on the laptop itself.  so I have a 22" monitor with a native resolution of 1680x1050 displaying the 1280x800 resolution of the laptop. it just mirrors the display. 

The video card has 128 MB of RAM, and i have a total of 2 GB in the machine. I'm using the most up to date 3D accelerated video driver for my card. So it should be powerful enough to display the full 1680x1050 resolution on my 22" monitor, as well as showing me the video. 

Could this be some sort of configuration issue of a second screen?  I've never used two monitors in Linux before, so i really don't know anything about it.

---

### Post by wolfen69 on 2008-03-17
someone found a fix here [https://answers.launchpad.net/ubuntu/+question/17857](https://answers.launchpad.net/ubuntu/+question/17857)

---

### Post by arbulus on 2008-03-17
> **wolfen69 said:**
> someone found a fix here [https://answers.launchpad.net/ubuntu/+question/17857](https://answers.launchpad.net/ubuntu/+question/17857)


It looked like they were trying to get an extended desktop across two monitors.  I still want my external monitor to mirror the laptop's monitor, I just want it to be at it's native resolution and to show my videos.

---

### Post by Pijits_1 on 2008-03-17
Have you tried these codecs?

```
sudo apt-get install ubuntu-restricted-extras
```

```
sudo apt-get install w32codecs
```

```
sudo apt-get install libxine-extracodecs gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-pitfdll
```

I'm pretty sure they may help

---

### Post by Pijits_1 on 2008-03-17
> **Pijits_1 said:**
> Have you tried these codecs?

```
sudo apt-get install ubuntu-restricted-extras
```

```
sudo apt-get install w32codecs
```

```
sudo apt-get install libxine-extracodecs gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-pitfdll
```

I'm pretty sure they may help

I just read the rest of your posts. Sorry I can't help with that

---

