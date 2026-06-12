---
title: "Mythbuntu Diskless Image Size Question"
date: 2011-01-22
forum: Mythbuntu
---

### Post by Verzweifler on 2011-01-22
I did a new installation "from scratch" of Mythbuntu 10.10 and now face the issue that one of my diskless frontends won't no longer boot. 
As part of the PXE boot process, I first get a message that the IP-address has been assigned by the DHCP-server as expected but then an error shows up telling me that the size of the image to be loaded is too big.

I compared the image sizes from my previous 9.10 installation with that from 10.10 and realized that the i386.img in /opt/ltsp/ now has approx. **[COLOR="Red"]950[/COLOR]**MB of size, whereas the image in 9.10 was only about **[COLOR="Red"]200[/COLOR]**MB.

My frontend has 1GB of main memory and unfortunately cannot be upgraded as all banks are already full...

How can I reduce the image size, then? I tried the usual "chroot" and uninstalled quite some packages; however, the size is not shrinking enough. I also uninstalled mythtv (and planned to reinstall it afterwards to be placed in the overlay-section) but the size still is 680MB and I do not see what else I should uninstall.

Any help is appreciated. I am also investigating on whether I should use MiniMyth instead, since this will still work -according to the documentation- with only 512MB and shoudl work with 1GB as well... 

Thanks for your help


Michael

---

