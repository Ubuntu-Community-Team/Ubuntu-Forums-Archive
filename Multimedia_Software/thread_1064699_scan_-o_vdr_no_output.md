---
title: "scan -o vdr no output"
date: 2009-02-09
forum: Multimedia Software
---

### Post by AntsaRTF on 2009-02-09
Hi,

I've been trying to install vdr on my debian etch server. I have my dvb-t card installed and configured. When I scan for the channels, the scan command finds them, and if I use the default attributes (with out -o vdr) it writes them out on screen/file. But when I use the -o vdr attribute to produce vdr format, it finds the channels, but doesnt give anykind of output. At the end of executing scan, it says:

dumping lists (19 services)
Done.

Just as it should. But it doesn't produce anything to screeen or file Sad

Can anyone give any advice... or maybe give me Turku, Finland dvb-t channels.conf Very Happy

---

### Post by steefjeqv on 2009-02-14
Hi,

You can use the pipe command :

sudo your/scan/command > /var/lib/vdr/channels.conf

If you're interested, there is an updated repository for Ubuntu 8.10, maintained by e-tobi and hanno :

[http://www.hanno.de/blog/category/vdr/]("http://www.hanno.de/blog/category/vdr/")

Greetings,
Steven

---

