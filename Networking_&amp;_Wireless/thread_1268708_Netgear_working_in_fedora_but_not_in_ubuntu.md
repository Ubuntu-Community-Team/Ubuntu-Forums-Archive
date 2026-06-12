---
title: "Netgear working in fedora but not in ubuntu"
date: 2009-09-17
forum: Networking &amp; Wireless
---

### Post by sonu 1807 on 2009-09-17
I hava a  NetGear, Inc. WG111v3 54 Mbps Wireless adapter which is working fine in Fedora 11 out of box. In the same desktop, ubuntu jaunty (64-bit) recognizes it and event connects to internet but I can not surf as the connection remains virtually dead. In fedora, I get great speed. The network applet shows good signal strength in both. It is very puzzling for me. Because of that I am forced to use fedora in spite of my liking of ubuntu over it. 

Plz help!

---

### Post by uylug on 2009-09-17
> **sonu 1807 said:**
> I hava a  NetGear, Inc. WG111v3 54 Mbps Wireless adapter which is working fine in Fedora 11 out of box. In the same desktop, ubuntu jaunty (64-bit) recognizes it and event connects to internet but I can not surf as the connection remains virtually dead. In fedora, I get great speed. The network applet shows good signal strength in both. It is very puzzling for me. Because of that I am forced to use fedora in spite of my liking of ubuntu over it. 

Plz help!

So, you say it is working right?

Run these comands:

```

sudo dhclient wlan0 

sudo iwconfig wlan0 retry 9999999

ping google.com
```

---

### Post by sonu 1807 on 2009-09-17
Thanx Thanx Thanx uylug ...it worked like charm....:P

---

