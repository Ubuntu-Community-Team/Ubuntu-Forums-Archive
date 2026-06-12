---
title: "X-org editing  ATI board"
date: 2007-12-29
forum: Multimedia &amp; Video
---

### Post by saspo on 2007-12-29
[COLOR="Red"]Section "Device"

        Identifier      "Intel Corporation 82865G Integrated Graphics Controlle$

        Driver          "intel"

        BusID           "PCI:0:2:0"[/COLOR]

When I get into x-org, I get the above, in Red.  I want to install a board from Diamond Multimedia w ATI  Radeon 7000.  Will the entry below, in blue,  be ok?


[COLOR="Blue"]Section "Device"

        Identifier      "ATI Radeon 7000  Graphics Processing Unit"

        Driver          "ati"

        BusID           "PCI:0:2:0"[/COLOR]

---

