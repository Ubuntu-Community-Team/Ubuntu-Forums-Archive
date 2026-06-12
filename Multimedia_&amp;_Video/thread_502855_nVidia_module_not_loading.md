---
title: "nVidia module not loading"
date: 2007-07-17
forum: Multimedia &amp; Video
---

### Post by Sirkent on 2007-07-17
I've got an  NVIDIA® Geforce Go 8600, which doesn't work with the nvidia-glx driver provided in Ubuntu.

So I've downloaded the appropriate driver from Nvidia manually and run the set-up. It compiles a module for the kernel just fine. I can then restart GDM and it all works beautifully.

Bizarrely though, when I restart, X fails to start simply saying that no screens are found. I have to remove and then reload the module (using ignore) and then it works again. I assume there's a clash somewhere with the module, or it's being explicitly told not to load? Where would this be?

Any ideas?

---

### Post by ^Pho[T]on on 2007-07-17
i had this problem b4. I think it is still loading the default ubuntu nvidia module which then stops the new module from being loaded. it will work if you reinstall the new NVIDIA module after every restart and start X immediately after, which is the dumb way to do it. I solved this by stopping the old module from loading at boot time thereby allowing the downloaded module to load.

in file "/etc/default/linux-restricted-modules-common" add the line

DISABLED_MODULES="nvidia nvidia_legacy"

then restart your pc it shuld solve the problem

---

### Post by Sirkent on 2007-07-17
I'm afraid it doesn't work. The Xorg error complains that the module cannot be found...

---

### Post by Sirkent on 2007-07-18
*Bump*
Any ideas anyone? Is there anywhere I can look so I can find out why the module is causing a problem?
Thanks

---

### Post by dcooper108 on 2007-08-08
In the file "/etc/default/linux-restricted-modules-common" add the line

DISABLED_MODULES="nv"

---

