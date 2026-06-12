---
title: "Can Someone Help Me Program My Monitor Chip (24LC21) Over The i2c bus?"
date: 2011-03-24
forum: Multimedia Software
---

### Post by rainbowagent7 on 2011-03-24
Thanks in advance. I have a Viewsonic VG191 connected with VGA and have to manually enter the EDID table as specified by the manual because it is not being detected on it's own. I have researched this issue extensively and as I was reading the manual it specifically stated that > In order to use the 24LC21 in a monitor system, it must be programmed with a proper EDID table and then properly connected to the signals coming from the video controller card. The VESA committee has specified that the connections for DDC transmission can be part of the standard 15-pin VGA connector. A table of pinouts for this connector are shown in Table 2 
The reason I'm doing this is so I can run the native resolution of 1280X1024, and quite frankly because I believe following the manufacturers specs is the right thing to do. I've successfully added that modeline via the cvt method and had it working, but many video related issues started showing up afterwards and the image just didn't "feel" right. I would feel much more settled Knowing ALL of the specs have been entered correctly and there is no unnecessary noise in the communication of video card and monitor. I created an xorg.conf file so I can add any parameters needed which, thank Heaven, were all in the manual (Viewsonic kicks butt!). Anyway, if someone knows this area and could help that would be awesome because I'm determined to finish it. I'm still noobish but have a very good grip on Ubuntu and can follow instructions well.

---

### Post by rainbowagent7 on 2011-03-24
Anyone? I'll be here all night:-]

---

### Post by rainbowagent7 on 2011-03-24
Am I not being specific enough?

---

