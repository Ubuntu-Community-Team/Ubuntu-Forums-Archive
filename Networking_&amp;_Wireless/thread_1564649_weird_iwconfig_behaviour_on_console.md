---
title: "weird iwconfig behaviour on console"
date: 2010-08-30
forum: Networking &amp; Wireless
---

### Post by joeybernard on 2010-08-30
OK.  I haven't been able to find any information on what may be happening here, so I figured I would ask.  If I try and set the ESSID on my wireless interface from the console with iwconfig, it gets set to some very strange escaped characters, almost like unicode escaped characters.  If I then start up X11 and try the same thing in an xterm, iwconfig accepts the ESSID and sets it correctly.  I haven't been able to figure out why that works, and the console doesn't.  It also does the same thing if I ssh into the box and try to set the ESSID.  It comes out garbled, looking like

"\d2\sd\xx\xx\xx"

rather than

"mynet"

Why does this work fine in an xterm under X11?  I'm out of ideas.

Joey

---

