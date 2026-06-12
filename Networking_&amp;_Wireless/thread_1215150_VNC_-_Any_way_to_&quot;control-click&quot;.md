---
title: "VNC - Any way to &quot;control-click&quot; ?"
date: 2009-07-16
forum: Networking &amp; Wireless
---

### Post by nowhere@cox.net on 2009-07-16
Hey all,

I'm connecting to a mac from my Ubuntu laptop and trying to do some development work in Xcode and Interface Builder, the latter requiring a "control-click and drag" operation quite frequently. 

I've tried several vnc clients in succession trying to find one that is fast enough to actually do some work and one that transmits the required key/mouse event above. Here's a bit of results. Note that even the fastest below doesn't even come close to using NX ubuntu to ubuntu.

[LIST]
[*]vinagre is unusably slow, period. Dragging a small window across the desktop results in a window repaint every 1 second or so.
[*]tightvnc is fast enough but the interface is terrible, it doesn't play well with compiz on my laptop, and occassionally will not respond to F8 when in fullscreen mode so I cannot quit.
[*]grdc (0.6) is nearly perfect. Nice speed, great interface, built-in tunnel support, SCALED VIEWING!!! but it doesn't transmit the "control click" sequence I need.
[/LIST]

Any ideas? Think this is something to do with Mac Leopard VNC implementation? There's no preference referring to it and it does work mac to mac...


I hope this is ok to post since I am really asking about ubuntu vnc clients and if anyone knows one that works with the mac server.

Thanks!

---

### Post by nixscripter on 2009-07-29
I use xvncviewer (available in Synaptic Package manger) and use Control-click on a Mac just fine. Give it a try.

---

### Post by nowhere@cox.net on 2009-08-10
Thank Nix,

but I tried xvncviewer second,  following the default vinagre. It was unusably slow, the F8 popup thingy would not come up very very often and if in fullscreen mode I had to blow X away to get out of it.

Finally found gdrc which is very polished except for the control click thingy. It also loses connection occasionally but a simple click on the disconnect and connect buttons and I am back in super fast.

I love how ssh tunneling is integrated into it as well...

Thanks anyway though. I always appreciate someone taking the time to post...

---

