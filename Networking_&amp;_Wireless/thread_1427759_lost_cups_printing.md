---
title: "lost cups printing"
date: 2010-03-11
forum: Networking &amp; Wireless
---

### Post by Tourdog on 2010-03-11
My printer HP 6940 dt is accessed via wifi.  It worked flawlessly on -14, -18 but not the new Karmic Kernel -20 .

> CUPS server error...............  the cups scheduler is not running> Also: There was an error during the CUPS operation 'http connection encryption failed.'

I've tried nearly all the CUPS etc drivers in Synaptics to no avail..................  should I end this and try Samba?

---

### Post by Tourdog on 2010-03-11
Solved:

Terminal:  "sudo /etc/init.d/cups restart"  

 Printer shows now via wifi and double-sided printing works etc etc.   :)

---

### Post by mudjay on 2010-03-12
Thank you

---

