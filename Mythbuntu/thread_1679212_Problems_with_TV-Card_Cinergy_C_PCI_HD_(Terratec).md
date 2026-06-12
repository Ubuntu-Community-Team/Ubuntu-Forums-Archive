---
title: "Problems with TV-Card Cinergy C PCI HD (Terratec)"
date: 2011-01-31
forum: Mythbuntu
---

### Post by sgeberl on 2011-01-31
Hi,
Just installed latest Mythbuntu 10.10. and tryed to my TV-Card (Cinergy C PCI HD (Terratec)) up. First the backend recognised nothing, I added the mantis driver in /etc/driver and the backend recognised a Philips - Card (DVB-C) but the frontend was not able to retrieve any signal. I read the articles discribing the compilation of various drivers but the most say, that this is obsolete with Ubuntu Version 10.10.

Is there any HowTo for this task (Ubuntu 10.10) or a hint what I have to do?

Thanks
Stephan

---

### Post by sgeberl on 2011-02-06
solved :-)

add the line

mantis

to /etc/modules

restart the box and everything works fine.

---

