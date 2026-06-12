---
title: "dual-monitors at work, single monitor at home, vnc"
date: 2012-12-12
forum: Networking &amp; Wireless
---

### Post by timcredible on 2012-12-12
I have dual monitors at work, single monitor at home.  I'm using the default vino-server to access the dual monitor machine.  I'm using xtightvncviewer as the client.  It works fine, but 2 19" monitors are much wider than 1 24" monitor.  Is there a way to only display the left monitor?

Thanks.

---

### Post by dannyboy79 on 2012-12-12
not sure if vino is capable like x11vnc, but with x11vnc you can use the  -clip WxH+X+Y option so it only displays a portion of the x11 session

---

