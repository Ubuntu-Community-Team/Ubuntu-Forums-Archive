---
title: "[SOLVED] Amarok External Browser"
date: 2006-06-30
forum: Multimedia &amp; Video
---

### Post by gibbylinks on 2006-06-30
Hi,

I'm running Amarok 1.3 under XGL,Compiz with Gnome. Can I configure it to open Firefox when I click on the "Open In External Browser Icon" when viewing lyrics.

At the moment I get an error message - Could Not Launch The Browser. Could Not Find service "kfmclient"

This is a brilliant application, really impressed with it.

Cheers :o

---

### Post by pixelbunnie on 2006-07-03
Yeh..

sudo gedit /usr/share/config.kcfg/amarok.kcfg

either scroll down or search for "External Browser" (it's somewhere around the middle) and just replace "kfmclient" with "firefox"... save and restart amarok. 

:D

---

### Post by gibbylinks on 2006-07-03
Cheers Pixelbunnie,

Seems simple enough, will try it when I get home.

Thanks

---

### Post by pixelbunnie on 2006-07-03
No problem at all..

---

