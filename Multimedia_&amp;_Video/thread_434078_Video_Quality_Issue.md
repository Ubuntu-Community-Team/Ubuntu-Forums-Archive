---
title: "Video Quality Issue?"
date: 2007-05-05
forum: Multimedia &amp; Video
---

### Post by dhice on 2007-05-05
I've installed the gstreamer apps, and I can play the DVD's fine.  However, I have two problems with the current playback.

1. I cannot view the DVD menu's nor play the correct file.

2. The DVD quality is VERY poor, and the colors are completely off.  When I first tried it out, the people were blue until I messed around with the video option in Totem; however, the people's lips are of a yellowish hue.

If you can provide any assistance that would be great thanks!

[IMG]http://img.photobucket.com/albums/v18/ducksigs/Spiderman_2.png[/IMG]

---

### Post by disturbed1 on 2007-05-06
Totem doesn't support DVD Menus. The hue problem (blue people) is a driver setting. Could be a number of things from not using XV and/or not turning on video overlay, poor Linux driver support (ATI), improper settings in xorg.conf (bad modelines, improper vertical and horizontal refresh rates defined), incorrect/conflicting/too many codecs installed, any combination or none of those (meaning just flakey Totem DVD support ;) ).

For DVD playback with menus try VLC.

---

