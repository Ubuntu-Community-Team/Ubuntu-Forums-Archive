---
title: "wireless networks not detected"
date: 2009-10-23
forum: Networking &amp; Wireless
---

### Post by Cozze on 2009-10-23
hi

I just installed ubuntu 9.04 in dual boot with vista.

When I try to connect wireless to the web (right click on the icon, select wireless tab)ubuntu doesn't recognize/find/show any wireless networks. Is there a way to refresh the wireless network list? I don't have the problem in Vista;

thanks for your help. Cozze

---

### Post by mikewhatever on 2009-10-23
If the hardware isn't functional, there is no way to refresh. Please post the output of the following commands to show the hardware:

lspci

sudo lshw -C network

---

### Post by Cozze on 2009-11-01
problem solved.

Tx, Cozze

---

