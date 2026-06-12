---
title: "Canon PIXMA 5200R"
date: 2007-06-04
forum: Multimedia &amp; Video
---

### Post by GhentK on 2007-06-04
I recently installed Ubuntu (thank god Windows is off my HDD).

First complication arose tonight when I tried to add my WLAN printer, a Canon PIXMA 5200R. There are no default drivers for that model in Ubuntu, and I've only found the commercial Turboprint. Neither the 5200 nor the 5200R are thought of at linuxprinting.org (though they might be added sometime later).

Does anyone know of a free alternative? I must admit that I don't really fancy paying €30 all that much.

Thanks in advance.

---

### Post by GhentK on 2007-06-05
Bump.

Anyone?

---

### Post by FXFman1209 on 2007-06-05
I'm also looking for this solution. :(

---

### Post by endrre on 2007-06-19
hm,
i found a german guide, i do not understand the content, but anyway [http://www.linux-club.de/ftopic74287.html]("http://www.linux-club.de/ftopic74287.html")

---

### Post by kevpatts on 2007-06-19
Looking for this too. This may be a bit easier to read:
[http://translate.google.com/translate?u=http%3A%2F%2Fwww.linux-club.de%2Fftopic74287.html&langpair=de%7Cen&hl=EN&ie=UTF-8&oe=UTF-8&prev=%2Flanguage_tools](http://translate.google.com/translate?u=http%3A%2F%2Fwww.linux-club.de%2Fftopic74287.html&langpair=de%7Cen&hl=EN&ie=UTF-8&oe=UTF-8&prev=%2Flanguage_tools)

---

### Post by kevpatts on 2007-06-19
This worked perfectly for me after converting the RPM's using "sudo alien -cd <RPM package name>" for all three packages.

When installing the printer I used "TCP/Socket, HP DirectJet, RAW connection" option under "Network Printer", found the printer using the DHCP leases table on my router (printer appears as one of possibly many items under the name "*", but can be identified by doing a port scan in the Network Tools gui"). I used the expert driver in the choice of two.

Hope you have luck

---

### Post by GhentK on 2007-07-06
Thanks for the walk-through. I'll try it as soon as I get home. :)

---

### Post by kevpatts on 2007-07-06
No problem. Let me know how you get on.

---

### Post by GhentK on 2007-08-02
> **kevpatts said:**
> No problem. Let me know how you get on.

**comes back three weeks later when he has to reinstall printer**

It worked like a charm, kevpatts. Thanks very much, both of you. :D

I still have to have a Windows PC connected to the printer in order to perform certain tasks (like configuring network settings, checking ink level, etc.), though. **shakes half fist at Canon, since they at least allow Linux people to develop their own drivers**

---

