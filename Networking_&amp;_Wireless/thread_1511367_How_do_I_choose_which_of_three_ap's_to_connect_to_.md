---
title: "How do I choose which of three ap's to connect to (same ssid)?"
date: 2010-06-16
forum: Networking &amp; Wireless
---

### Post by djeikyb on 2010-06-16
I have three routers (linksys wrt54gl, ddwrt). I'm trying to use wds bridging, got two of them linked, but not the third. All three routers have the same SSID. I'm using Ubuntu 10.04 netbook remix.

My problem is I need to choose which of these my laptop connects to. Right now it connects to the one router which isn't playing nice with wds. I need it to connect to one of my other routers. I see the other signals using nm-tool, but they don't show in nm-applet. I created a connection in NetworkManager specifying the SSID + mac address of the correct router, but the tray applet doesn't show any options for connecting to manually configured networks, and I can't find any other useful app.

I suppose I could rtfm for iwconfig et al, but Ubuntu ought to have an easier way. Thanks for any help you guys can give.

---

### Post by djeikyb on 2010-06-17
Hmm. Actually I didn't find a way to mandate mac address in wpa_supplicant.conf, so I seem to be stuck for the moment. Any suggestions, whether gui or cli based?

---

