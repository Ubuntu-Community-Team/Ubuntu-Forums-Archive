---
title: "ATI Radeon Mobility X1200 w/ Fiesty Fawn"
date: 2007-08-24
forum: Multimedia &amp; Video
---

### Post by pandron on 2007-08-24
I have an ATI Radeon Mobility X1200 video card in my Toshiba laptop.  I was able to install Ubuntu using the "Alternate CD", and by typing in:

"*sudo dpkg-reconfigure -phigh xserver-xorg*" and selecting "vesa" was able to get the GUI running.

Then I downloaded and installed all the updates, etc.  

I also typed "*sudo pciids-update*"

And "*lspci*" which showed my video card correctly as 
ATI Technologies blah blah blah X1200".

Then I tried to enable the ATI restricted driver in the "restricted driver manager".  The xserver failed, and brought me to the command line.

I then ran the dpkg-reconfigure again and am back to the vesa driver.

Has anyone solved the X1200 driver problem?  I am very much of a newbie, so please break it down in the simplest terms possible!

Thanks!

---

### Post by pandron on 2007-08-24
> **pandron said:**
> 
I also typed "*sudo pciids-update*"


I actually typed "sudo update-pciids". sorry.

---

### Post by pandron on 2007-12-07
Just a quick update.  It turned out I was installing the 64-bit version of Fiesty (which in theory should work I guess).  I recently installed Gutsy 32 Bit, and I'm up and running.  It work right away, all I had to do was enable the restricted driver.  Now if I can just get my wireless working...

---

