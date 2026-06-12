---
title: "&quot;No URI handler for DVB&quot; message in Movie Player"
date: 2010-01-16
forum: Multimedia Software
---

### Post by SuperVectorGirl on 2010-01-16
I have a Pinnacle PCTV HD pro usb stick, and having unsuccessfully tried MythTV and every other DVB player in the repository, I was successful in getting Totem/Movie Player to load the channels (w_scan -ft -c US -k seemed to work and saved in the gstreamer folder...I think, lol!), but it won't let me play any of the channels but gives me a "No URI handler for DVB" message! What is a URI handler, and how do I resolve this? Thank you, in advance.:(

---

### Post by SuperVectorGirl on 2010-01-17
Ok, so it seems as if this is a known [bug]("https://bugs.launchpad.net/ubuntu/+source/totem/+bug/196152") in Totem/gstreamer on Launchpad, which I found doing further searching. Consequently, I had no problems scanning/loading/watching in Kaffeine, which I thought I would share in case anyone else with a similar problem reads this. :KS

---

### Post by miki4242 on 2010-01-18
There is a more recent bug for this [here]("https://bugs.launchpad.net/ubuntu/+source/gst-plugins-bad0.10/+bug/277877").

Weird stuff is going on with this. The URI handler is in the source code for the plugin, but it doesn't show up e.g. with `gst-inspect-0.10 dvbsrc`

I'm interested in this stuff myself, so I'm going to look into this some more.
If I find a fix for this I will add the package to my PPA.

Watch this space :-)

---

