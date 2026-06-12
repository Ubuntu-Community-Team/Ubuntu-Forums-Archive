---
title: "Rythmbox and a Xine back-end"
date: 2009-06-17
forum: Multimedia Software
---

### Post by Aiello on 2009-06-17
Well, I have a bit of a dilemma on my hands. 

Most of my music collection is in WMA Lossless and I would like to use Rhythmbox as my music player/manager. Unfortunately, Rhytmbox uses Gstreamer as its back-end, and thus cannot play WMA Lossless files. Now, I also have Xine installed on my system, which I know can be used as the back-end for music/media players and can play WMA Lossless. Is there any chance I can get Rhytmbox to use Xine as its back-end instead of Gstreamer?

Thanks!

---

### Post by mc4man on 2009-06-17
If you were to search rhythmbox-xine there isn't anything dating after 2005, it appears it was once an option in 0.8.x and earlier. So I'd say no way.

---

### Post by TheNosh on 2009-06-17
i'm pretty sure their are gstreamer plugins for WMA. i play WMAs in rhythmbox just fine, and i'm pretty sure all i did was try to play it and then get prompted to download the plugins, so i just clicked okay and that was it.

---

### Post by kostkon on 2009-06-18
Try installing the *gstreamer0.10-ffmpeg* package and see if that will make any difference. Also, you could install the *w32codecs* (or *w64codecs*) from [*Medibuntu*]("http://medibuntu.org/") (*gstreamer0.10-pitfdll* must be installed for this).

---

### Post by mc4man on 2009-06-18
Gstreamer does not play wma **lossless** unless you purchase the fluendo codec pac

---

### Post by markbuntu on 2009-06-18
Rythmbox is a Gnome app and gnome uses gstreamer. 
KDE and KDE apps use xine. 

There are some apps which use both but rythmbox is not one of them. You can get Totem in gstreamer or xine flavors. vlc uses xine and so does amarok since they are KDE apps though vlc is somewhat less dependent on the KDE libs than amarok. 

Try amarok, it is my favorite player.

---

