---
title: "Could I Run An Audiomedia 3 Card Using Wine?"
date: 2006-08-23
forum: Multimedia &amp; Video
---

### Post by Mark76 on 2006-08-23
To install the drivers?

---

### Post by dolson on 2006-08-23
no. if your hardware is not supported in linux, you're stuck with windows.

---

### Post by floogy on 2006-08-24
I thought something similar about scanner and the wine twain. I'm curious if that will work on usb or firewire devices.
Although I think I already read about that, if that would work ;-)

EDIT (I googled a bit):
[http://www.sane-project.org/old-archive/1999-08/0249.html](http://www.sane-project.org/old-archive/1999-08/0249.html)
[http://www.sane-project.org/old-archive/2001-04/0155.html](http://www.sane-project.org/old-archive/2001-04/0155.html)
[http://lists.alioth.debian.org/pipermail/sane-devel/2005-April/013476.html](http://lists.alioth.debian.org/pipermail/sane-devel/2005-April/013476.html)

[http://www.winehq.org/?issue=311#gPhoto%20&%20TWAIN](http://www.winehq.org/?issue=311#gPhoto%20&%20TWAIN)
> TWAIN, the standard for image acquisition devices, has only been implemented for scanners in Wine. This weekend Marcus dropped a large patch to add support for [COLOR="DarkRed"]gPhoto supported devices[/COLOR]. Marcus has been a Wine hacker for over a decade and in the past few years has been actively working on gPhoto. In fact, if you've seen the annotated pictures from WineConf the past couple of years, they've been done by him. On Sunday he asked on wine-devel about his approach for Wine's TWAIN to access libghoto
[http://packages.ubuntu.com/warty/libs/libwine-twain](http://packages.ubuntu.com/warty/libs/libwine-twain)
> This package contains a TWAIN interface that allows Windows apps to communicate with scanners [COLOR="DarkRed"]supported by SANE[/COLOR].

Although there have been some thoughts about supporting scanners ***from Linux*** through wine with a twain interface (this is the upside down situation, of the working examples above), I think this is not supported, and might never be supported in the future.

---

