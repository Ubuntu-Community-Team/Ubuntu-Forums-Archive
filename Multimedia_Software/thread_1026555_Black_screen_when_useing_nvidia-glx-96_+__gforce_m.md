---
title: "Black screen when useing nvidia-glx-96 +  gforce mx 400."
date: 2008-12-31
forum: Multimedia Software
---

### Post by gorby on 2008-12-31
Hi there,
I recently installed intrepid, the install was a breeze and this is the only problem  i have run into. 

Initially i tried the latest glx package, but saw in dmesg that my card was not supported when the module loaded. So i installed nvidia-glx-96 and now the module loads fine as i can see in dmesg.
The next problem was a "no screens" error from X after i had run nvidia-xconfig. This was the first time id had call to look in my xorg.conf this release ; i was suprised by the absence of many old things. 
Adding in the "BusId" field into the device section got X starting again, but im stuck of things to try now.

To compound the problem, there is no signs of foul play, xorgs log file looks fine; no errors relating to video or screen stuff. Also I know gnome / x is fully starting as i have auto login enabled and if i type my keyring password after the hard drive has settled down it brings my wifi up =)
Compiz was getting segfault errors also, so i removed it on the off chance that was causing the problems, no joy.
Any help would be greatly appreciated =) vesa mode sucks :P If you would like me to post any logs or config files just ask.
ty in advance.

edit - replaced the hard drive, it was causing the segfaults, issue is still persistent on clean build, before and after update manager grabs the new kernel.

---

### Post by bumanie on 2008-12-31
If my memory serves me correctly, that card should use the older legacy driver - can't remember the number (78 I think).

---

### Post by pietjanjaap on 2008-12-31
Try envy, you can choose 3 drivers.
envy is in ubuntu.

---

