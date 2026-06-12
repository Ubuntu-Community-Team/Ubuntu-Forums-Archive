---
title: "flash plug-in for firefox"
date: 2009-04-12
forum: Multimedia Software
---

### Post by tmichael on 2009-04-12
I am running a Dell Inspiron Mini 9 with Ubuntu 8.04.  When I try to play videos on Hulu.com, I get a "requires Flash Player 9" error message.  Firefox tells me that I already have Flash 9 plug-in installed, but it seems that what Firefox actually uses is a plug-in called Swfdec 0.6.0 (I found this out by right-clicking on the flash content).  How can I get Firefox to actually use the Flash plug-in?

---

### Post by gandaran on 2009-04-12
remove the swfdec completely (use synaptic package manager) and keep only adobe flash installed.

---

### Post by SKLP on 2009-04-12
Remove the package swfdec-mozilla, and install the flashplugin-nonfree package.

---

### Post by tmichael on 2009-04-12
Thanks to gandaran and SKLP--Problem solved!

---

