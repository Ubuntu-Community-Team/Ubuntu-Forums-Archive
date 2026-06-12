---
title: "Canon mp560 wifi problem"
date: 2012-10-31
forum: Networking &amp; Wireless
---

### Post by Notasoddingclue on 2012-10-31
Trying to connect the Canon mp560 printer to this Toshiba laptop so I can remotely print files for my employer.

Tried going through router but there seems to be a point that I am missing.  The laptop has wifi as I am connected to the netgear hub but there is no connection to the printer.

Any help please?

---

### Post by pdc on 2012-10-31
I'm not clear about your hardware setup;

.........I think you need a Canon driver to print with the MP560;

for that go here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100236502.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100236502.html)

to download MP560 series IJ Printer Driver Ver. 3.20 for Linux (debian Packagearchive)

it comes down as a .tar.gz file ........... [COLOR="SeaGreen"]**cnijfilter-mp560series-3.20-1-i386-deb.tar.gz**[/COLOR]

if you download it and save it; (it should be saved in your Downloads directory); the commands would be

> [COLOR="Red"]cd Downloads[/COLOR]

>  [COLOR="Red"]tar -zxvf cnijfilter-mp560series-3.20-1-i386-deb.tar.gz[/COLOR]

> [COLOR="Red"]cd cnijfilter-mp560series-3.20-1-i386-deb[/COLOR]

> [COLOR="Red"]./install.sh[/COLOR]

...........the install may ask you if you want usb or wifi connection: you might find usb easiest......if it is physically possible

---

