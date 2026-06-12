---
title: "Got rid of KNetworkManager to switch to WICD, but now have no internet.. :/"
date: 2009-12-02
forum: Networking &amp; Wireless
---

### Post by Literati on 2009-12-02
So, stupid mistake here, I was using KPackageManager to install wicd, but since both it, and I, are stupid, it told me I had to get rid of KNetworkManager first, and then install wicd. Well, obviously once I got rid of KNetworkManager, my internet went down the toiler (I can't even connect via eth0) 

So, basically, I'm wondering how I can fix this. My pc was installed via USB Stick, as it doesn't have a CD Drive. So I tried making my software sources back to the "cdrom" but obviously, it's looking for a CD when it's actually on /dev/sde...

Suggestions?

---

### Post by Literati on 2009-12-02
SOLVED:

sudo ifconfig eth0
sudo dhclient eth0

When hooked up by ethernet.

---

