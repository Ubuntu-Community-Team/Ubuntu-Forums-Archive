---
title: "I can't play m3u streaming audio"
date: 2006-08-11
forum: Multimedia &amp; Video
---

### Post by westood on 2006-08-11
I can't play m3u streaming audio

---

### Post by kaffelars on 2006-08-11
It's not possible to know what may be wrong when you don't say *anything* except stating the fact that you can't play m3u streaming audio :-$

---

### Post by Autoclamp on 2006-08-28
If your problem is the same one I had (m3u files don't play in Totem when accessed through a link in Firefox), you may want to try downloading the totem-gstreamer-firefox-plugin.

To do this, go through these menus: Applications > Add/Remove... > Advanced. Click the search button, and put totem-gstreamer-firefox-plugin into the search bar. The package should appear in the area below. Click on the box next to the package title, and choose "Mark for Installation." Click "Apply," and you should be good to go! Well, it worked for me anyway.

Or, if you're comfortable with the command line, you can open up a terminal and enter:

sudo apt-get install totem-gstreamer-firefox-plugin

And Kaffelars-- since when do we shush newbies? :o

---

