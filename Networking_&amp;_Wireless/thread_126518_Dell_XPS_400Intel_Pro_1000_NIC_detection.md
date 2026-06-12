---
title: "Dell XPS 400/Intel Pro 1000 NIC detection"
date: 2006-02-06
forum: Networking &amp; Wireless
---

### Post by vfxdude2 on 2006-02-06
Hi folks -

Just thought I'd post a piece of hard-won info for the sake of others trying to solve the same problem... :-)

I have a Dell XPS 400 with an on-board Intel Pro 1000 gigabit ethernet chip. (It's a PC82573L to be exact;  I had to follow the traces on the board to figure out what it was ;-) )

Anyway, the install for Breezy couldn't detect this NIC.  

After trying several dozen other things, I found the really easy solution:  You need to re-compile the e1000 driver.  Download the source from the Intel website, make sure you have the development packages installed (you can do that from the package manager), and then just compile it.

Don't know why the original e1000 driver didn't work.  I have a 64-bit Pentium D;  maybe that has something to do with it... who knows?

-vfxdude

---

### Post by mips on 2006-02-16
[http://www.ubuntuforums.org/showthread.php?p=741687](http://www.ubuntuforums.org/showthread.php?p=741687)

Thanks to ubuntulifestyle for the french to english tranlation of the wiki page.

---

