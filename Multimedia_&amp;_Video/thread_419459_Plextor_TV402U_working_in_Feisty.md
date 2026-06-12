---
title: "Plextor TV402U working in Feisty?"
date: 2007-04-23
forum: Multimedia &amp; Video
---

### Post by lumpmoose on 2007-04-23
Has anyone got the Plextor TV402U USB capture box working in Feisty/2.6.20?  I've tried both the [[color=blue]blog.zoeloelip.be[/color]](http://blog.zoeloelip.be/2007/02/19/go7007-driver-update/) and [[color=blue]nikosapi.org[/color]](http://nikosapi.org/nikosapi.org/wiki/index.php?title=WIS_Go7007_Linux_driver) drivers, with and without the manual fxload method (i.e. [FONT="Courier New"]sudo fxload -t fx2 -D /proc/bus/usb/002/006 -I /lib/firmware/ezusb/hpi_PX-TV402U.hex[/font]) and the correct /dev/video device never appears.  The [[color=blue]Gentoo Wiki[/color]](http://gentoo-wiki.com/HARDWARE_go7007) and [[color=blue]bug[/color]](http://bugs.gentoo.org/show_bug.cgi?id=157021) pages haven't been updated for 2.6.20 yet.  I guess I upgraded too early (it was working fine in Edgy, I believe with one of the Gentoo bug diffs and running fxload manually).

---

### Post by will71110 on 2007-08-16
Has anyone got this to work yet.  I'm am also having problems with this.  I tried what this post said [http://ubuntuforums.org/showthread.php?t=288830 ]("http://ubuntuforums.org/showthread.php?t=288830") but this did not work.  I get an error.  Anyone else have a fix for thsi?

---

