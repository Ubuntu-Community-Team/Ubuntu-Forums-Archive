---
title: "Via S3 UniChrome drivers? Ubuntu 6.06"
date: 2006-06-17
forum: Multimedia &amp; Video
---

### Post by Arbiter on 2006-06-17
Hi all, I just slapped together a new linux box and I've been trying to iron out some of the problems.  Pretty much everything works except the graphics chip.  I'm not quite sure what to do.  I'm using an MSI PM8M-V mATX motherboard that has VIA UniChrome integrated graphics.  In my xorg.conf file, it just says "vesa" under the driver name thing.

---

### Post by MetalMusicAddict on 2006-06-17
Im sorry I cant help but I wanna know also. I plan on building a mini-ITX system and I *think* it uses the same chipset.

---

### Post by Tomy on 2006-06-19
[quote=Arbiter]Hi all, I just slapped together a new linux box and I've been trying to iron out some of the problems. Pretty much everything works except the graphics chip. I'm not quite sure what to do. I'm using an MSI PM8M-V mATX motherboard that has VIA UniChrome integrated graphics. In my xorg.conf file, it just says "vesa" under the driver name thing.[/quote]

Here is my "Device" section from xorg.conf for the Unichrome Pro ( other than the Identifier it is the same on a box that has only the Unichrome IGP).

Section "Device"
        Identifier      "VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter"
        Driver          "via"
        BusID           "PCI:1:0:0"
        Option          "DisableIRQ"
        Option          "EnableAGPDMA"
EndSection

good luck 
Tomy

---

### Post by linuxtoindia on 2008-03-18
[COLOR="DimGray"]WE DONT HAVE MUCH SUPPORT FOR VIA CARDS AND CHIPSETS IN LINUX!
BADLUCK! WE CANT MAKE THE BEST OF IT! WELL THIS IS JUST A DRAWBACK![/COLOR]

---

