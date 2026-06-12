---
title: "Ati 9600 XT + fglrx + Xine Xv problems"
date: 2006-07-11
forum: Multimedia &amp; Video
---

### Post by Pitou on 2006-07-11
Hello,

I'm trying to setup my ATI card in mirror mode to have same screen on 2 monitors. (in fact, one standard CRT monitor and a Sanyo Z2 projector)

I'm using 8.25.18 drivers (the one in repository)

Here is what I did:

aticonfig --initial --input=/etc/X11/xorg.conf
aticonfig --dtop=mirror --input=/etc/X11/xorg.conf

So far everything works fine except for Xine that gives me this error message:

video_out_xv: Xv extension is present but I couldn't find a usable yuv12 port.
              Looks like your graphics hardware driver doesn't support Xv?!

It works, if I specify "opengl" or "xshm" as the video driver, but would prefer Xv.

Any idea?

Thank you.

Pitou!

---

### Post by Pitou on 2006-07-11
Found the solution,

Forgot to do:

sudo aticonfig --overlay-type=Xv

Pitou!

---

