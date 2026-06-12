---
title: "[SOLVED] Kaffeine + video playback + DVB problem"
date: 2007-10-18
forum: Multimedia &amp; Video
---

### Post by Rusna on 2007-10-18
Hi,

I have a problem with fresh baked Ubuntu 7.10 Gutsy Gibbon.

I have a DVB-C card which I want to use with Kaffeine. And other multimedia files I want to play with Mplay/Rhythmbox.

When I have done a fresh clean install and only installed Mercurial DVB drivers and set up Kaffeine to work with DVB it works great.
But if I open a random video file with for example Totem and it downloads the suitable codecs it at the same time messes my Kaffeine, from this point on I only get a slice of the DVB picture I'm supposed to have.

Here's a screenshot 
[IMG]http://users.utu.fi/tjrepo/pictures/Screenshot.png[/IMG]

The tiny slice of the picture is correct, but it's only a slice!

Even if after a re-install I install Mplayer and do not run it, it breaks the Kaffeine output.
If I try to install gstreamer codecs, Kaffeine breaks
If I try to install Amarok, Kaffeine breaks

I cannot do a one freaking thing without Kaffeine breaking! I've now done about ten re-installs and still haven't found the way out.

Please help me out!

---

### Post by Rusna on 2007-10-21
Problem is solved. FGLRX caused the problem, ever since I switched back to ati driver, everything works great.

---

