---
title: "Set Booktype for DVD+R when burning DVD's"
date: 2007-10-25
forum: Multimedia &amp; Video
---

### Post by eldarko on 2007-10-25
I am still in the process of migrating from a windoze box.  One of the last challenges is being able to backup my DVD's. 

Previously I used DVD Decrypter / DVD Rebuilder / DVD Shrink.  This part seems to have been solved using Wine (not confirmed since I haven't gone through the complete process).  

I would like to set the Booktype of DVD-R's to DVD-ROM for compatibility.  I could do this previously in DVD-Decrypter.  Under wine it doesn't detect my drive, and won't allow me to.  Some threads recommended using DVD+RW Tools which is more involved then I want.

Is there some software I can run natively that will do this?  Also, I have read positive reviews of DVD::Rip.  Does anyone have preferences for software to decrypt DVD's ?

---

### Post by toastydave1 on 2007-11-25
I too would like to do this, anyone found out?

I have found you can get dvd+rw tools to set the book type but you need to be root, using the command


sudo dvd+rw-booktype -dvd-rom -unit+r /dev/hdc

if I just use "dvd+rw-booktype -dvd-rom -unit+r /dev/hdc" in the command line options in k3b for dvd+rw tools it just burns a +r (note no sudo)

can I run k3b as root?

does anyone know how to configure k3b for bitsetting?

thanks

---

