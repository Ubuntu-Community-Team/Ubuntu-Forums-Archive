---
title: "gstreamer ripping tool to decode/encode propretary formats"
date: 2008-11-09
forum: Multimedia Software
---

### Post by marco.pallotta on 2008-11-09
I'm searching for a gstreamer ripping tool to decode/encode propretary formats (mp3, divx, mpeg2, mpeg4, etc). Thoggen is a great tool but only for ogg.
Moreover if one user buys fluendo codecs it needs only gstreamer compliant apps to decode/encode propretary formats (he couldn't use acidrip, dvdrip, etc). 

At last, What about a gstreamer dvd authoring software?

P.S. I already posted this question to launchpad ([https://answers.launchpad.net/ubuntu/+question/48815](https://answers.launchpad.net/ubuntu/+question/48815)) but with no replies. I hope you can help me.

---

### Post by hansdown on 2008-11-09
Hi marco.pallotta.

For music, you could try k3b. For dvd, try dvdauthor.
Go to system> administration> synaptic package manager.
Search for your choice.

---

### Post by marco.pallotta on 2008-11-09
hansdown, are you sure does k3b and dvdauthor support gstreamer backend? It doesn't seem they do it.
Moreover does k3b support audio and video ripping? I know it only can rip .cda to mp3, burn cd and dvd, and it can be used as dvd authoring software, but not ripping, for example, .avi to divx, .avi to mpeg, and so on as acidrip (and others) can do.

---

### Post by hansdown on 2008-11-09
Ultamatix might be what you're looking for.

[http://news.softpedia.com/news/Ultamatix-The-New-Automatix-90801.shtml](http://news.softpedia.com/news/Ultamatix-The-New-Automatix-90801.shtml)

Gstreamer plugins provide the codecs for audio and video, so by all means install them from the add and remove.

---

### Post by marco.pallotta on 2008-11-09
Hansdown,

I have read what Ultamatix can do but it doesn't seem to be what I'm searching for as it is a sort of simpler synaptic but it's not a ripping or authoring tool that support gstreamer backend. It can install devede, dvd ripping, dvd styler, firefox, and so on but all of them can be already installed via Synaptic and, for the moment, I don't search for a replacement of this last.

---

