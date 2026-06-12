---
title: "How to uninstall ATI drivers?"
date: 2006-06-13
forum: Multimedia &amp; Video
---

### Post by AceRimmer on 2006-06-13
I installed the "official" ATI drivers and now I am not getting any 3d acceleration.  Before I was getting 2400fps on the gears benchmark, now I'm getting 150.  I tried just renaming the driver entries in xorg.conf to "ati" but it still isn't working.  Then I copied my original xorg.conf file over the one that was modified by the ati installer.  Still nothing.  I'm trying to avoid doing a clean install here. My card is a 9000 Pro AGP. 

Thanks.

---

### Post by ajgreeny on 2006-06-13
Try "sudo dpkg-reconfigure xserver-xorg"

This may put you back to a more usable system, though I did find it took a bit of doing on my box and I had to make a few tries before getting it right.  Luckily I had a second partition on which I try out such things before doing it on my main working partition.  I eventually had to copy the xorg.conf from the working partition to the test one before I got back to a sensible condition.

---

### Post by fatalfury24 on 2006-06-13
[QUOTE=AceRimmer]I installed the "official" ATI drivers and now I am not getting any 3d acceleration.  Before I was getting 2400fps on the gears benchmark, now I'm getting 150.  I tried just renaming the driver entries in xorg.conf to "ati" but it still isn't working.  Then I copied my original xorg.conf file over the one that was modified by the ati installer.  Still nothing.  I'm trying to avoid doing a clean install here. My card is a 9000 Pro AGP. 

Thanks.[/QUOTE]
To uninstall just go into terminal and type in
cd /usr/shar/fglrx/
sudo sh ./fglrx-uninstall.sh

---

### Post by AceRimmer on 2006-06-13
Thanks for the help guys.

---

