---
title: "Mele A1000 TV box as frontend?"
date: 2012-05-09
forum: Mythbuntu
---

### Post by dibuntux on 2012-05-09
You probably know this: Mele A1000 TV box. It is an Android TV box
with this specs ARM CortexA8 1GHz DDR3 512MB RAM / 2GB Nand Flash, MALI GPU HDMI 1080p output, with a nice remote, that has been hacked to run an Ubuntu 10.04 image!

[http://rhombus-tech.net/allwinner_a10/hacking_the_mele_a1000/](http://rhombus-tech.net/allwinner_a10/hacking_the_mele_a1000/)

Has somebody tried to run Myth on it? It would be the perfect front end! Google around, there are some Utube videos of the stuff.

What do you guys think?

---

### Post by nickrout on 2012-05-10
> **dibuntux said:**
> You probably know this: Mele A1000 TV box. It is an Android TV box
with this specs ARM CortexA8 1GHz DDR3 512MB RAM / 2GB Nand Flash, MALI GPU HDMI 1080p output, with a nice remote, that has been hacked to run an Ubuntu 10.04 image!

[http://rhombus-tech.net/allwinner_a10/hacking_the_mele_a1000/](http://rhombus-tech.net/allwinner_a10/hacking_the_mele_a1000/)

Has somebody tried to run Myth on it? It would be the perfect front end! Google around, there are some Utube videos of the stuff.

What do you guys think?

I think that you will have no video acceleration that is compatible with mythtv and it will therefore fail at playing back any decent video stream.

OTOH I believe xbmc has video acceleration compatibility for the major ARM video acceleration method. so XBMC running mythbox may be a better bet.

---

### Post by dibuntux on 2012-05-10
Yes, it was stated that at the moment there's no HW acceleration, nonetheless they were having a fair performance out of opensw drivers. 
But, I sow a demo of ubuntutv that was running on accelerated codec on an ARM box. 
And about XBMC, it is using VDPAU right? So if XBMC can run, maybe myth can too...

Otherwise, you can just use the box in Android as I'm doing it now with my phone: program a show with the browser using mythweb and then accessing the recording with UPnP client, (Bubble UPnP). Not as clean as a myth frontend, but better than most tv box with no browser, and thus no ways of starting a recording.

---

### Post by nickrout on 2012-05-10
> **dibuntux said:**
> Yes, it was stated that at the moment there's no HW acceleration, nonetheless they were having a fair performance out of opensw drivers. 
But, I sow a demo of ubuntutv that was running on accelerated codec on an ARM box. 
And about XBMC, it is using VDPAU right? So if XBMC can run, maybe myth can too...

Otherwise, you can just use the box in Android as I'm doing it now with my phone: program a show with the browser using mythweb and then accessing the recording with UPnP client, (Bubble UPnP). Not as clean as a myth frontend, but better than most tv box with no browser, and thus no ways of starting a recording.

It has nothing to do with VDPAU, which is not available on ARM, nor does the android box have an nvidia GPU. I cannot recall the name of the technology that drives most ARM video acceleration but XBMC supports it, mythtv doesn't.

These and similar boxes are quite cheap, and certainly worth trying, but there are certainly reports that even the native android client has significant video playback problems. eg [http://androidforums.com/google-tv/338651-android-tv-box-flexiview-fv-1-a.html](http://androidforums.com/google-tv/338651-android-tv-box-flexiview-fv-1-a.html)

EDIT: The technology I am referring to is OpenMAX.

---

### Post by dibuntux on 2012-05-11
Yes, I know VDPAU is Nvidia; but I also know of some efforts to use VDPAU as an interface to other GPU. Kind of DirectX for Linux, something it lacks the most. To have programs support directly the hardware and not a common API is so '80s.
I think the people that made the Ubuntu image for it want to use XBMC... so I imagined somebody was interested in having myth on stuff like that.
BTW, my phone with an ARM v6 can play almost anything with MX Player on Android 2.2, albeit slow (ehi, 600 MHz on SW codecs).

---

