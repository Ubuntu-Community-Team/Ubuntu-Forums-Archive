---
title: "Dual - 4 header PCI Video (nvidia) setup"
date: 2009-03-18
forum: Multimedia Software
---

### Post by opscure on 2009-03-18
Hi everyone,

I'm hoping someone out there can assist me a bit with some issues I'm having.  I just picked up two, four header pci video cards and I am only able to access one (card -- four screens) depending on the order I list them in my xorg.conf file.

Card: [http://www.newegg.com/Product/Product.aspx?Item=N82E16814139037](http://www.newegg.com/Product/Product.aspx?Item=N82E16814139037)
I am currently using the 180.29 driver from nvidia's site with xubuntu 8.10 fully updated.  The driver seemed to install alright... see attached nvidia-installer.log inside of logs.tar.

Where I'm running into problems is initializing the second PCI Card on the system.  This video card (screens 4-7) work fine if I list them first in the xorg.conf file (also in the logs.tar file). So, I know it's not bad hardware.  You can also find the Xorg.0.log in the logs.tar file for reference to the errors on the second GPU.  I put an output of lspci |grep nVidia in the tar file so, you can be sure my bus ids are right.

I think the problem has something to do with a lack of devices being created in /dev/.  The devices I'm getting are nvidia0, nvidia1, nvidia2, nvidia3, and nvidiactrl... see the lsgrepnvidia.log file in the tarball for the output from ls |grep nvidia inside the /dev/ directory.  Either that or the driver doesn't understand how to interact with four GPU's.  I really don't think this is the case since someone was able to get six monitors working in this post:
[http://ubuntuforums.org/showthread.php?t=884161](http://ubuntuforums.org/showthread.php?t=884161)

I'm not sure if there is a manual way to add more devices and have the second GPU point to them.  I tried a `mknod nvidia4 c 195 0` inside of the /dev/ directory and it created the device node fine, but had no impact on the fifth display turning on.

Anyone out there have any ideas, this is kind of driving me crazy.

Thanks.

---

### Post by opscure on 2009-03-18
Needed to pass vmalloc=256M to the kernel at boot.

All better now... 8 monitors up and running correctly.

---

