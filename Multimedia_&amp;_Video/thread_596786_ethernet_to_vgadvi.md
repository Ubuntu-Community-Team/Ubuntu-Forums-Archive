---
title: "ethernet to vga/dvi"
date: 2007-10-29
forum: Multimedia &amp; Video
---

### Post by cobaltcopy on 2007-10-29
Hi, this might be a really specialized question, but here goes:

I work at a museum and we have 15 or so kiosks that run touchscreens and display video on Windows embedded. The kiosks are continually having problems - rebooting, etc. I am researching the possibility of having one machine driving all the kiosks without thin clients.

Is it possible to run multiple x11 sessions and stream those sessions over ethernet and be converted to dvi/vga at the kiosk via a rtp box? I know that there are adapter boxes that allow you to take vga into an adapter box, multicast/unicast it over an IP network and then convert it to vga at the display. What I want is to take rtp straight out of the server and convert it to vga at the kiosk - simultaneously for 15 sessions.

Is it even possible to take 15 or so x11 sessions and unicast it over ethernet? You can't have multiple x11 sessions that each run vga because it take 15 vga ports.

It might be simpler just to buy 15 mini-itx boards and run linux on them. [The apps are in flash]

---

