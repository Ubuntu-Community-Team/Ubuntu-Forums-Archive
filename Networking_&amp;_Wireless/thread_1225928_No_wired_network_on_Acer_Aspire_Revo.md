---
title: "No wired network on Acer Aspire Revo"
date: 2009-07-29
forum: Networking &amp; Wireless
---

### Post by rogerdean on 2009-07-29
Hello all

I've just got hold of my new Acer Aspire Revo nettop and I'm very pleased with it. Jaunty went on and, after adding a PPA, the nVidia ION graphics are fine.

All that's left to fix is the wired network, which shows no life at all, no LED on my router etc.

Does anyone have any ideas on this? Doubtless you'll need more info from me - just let me know what to post and how to get it!

Cheers
Roger

---

### Post by superprash2003 on 2009-07-29
try checking the LAN cable again.. could be a problem with the cable

---

### Post by rogerdean on 2009-07-29
Thanks, I know these things often turn out to be something simple. Anyway, I've tested this with half a dozen different cables, and 2 Revo computers. All same result. 

So, how do I get the readouts that will help you gurus point me in the right direction?

Cheers
R

---

### Post by rogerdean on 2009-07-30
OK, making progress. It seems the new nvidia chipset has an ethernet driver that is not yet in the kernel or in Ubuntu

This manual page...
[http://manpages.ubuntu.com/manpages/jaunty/man4/nfe.4freebsd.html](http://manpages.ubuntu.com/manpages/jaunty/man4/nfe.4freebsd.html)
...tells me I can compile the driver into the kernel (eek!) or load it as a module on boot (better)

The driver file is provided at that page, and I can edit loader.conf as instructed. But where do I put the driver file so that loader.conf finds it?

Thanks in advance!
Roger

---

