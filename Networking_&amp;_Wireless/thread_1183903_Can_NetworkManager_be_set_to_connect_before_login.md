---
title: "Can NetworkManager be set to connect before login?"
date: 2009-06-10
forum: Networking &amp; Wireless
---

### Post by yenrab on 2009-06-10
Is it possible to configure NetworkManager to connect to my home network as part of the start up process?

At present it connects when I log in to gnome, presumably initiated by nm-applet. If I log in as another user I get prompted for the wireless network key.

I would prefer networkmanager to connect automatically so that programs like fetchmail, sshd and apache can work, and all user accounts get network access. Is this possible? It seems like the Right Thing? The nm-applet would then just be used to display the current status and to change to different network settings.

---

### Post by Iowan on 2009-06-10
I saw another thread that suggested boot-time activation would need to be done via* /etc/network/interfaces* - rather than NM

---

