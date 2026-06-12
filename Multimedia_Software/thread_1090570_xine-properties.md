---
title: "xine-properties?"
date: 2009-03-08
forum: Multimedia Software
---

### Post by etherealeclipse on 2009-03-08
I finally managed to get videos playing while moving windows with the opensource ati drivers with gstreamers by spesifying it uses the, erm... textured radeon drivers (or something like that not at my computer at the moment) via gstreamer-properties, is there a xine version of gestreamers properties as i use totem-xine as the gstreamers version dosen't really work when playing dvd's (can't wait for jaunty). and help on specifying which driver xine uses?

---

### Post by cariboo on 2009-03-08
Have you got libdvdcss2 installed? It is available in the [Medibuntu]("http://help.ubuntu.com/community/Medibuntu#Adding the Repositories") repositories.

Jim

---

### Post by etherealeclipse on 2009-03-08
Yes I do i get the failed streaming or something like that error with the gstreamer totem, though I've only tried this on one dvd never tried other dvd's with the gstreamer if the problem is the dvd though it works with the xine totem.

---

### Post by markbuntu on 2009-03-09
There is not really any xine settings manager like gstreamer has but you can set all the xine backend defaults by running the xine-ui video player setup menu. You can find it with the Synaptic Package Manager

xine-ui

---

### Post by etherealeclipse on 2009-03-09
Doesn't really help with totem-xine i.e. it doesn't change some sort of 'xine global settings' though this issue isn't that big of one after all I don't really watch dvd's all that much would just be good to know how in case after all what sells linux to people more than seeing vidoes playing as you rotate your desktop cube :D (hiding the fact it took a while to get it working quite as well). Also the change i gig to get it working on gstreamers was choosing the default output device as the 'radeon textured video' which i think started appearing after adding Option texturedvideo "on" to my xorg.conf.

---

### Post by gandaran on 2009-03-09
totem-gstreamer doesn't play DVD'S with menus (but will work if you buy the fluendo-gstreamer codecs) try using other players if you don't want to pay for codecs, vlc, mplayer and gxine are very good players for DVD'S or any other format, mplayer and gxine/xine use the w32codecs package, make sure you have this package plus libdvdcss2 installed.

---

### Post by etherealeclipse on 2009-03-09
I like totem, I was really just asking if it could be done not that big of a issue other than that I'm happy with totem even though I use two versions.

---

