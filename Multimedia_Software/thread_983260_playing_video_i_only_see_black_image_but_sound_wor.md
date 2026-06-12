---
title: "playing video i only see black image but sound works fine"
date: 2008-11-15
forum: Multimedia Software
---

### Post by Fenix-TX on 2008-11-15
I've enabled medibuntu, installed all packages needed (non-free-codecs, kubuntu-restricted-extras, w32codecs, all gstreamer packages, all libxine packages and more!!), installed other players like mplayer, kmplayer, vlc, and with all video players (dragon player included) i only have sound and black image!! Any ideas?

---

### Post by cariboo on 2008-11-15
Have you installed the unbuntu-restricted-extras meta package?

Jim

---

### Post by Fenix-TX on 2008-11-15
Yes, i've installed ubuntu-restricted-extras package too :(

---

### Post by Neostar on 2008-11-15
Might be a problem with the driver for the graphics card.

---

### Post by Fenix-TX on 2008-11-15
I'm using ati opensource driver

I've forgot to say that videostreaming is working and youtube too

---

### Post by Fenix-TX on 2008-11-16
Tunning xine options on kmplayer made see video on kmplayer, but not on others media players. In fact, i think that was the option: video.device.xv_preferred_method -> Textured Video (it was Any, and i've changed it). Is there any way to change that globally?

---

### Post by Fenix-TX on 2008-11-16
Ok, editing ~/.xine/config file and doing some settings, now works.

---

### Post by harsh1kumar on 2009-02-27
I want to know how you fixed the issue you had. I have similar problem.:confused:

---

