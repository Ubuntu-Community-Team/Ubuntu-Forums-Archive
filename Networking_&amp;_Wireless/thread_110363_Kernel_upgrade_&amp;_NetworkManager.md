---
title: "Kernel upgrade &amp; NetworkManager"
date: 2005-12-30
forum: Networking &amp; Wireless
---

### Post by Michael Steinberg on 2005-12-30
I've been using NetworkManager on my Dell Inspiron 1150 (Broadcom WiFi card) and it's been pretty good; I had it set up so I could suspend to RAM and when I woke the computer up NetworkManager immediately connected. A few days ago I upgraded the kernel to 2.6.12.16.1 and from then on networking got disconnected whenever I suspended. I had to use the Networking panel instead & this killed NetworkManager. To connect to a new network most times had to reboot.

Instead of messing around any more I forced a downgrade to the previous kernel (2.6.12.16) and everything was fine again.

Anyone else have this problem? Any suggestions to avoid it in the next upgrade?

Michael Steinberg

---

