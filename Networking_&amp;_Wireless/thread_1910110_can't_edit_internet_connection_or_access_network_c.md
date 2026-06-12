---
title: "can't edit internet connection or access network connection in 11.10"
date: 2012-01-16
forum: Networking &amp; Wireless
---

### Post by JasonR on 2012-01-16
Been using 11.10 xubuntu for a few months successfully.  All of a sudden, I can't edit my wireless connection through the panel icon.  Also, I can't access the network connection settings through the application menu. The choices aren't grayed out, but clicking on them does nothing.  **I do have wireless**.  Oddly, though, my network panel icon indicates that wireless is disconnected. I don't recall changing any settings.  Any ideas? :confused:

---

### Post by praseodym on 2012-01-16
Try

> gksu nm-connection-editor

---

### Post by JasonR on 2012-01-16
Thanks for the reply.  This is what I get: 

** (nm-connection-editor:8211): WARNING **: Failed to initialize the UI, exiting...
ice-wwan' not present in theme


I figured the default XFCE network manager is not working, so I installed Wicd using Synaptic.  I can edit my connection now, but I still can't figure out the problem with the other manager.  Actually, I like Wicd better, but I'd like to know what's going on.

---

