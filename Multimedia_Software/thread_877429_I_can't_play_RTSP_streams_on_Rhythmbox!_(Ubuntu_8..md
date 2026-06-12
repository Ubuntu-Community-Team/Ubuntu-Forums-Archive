---
title: "I can't play RTSP streams on Rhythmbox! (Ubuntu 8.04 H)"
date: 2008-08-01
forum: Multimedia Software
---

### Post by eliseu_carvalho on 2008-08-01
I've been trying to play a local FM radio station into Rhythmbox, but for some reason the program gives me an error message. My Linux is in Portuguese, but it says something like:

"It wasn't possible to play - can't determine stream type"

So I changed rtsp:// to http:// and tried to play again, and I get an "unknown error" message.
I was looking at Google about playing rtsp:// streams into Rhythmbox. I found lots of things and tried them, but none worked here. And I don't want to use RealPlayer just for one radio station.
Can someone help me?

---

### Post by mythmgn on 2010-06-04
I made it working for me by this:

Installed the following packages:
libgstreamermm-0.10-2 (0.10.6-1)
libxml++2.6-2 (2.30.0-1)



Hope it helps.

---

