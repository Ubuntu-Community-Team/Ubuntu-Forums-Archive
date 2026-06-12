---
title: "How to WOL from Hibernate or sleep ubuntu 12.04 minimal server"
date: 2012-05-30
forum: Networking &amp; Wireless
---

### Post by microchef on 2012-05-30
Hi How do i  WOL wake from Hibernate or sleep? on my server Ubuntu 12.04 minimal installation
 if i pm-suspend or pm-hibernate then i cannot wake from a magic packet, however if I shutdown -h now I can wake the server

Huh? why?

---

### Post by Sularco on 2012-06-01
I believe that is part of the hardware specifications for WOL. Only if the machine is in shutdown state will the network card be set to listen for the magic packet on broadcast. Suspend or hibernate won't, unless your MoBo or network card manual says otherwise.
I just tried mine out of curiosity (Gigabyte 890GPA) and it will wake from shutdown immediately, but not from suspend or hibernate.

---

