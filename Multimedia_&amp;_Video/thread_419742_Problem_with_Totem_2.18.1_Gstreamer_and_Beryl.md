---
title: "Problem with Totem 2.18.1 Gstreamer and Beryl"
date: 2007-04-23
forum: Multimedia &amp; Video
---

### Post by Shattapp on 2007-04-23
Does anyone else has the same problem as I do with Totem 2.18.1 with Gstreamer 0.10.12 and Beryl. When I have Beryl loaded I can't watch any movies with Totem. Nothing is shown in the "movie"-window. If I unload Beryl, the picture gets back. 

I tried using Totem with Xine-lib instead and that worked fine. But with xine-lib I get alot of buffering when playing movies from the network. That works fine when using Gstreamer. 

My computer is a V3405 Fujitsu-Siemens with a Intel940/945 vga-card.

---

### Post by stanna on 2007-04-25
i have the same issue with my laptop, i dont have this problem with my desktop tho, but its a completly different machine, so im not sure what the problem is.. i havnt tried to play movies over the network yet with xine, but ill give that a shot.

---

### Post by Stex on 2007-05-04
It's to do with the default video output for gstreamer, doesn't seem to autodetect properly through beryl sometimes. You may be able to fix it using the gstreamer config tool, run the command (Alt+f2): **gstreamer-properties**
In the video tab, change the default output plugin. I fixed this issue on my laptop by using **X Window System (No Xv)**

I also have an intel graphics card, anyone suppose this is a factor?

---

### Post by stanna on 2007-05-06
that worked for me, thanks a million stex!

---

### Post by Shattapp on 2007-05-12
> **Stex said:**
> It's to do with the default video output for gstreamer, doesn't seem to autodetect properly through beryl sometimes. You may be able to fix it using the gstreamer config tool, run the command (Alt+f2): **gstreamer-properties**
In the video tab, change the default output plugin. I fixed this issue on my laptop by using **X Window System (No Xv)**

I also have an intel graphics card, anyone suppose this is a factor?

Worked for me as well. Thanx a bunch for this...

---

