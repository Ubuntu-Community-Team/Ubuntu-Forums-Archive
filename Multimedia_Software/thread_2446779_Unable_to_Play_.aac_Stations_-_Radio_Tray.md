---
title: "Unable to Play .aac Stations - Radio Tray"
date: 2020-07-06
forum: Multimedia Software
---

### Post by jneill on 2020-07-06
Using Radio Tray 0.7.3 on 32-bit Ubuntu 14.04 (it&#8217;s an old under-powered machine); python-gst 0.10.
 
With several .aac stations I get the following:
 
[FONT=arial]gstsouphttpsrc.c(924):
gst_soup_http_src_finished_cb ():/
[/FONT][FONT=arial][COLOR=#172B4D]GstPlayBin2:player/[/COLOR][/FONT][FONT=arial]
GstURIDecodeBin:uridecodebin0/
GstSoupHTTPSrc:source:
libsoup status code 8[/FONT]
 
What am I missing?

---

### Post by CelticWarrior on 2020-07-07
Welcome.

>  What am I missing? 				
You're missing an upgrade to a supported version. 14.04 is out of support since last year and shouldn't be used.
We won't help you with an obsolete release.

---

### Post by mc4man on 2020-07-08
Well 14.04 is actually still supported to some extent (all Main repo) see screen for updates pending here, (haven't booted to in a couple of months) so...
Anyway radiotray plays a known aac stream fine here so not sure. Maybe add one of the aac streams from here to test., they work well here.
[https://radioparadise.com/listen/stream-links](https://radioparadise.com/listen/stream-links)

---

### Post by jneill on 2020-07-09
Radiotray handles many aac streams, but there are several that error, for instance: [http://34.83.38.54/mwfmadison-wrisfmaac-ibc3](http://34.83.38.54/mwfmadison-wrisfmaac-ibc3)  or   [http://34.83.202.216/townsquare-wxxqfmaac-ibc3](http://34.83.202.216/townsquare-wxxqfmaac-ibc3)

---

### Post by mc4man on 2020-07-09
> **jneill said:**
> Radiotray handles many aac streams, but there are several that error, for instance: [http://34.83.38.54/mwfmadison-wrisfmaac-ibc3](http://34.83.38.54/mwfmadison-wrisfmaac-ibc3)  or   [http://34.83.202.216/townsquare-wxxqfmaac-ibc3](http://34.83.202.216/townsquare-wxxqfmaac-ibc3)
gstreamer doesn't handle those type of url/streams, not back then, not now. (views as a corrupt url
Even if a bug and fixable will obviously never happen for gst-0.10..

Use any non gstreamer player or a browser, they'll play back fine.

(- extended security support for 14.04 thru 2022, free to regular users

[https://ubuntu.com/esm](https://ubuntu.com/esm)
(scroll to bottom of page

---

