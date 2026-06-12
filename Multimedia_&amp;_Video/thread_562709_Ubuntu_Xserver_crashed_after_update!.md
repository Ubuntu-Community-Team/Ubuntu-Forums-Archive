---
title: "Ubuntu Xserver crashed after update!"
date: 2007-09-29
forum: Multimedia &amp; Video
---

### Post by imranmcse on 2007-09-29
I recently moved from Windows to Ubuntu and I like it so much. But all my excitements gone when I update the machine and restart the Ubuntu. I am unable to see Xserver now. Look at below:
[B](EE)module ABI minor version (2) is newer than the server's version (1)
(EE) Failed to load module "i810" (module requirement mismatch, 0)
(EE)No drivers available.[/B]

Even I tried changing it to vesa, but still no success. I don't want to lost my whole Ubuntu machine. Is there any way I can recover this error and again back with all stuff?

---

### Post by imranmcse on 2007-09-29
After googling I tried this "sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10"
It shows me error message as well 
**" E: Version '1:1.0.2-0ubuntu10' for 'xserver-xorg-core' was not found.**
I tried changing driver to 'vesa' no success.
The big problem in this shell console there is no internet connectivity at all. My wireless is also not working.
Kindly dears help me please. I am so sad.:mad:

When I run sudo aptitude show xserver-xorg-core | grep Version
it shows ** Version: 2:1.2.0-3ubuntu8**
Kindly help me to solve the issue.

---

### Post by gsmlinux on 2007-10-06
Change the driver from i810 to intel in your xorg.conf file, that worked for me. I also had to remove the lines for the load of the modules ic2 and type1 from xorg.conf.

---

