---
title: "Internet Connection Sharing"
date: 2010-06-26
forum: Networking &amp; Wireless
---

### Post by tm-chex on 2010-06-26
I am trying to Enable Internet Connection sharing In Ubuntu 10.14 through firestarter so I can get my Xbox on to the internet, and I have the devices configured properly, but everytime I try to plug in the Xbox the operating system disconnects me from the internet, Ignores the wireless network, and tries to connect to the internet through the Xbox, is there a way to make it connect through wireless only, even when a networking cable is connected?

---

### Post by marshmallow1304 on 2010-06-26
Assuming you are using 10.04 (there is no 10.14), close Firestarter, then open System->Preferences->Network Connections.  Select your wired connection (probably eth0) and click "Edit".  On the "IPv4 Settings" tab, set "Method" to "Shared to other computers".  Apply and close then attach the Xbox.  Remember to set it back if you need the wired connection for anything else.

---

### Post by tm-chex on 2010-06-26
thanks. and How can I modify the connection setting on eth0 for static IP, or What numbers should I enter in the Xbox to get it to work?

---

