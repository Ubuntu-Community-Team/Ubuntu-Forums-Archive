---
title: "play media files with totem"
date: 2007-11-26
forum: Multimedia &amp; Video
---

### Post by Dino05 on 2007-11-26
I' ve an on-again off-again experience with totem media player. I'm either able to play downloaded media files but not streaming video from a website or vice verser. I did install the w32codecs_20071007-0.0_i386.deb and install/remove re-install gstreamer and so on and so off. Currently I can play streaming video from ie C_SPAN but not able to play an mp3 file stored on my hard drive.
This is the error msg I get when I try to play downloaded files :-

[B]Totem could not play 'file:///home/dino/ug386-hour1mix.mp3'.

Audio codec 'MPEG 1 Layer 3 CBR' is not handled. You might need to install additional plugins to be able to play some types of movies[/B]

---

### Post by Keith Hedger on 2007-11-26
I thing you have to install the gstreamer plugins (via synaptic) gstreamer0.10-plugins-good, gstreamer0.10-plugins-ugly-multiverse and gstreamer0.10-plugins-bad

---

### Post by Majorix on 2008-01-20
^ That didn't work for me :(

---

### Post by cor2y on 2008-01-21
Enable the restricted repos first.
System->Administration->Software Source
Check off univers,multiverse,restricted.
Then update your sources finally via Synaptic or Add/Remove enable all gstreamer plugins.

---

