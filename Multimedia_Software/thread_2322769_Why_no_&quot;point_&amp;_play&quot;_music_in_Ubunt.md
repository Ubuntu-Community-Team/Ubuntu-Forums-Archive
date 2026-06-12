---
title: "Why no &quot;point &amp; play&quot; music in Ubuntu"
date: 2016-04-30
forum: Multimedia Software
---

### Post by joverstreet1 on 2016-04-30
Why is it that MP3s can be played in Linux Mint Mate version by simply putting the mouse pointer on the MP3 file but this does not work (have to double click on MP3 file and Banshee application is then opened) on Ubuntu even on the Mate version 16.04 or any other version, i.e. what allows Linux Mint Mate to do this while Ubuntu does not ?

Thanks.

---

### Post by mc4man on 2016-04-30
quite a ways back totem had an audio preview for nautilus. That was dropped upstream for gnome-sushi which previews both audio & video
(highlight file > press space bar.
Mate must have created the own version of what was totem-audio-preview. So figure out what package installs it & put on your install

---

### Post by joverstreet1 on 2016-04-30
> **mc4man said:**
> quite a ways back totem had an audio preview for nautilus. That was dropped upstream for gnome-sushi which previews both audio & video
(highlight file > press space bar.
Mate must have created the own version of what was totem-audio-preview. So figure out what package installs it & put on your install

I searched Synaptic for all of the names that you mentioned but I found no installed matches.

Could this have something to do with "Gstreamer" applications ?

Thanks.

---

### Post by mc4man on 2016-04-30
What mate is using likely isn't in Ubuntu repos, maybe they have their own or it's just part of their install. You'd have to ask them
In ubuntu the package is called gnome-sushi, shown in screen on an audio file. (timeline shows on cursor movement, then fades, ect

---

### Post by Dennis N on 2016-04-30
> what allows Linux Mint Mate to do this while Ubuntu does not ?

I believe MATE uses the **gstreamer** plugin called **playbin** to handle the playback on mouseover.  I suppose you can look that up on the web for more details. It is working in Ubuntu MATE 16.04.

---

### Post by mcduck on 2016-05-03
Doesn't Mate also use it's own file manager? You'd probably need that as well instead of using Nautilus...

---

