---
title: "jumpy video in firefox"
date: 2008-03-16
forum: Multimedia &amp; Video
---

### Post by thischarmingman on 2008-03-16
Hi

Recently I've had problems with video playback in the firefox browser. Horizontal lines would appear on the video, very noticeable whenever there is quick moving shots. I don't think this is a video card error as when watching dvds in totem or any other player it is fine. Any ideas as to what might be the problem?

Thanks

---

### Post by xc3RnbFO8P on 2008-03-16
What are the specifications of your computer?

---

### Post by thischarmingman on 2008-03-16
> **Ringi said:**
> What are the specifications of your computer?

Its an IBM T40 thinkpad - ATI radeon 7500, 1 GB RAM, 1.5mhz intel pentium m. In a previous install of ubuntu, videos in firefox worked fine so I know my laptop is capable

---

### Post by xc3RnbFO8P on 2008-03-16
Did you install w32 codec

---

### Post by thischarmingman on 2008-03-16
> **Ringi said:**
> Did you install w32 codec

Yes, as well as the mediaplayer connectivity plugin. Neither have worked. Does the w32 codec need to be configured in any way or should firefox automatically recognise it?

---

### Post by xc3RnbFO8P on 2008-03-16
No, just try to install it again:
> wget -c [http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu1_i386.deb](http://packages.medibuntu.org/pool/non-free/w/w32codecs/w32codecs_20071007-0medibuntu1_i386.deb)
sudo dpkg -i w32codecs_20071007-0medibuntu1_i386.deb
And in Mediaplayerconnectivity> configure,  try to change player (vlc if you got it installed)

---

### Post by thischarmingman on 2008-03-16
> **Ringi said:**
> No, just try to install it again:

And in Mediaplayerconnectivity> configure,  try to change player (vlc if you got it installed)

Tried that, still the same. I've tried to use opera but it doesnt even allow me to view videos. Help!

---

### Post by kerry_s on 2008-03-16
> **thischarmingman said:**
> Hi

Recently I've had problems with video playback in the firefox browser. Horizontal lines would appear on the video, very noticeable whenever there is quick moving shots. I don't think this is a video card error as when watching dvds in totem or any other player it is fine. Any ideas as to what might be the problem?

Thanks

is it just on a certain site or all sites? some sites just suck, can't be helped, it's there fault, not your players.

also make sure you don't have competing plug ins trying to play the same format.
type ```
about:plugins
``` in your browser to see the plugins.

---

### Post by thischarmingman on 2008-03-16
> **kerry_s said:**
> is it just on a certain site or all sites? some sites just suck, can't be helped, it's there fault, not your players.

also make sure you don't have competing plug ins trying to play the same format.
type ```
about:plugins
``` in your browser to see the plugins.

It happens on all sites. How do I know if there are conflicting plug-ins in the list that is generated?

---

