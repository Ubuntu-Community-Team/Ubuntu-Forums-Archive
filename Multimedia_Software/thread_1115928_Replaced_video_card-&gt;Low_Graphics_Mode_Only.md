---
title: "Replaced video card-&gt;Low Graphics Mode Only"
date: 2009-04-04
forum: Multimedia Software
---

### Post by toyota_f1 on 2009-04-04
Hi all,

I've got an old machine I was donating to a family member

Ubuntu 8.10
AMD Duron 1700
1 gig RAM

I had finished the install and had everything tweaked the way I wanted when the original video card failed (an old ATI Radeon 9600 256mb AGP).

I swapped out the card with an ATI Radeon 9250 256mb PCI card (not pci-e).  Now I'm getting the EE nothing detected error at startup and can only use low graphics mode.  I guess I haven't played with Intrepid enough - I didn't realize that "screens & graphics" was taken out - I'm at a loss for how to get this card working properly now.

Any help?

Thanks!

---

### Post by utnubuuser on 2009-04-04
Hi - how about > sudo jockey-gtkat the recovery console to see if the machine will offer the right driver.  (jockey-gtk is the command to start the hardware-driver utility).

You could also try installing the ati driver fglrx with > sudo apt-get install xorg-driver-fglrx(that's what the driver is called in Hardy Heron anyway.  I don't imagine it's changed for Intrepid Ibex.)

and maybe > sudo dpkg-reconfigure -phigh xserver-xorg before anything else

---

