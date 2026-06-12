---
title: "Sound issues when logging in after xorg update..."
date: 2006-08-24
forum: Multimedia &amp; Video
---

### Post by anthonysales on 2006-08-24
Hello all...I'm currently having sound issues with my system. After doing an upgrading my xorg, my sound got messed up whenever I log in. When GDM starts up and the login screen appears, I get sound coz I can hear the bongos, but when I log in, my sound goes away and I get an error by the sound icon saying "No volume controls GStreamer plugins and/or devices not found."  When i run lsmod, I can see that the module for my sound device is there in the list.  Can anyone help me? my specs are:

AMD Athlon 64 X2 4200+
MSI K8N Neo4-F
Onboard sound (AC'97)

Thanks to anyone who replies. =)

---

### Post by anthonysales on 2006-08-25
got it! hehehe..just had to add my user to the "audio" group! sound works noW :D

---

