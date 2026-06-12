---
title: "Android tablet bypassing proxy"
date: 2011-04-27
forum: Networking &amp; Wireless
---

### Post by dbclinton on 2011-04-27
I know this isn't directly related to Ubuntu (even if the rest of my network is pure Ubuntu!), but I haven't had any luck uncovering this info through the usual channels. 
Does anyone know which port Android 2.2 on a VIA wm8650 uses to access the Internet? My Wifi is routed through a Linux firewall (Ipcop) which forces normal outbound Internet traffic via normal ports (80, 8080 etc) through the ipcop proxy, but the wm8650 somehow bypasses the proxy. I don't know whether I'm just missing the port the tablet is actually using.
Thanks,
David

---

### Post by dbclinton on 2011-05-19
Turns out that the reason the tablet was getting past my proxy had nothing to do with Android - it was because my firewall's iptable file had somehow become corrupted. :oops:

---

