---
title: "totem"
date: 2008-04-18
forum: Multimedia &amp; Video
---

### Post by manicmailman on 2008-04-18
hey why is it that totem thinks i have a cd in the player when a dvd is in... it also cant get the menu goin...

---

### Post by nicedude on 2008-04-19
Try using vlc player instead of totem. It worked for me.

---

### Post by cor2y on 2008-04-19
if its gutsy totem-gstreamer was broken in it for dvd playback.
Try installing totem-xine instead and see how that works.
Also totem-gstreamer (the default player for ubuntu) does not/cannot handle dvd menu navigation only totem-xine can.
Just look for it in synaptic using the search function or ```
 sudo apt-get install totem-xine
``` it will automatically remove totem-gstreamer and install totem-xine, then try dvd playback again.

---

### Post by manicmailman on 2008-04-19
k i got the new player... or rather different version of totem but now it says that it doesnt have the proper codecs to play it...

---

### Post by cor2y on 2008-04-19
add the medibuntu repos
```
https://help.ubuntu.com/community/Medibuntu
```
update the source list, and then install libdvdcss2 libdvdread, libdvdnav then try again.

---

