---
title: "Changing video cards from ATI to NVidia. How to?"
date: 2006-07-08
forum: Multimedia &amp; Video
---

### Post by Sciamano on 2006-07-08
Hi,
I installed the ATI drivers for my video card (a very old Radeon8500). After a LOT of work I succeeded in making them work, but it looks like they have some kind of conflict with the XServer: when I logout or try ctrl-alt-backspace the PC freezes.

A friend of mine lent me his old Nvidia FX5200 and I was willing to try to install it, since it looks like Nvidia drivers have less issues.

How do I do that?
I mean, I guess I have to uninstall ATI drivers before I do anything. How do I do that? 

Thanks
Luca

---

### Post by raldz on 2006-07-08
Follow this howto:

[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

Don't worry if the page is long, you may only need the first part on top..

It's ok not to remove your ATI driver, because when you enable your nVidia driver via nvidia-xconfig, it will just disregard your previous drivers..

---

### Post by Sciamano on 2006-07-08
Thanks, it worked.
And the PC magically stopped freezing after logging out or pressing ctrl-alt-backspace.

Thanks again

---

### Post by raldz on 2006-07-08
cool.. enjoy.. ;) ;)

---

