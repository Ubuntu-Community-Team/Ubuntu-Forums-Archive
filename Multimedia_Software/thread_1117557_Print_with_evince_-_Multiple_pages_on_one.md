---
title: "Print with evince - Multiple pages on one"
date: 2009-04-06
forum: Multimedia Software
---

### Post by stivn on 2009-04-06
Hallo,

I am trying do print a pdf with 4 pages on one in landscape format. So i configured in print options (see screenshot) but it prints a strange layout (see screenshot). Then I rotated the pages about 90° an tried do print in vertical format (see screenshots). There the layout is right, but its not in the selected order (i selected 31,42 order an it prints 12,34 order). What am i doing wrong, or is it a bug in jaunty?

Thanks

Stivn

Preferences (Landscape):
[http://www.ubuntu-pics.de/bild/12011/bildschirmfoto_drucken_q74Veo.png](http://www.ubuntu-pics.de/bild/12011/bildschirmfoto_drucken_q74Veo.png)

Print preview (Landscape):
[http://www.ubuntu-pics.de/bild/12012/bildschirmfoto_evince_print__null__t0loru_pcbDLB.png](http://www.ubuntu-pics.de/bild/12012/bildschirmfoto_evince_print__null__t0loru_pcbDLB.png)

Preferences (Portrait):
[http://www.ubuntu-pics.de/bild/12013/einstellungen_hochformat_2hyqVp.png](http://www.ubuntu-pics.de/bild/12013/einstellungen_hochformat_2hyqVp.png)

Print preview (Portrait):
[http://www.ubuntu-pics.de/bild/12015/hochformat_ausgabe_Vok1B7.png](http://www.ubuntu-pics.de/bild/12015/hochformat_ausgabe_Vok1B7.png)

---

### Post by pableu on 2009-09-17
I would say you're affected by this old bug: [https://bugs.launchpad.net/evince/+bug/121524](https://bugs.launchpad.net/evince/+bug/121524)

It should be fixed in 9.10 coming out next month :-)

---

### Post by stumbleUpon on 2009-09-17
You can use pdfnup to print 4 pages per single page in the landscape mode. pdfnup is in the pdfjam package (sudo aptitude install pdfjam)

---

