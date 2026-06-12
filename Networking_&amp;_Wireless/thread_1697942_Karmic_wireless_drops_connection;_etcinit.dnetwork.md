---
title: "Karmic wireless drops connection; /etc/init.d/networking restart does nothing"
date: 2011-03-01
forum: Networking &amp; Wireless
---

### Post by Moozillaaa on 2011-03-01
Karmic occasionally drops the wireless connection, with the machine in the same room as the router. 

Executing **/etc/init.d/networking restart** returns '**Ignoring unknown interface wlan0=wlan0**', and that's the wireless interface I use.

iwlist scan for ***THAT*** interface shows my router's signal, and the neighbors' too...

I haven't found a process to restart, which controls 'init.d' (which I'm guessing I have to do???)

Thanks...

edit:
Is this correct:
> Apparently Network Manager in karmic only allows your wifi to activate upon logging in to Gnome or KDE (not sure if this is a bug or what).

---

