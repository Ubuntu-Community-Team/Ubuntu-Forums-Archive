---
title: "Video Playback Laggy (VLC, .avi or .mkv)"
date: 2011-05-03
forum: Multimedia Software
---

### Post by Dubslow on 2011-05-03
Hey guys,
Just got a bunch of movies from a friend. Tried to play a HD Star Wars .mkv with VLC, but it was pretty clearly lagging. Then I tried a Disney movie from 1963 as a .avi, but that appeared to lag too, and I don't think it's the movie. I'm pretty positive that I have the capability to play HD movies. I can play a 256x256 Minecraft texture pack still at maxed out graphics with no lag.

AMD Phenom II X6 1055T Thuban _2.8GHz 6 x 512KB L2 Cache_ 6MB L3 Cache Socket AM3 125W _Six-Core_ Desktop Processor HDT55TFBGRBOX

_GeForce GTX 460 (Fermi) 768MB 192-bit GDDR5 PCI Express 2.0 x16 HDCP Ready SLI Support Video Card_

_8 GB of RAM_

I have installed the restricted NVIDIA drivers as Ubuntu requested on install.

(Still running 10.10 Maverick)

What can I do? Am I missing some codecs?

---

### Post by handy on 2011-05-03
You've done the Restricted Formats thing:

[https://help.ubuntu.com/community/RestrictedFormats/#Playing%20Restricted%20Formats](https://help.ubuntu.com/community/RestrictedFormats/#Playing%20Restricted%20Formats)

& it sounds like you must already have libdvdcss2 & such:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Dubslow on 2011-05-03
I got the dvd thing working (I had previously tried to install that package with apt-get but it hadn't worked) but I already had the restricted extras. As for the .mkv, it went much better after I killed the Minecraft server I had running, as well as compiz. Compiz was taking half of my CPU, and killing that made the video run fine. On the other hand, it seems like I should be able to run compiz and HD .mkv's at the same time.

---

### Post by handy on 2011-05-04
I haven't had problems with watching videos for very many months now. & I have been using the -git AMD/ATi open-source driver stack & kernel now for well over 18 months.

Though, I must say, I NEVER use Compiz or the like, for two reasons: Primarily I don't use a DE, & I'm not interested in those pretties. Secondarily, such 3D desktop stuff just seems like a terribly inefficient waste of system resources to me.

When I say that, I'm not making a personal judgement, it is just the way I see it, & in reality I'm just a boring old fart. :)

---

