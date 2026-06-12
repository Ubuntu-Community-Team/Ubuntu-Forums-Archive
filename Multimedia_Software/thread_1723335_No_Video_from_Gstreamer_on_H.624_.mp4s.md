---
title: "No Video from Gstreamer on H.624 .mp4s?"
date: 2011-04-06
forum: Multimedia Software
---

### Post by castironpants on 2011-04-06
I had been having trouble with Banshee playing podcasts and it turned into a bigger problem. I use VLC so I hadn't noticed, but Totem (and Gstreamer as a whole) can't seem to play h.624 video. All I get is audio, even when I do a command like 

gst-launch -v playbin uri=file:///path/to/video.mp4

(Well, now I get nothing, but more on that in a moment).

So I tried reinstalling Gstreamer, and I just tried updating to the Gstreamer Developer PPA. The only change that came from that is that now nothing happens instead of just hearing audio. I've attached the output.

I've gone into gstreamer-properties and tried every configuration. Each time I see the colored stripes and the snowy video corner, but it never seems to make a difference. What's wrong?

---

### Post by no2498 on 2011-04-07
install smplayer it loads a 264 file with it
its the front end of totem

---

### Post by castironpants on 2011-04-07
Are you sure? I thought it was an mplayer gui

---

### Post by castironpants on 2011-04-07
As I suspected, that did nothing. I'm not trying to REPLACE Totem (I don't even normally use to play video) but I need Gstreamer to be able to handle this video to watch video podcasts in Banshee.

---

### Post by BicyclerBoy on 2011-04-07
Do you have installed the gstreamer good bad & the ugly packages ?
Search in synaptic
I think you need to allow additional repos..

Have a quick try (just to confirm anything works) with VLC as it has worked with mpeg4/10-H264-AVC for some years..

Is your video playback using video decode acc in the fglx ATI driver ?
Could this be the problem..
VLC will not use VA-API (GPU h/w) unless compiled from source or 3rd party ppa (splitted-desktop).

---

### Post by castironpants on 2011-04-07
I have all three sets (both regular and multiverse for bad and ugly) installed

---

### Post by no2498 on 2011-04-08
you also need the 10 that goes with the ubuntu you use

---

### Post by Yellow Pasque on 2011-04-08
It looks like you installed gstreamer-vaapi and are trying to use it. FWIW, it was broken the last time I tried it. Using gstreamer's X11 video output would be safest.

---

### Post by castironpants on 2011-04-09
I'll try uninstalling that, rebooting and giving that a go then. Thanks! (I'll let you know if it works)

UPDATE: Yes, that totally solved it! Thank you so much, Temüjin

---

