---
title: "Via driver doesn't work on VIA board (EN15000)"
date: 2006-06-05
forum: Multimedia &amp; Video
---

### Post by tsantos on 2006-06-05
I'm running Dapper on a VIA EN15000 board and I can't get the via video to work with the via driver.  I've tried to do this to my xorg.conf file:

Section "Device"
        Identifier      "VIA CN700"
         Driver          "via"
        BusID           "PCI:1:0:0"
        Option          "DisableIRQ"
        Option          "EnableAGPDMA"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "VIA CN700"
        Monitor         "VP201s"
        DefaultDepth    24
...

It tells me:

dlopen: /usr/lib/xorg/modules/extensions/libGLcore.so: undefined
symbol: __glXLastContext
(EE) Failed to load /usr/lib/xorg/modules/extensions/libGLCore.so
(EE) Failed to load module "GLcore" (loader failed, 7)
(EE) No devices detected.

If I just change the "via" to "vesa", X comes up without a hitch (other than being really slow).

Anyone have experience with this?  I fear that the video on the EN15000 may be too new for the driver but it gives me so little info when it fails that I really have no idea.

-Tom-

---

### Post by localzuk on 2006-06-05
Which is the actual graphics chipset? Take a look at [http://www.viaarena.com/default.aspx?PageID=2&OSID=20&CatID=2260](http://www.viaarena.com/default.aspx?PageID=2&OSID=20&CatID=2260) and [http://ftp.x.org/pub/X11R7.0/doc/html/via.4.html](http://ftp.x.org/pub/X11R7.0/doc/html/via.4.html) for information about using via chipsets with Xorg.

I use a CLE266 chipset with the ubuntu via driver fine.

---

### Post by tsantos on 2006-06-05
The EN15000 board has the CN700 chipset on it.

-Tom-

---

### Post by localzuk on 2006-06-05
It appears that the xorg one doesn't yet support that chipset (it doesn't support the CN400 which is earlier either).

There isn't an official via driver either. So I am afraid you are stuck with vesa until it is supported (I was stuck with vesa for a long while whilst the CLE266 was unsupported).

---

