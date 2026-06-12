---
title: "remove ALL nvidia references before installing new nvidia driver ?"
date: 2009-10-27
forum: Multimedia Software
---

### Post by nss0000 on 2009-10-27
Gents:

My new AMD-965 kit includes a BFG_9800-GTX+ vidcard. I've installed Jaunty_9.04 and packaged nvidia drivers using SYNAPTIC. Graphics performance is miserable. Expected, as the installed drivers are not listed as supporting the card.

The NVidia-site lists their available Linux driver  <185.18.36> driver as fully supporting the card. 

From searches I gather before trying to install this new NVIdia driver I must remove **ALL TRACES** of any previous NVIDIA drivers. Is there a single command to do this ?

---

### Post by oldfred on 2009-10-28
I never found a good command. I went berserk and unstalled lots of stuff. I accidentally uninstalled the entire desktop and only had a command line for a while until I found the command to reinstall. Who knew that gdm was gnome? 

I removed the nvidia from hardware drivers and booted with the nv device driver in my old xorg.conf. I have only updated for at least two years and had lots of versions of stuff. I then went into synaptic and removed everything nvidia. Then I downloaded the current driver. Although it works fine, it is not as good as the clean install I did in other partitions to test 64 bit and to test Karmic. Both worked just fine as installed and do not even have much of anything in xorg.conf. 

This many times install will be retired and a new clean install of Karmic will be my system about 2 weeks after it is released.

---

### Post by cor2y on 2009-10-28
You dont need to remove any nvidia references/software/drivers the installer will notify you that it has to remove them in order to install the new drivers and you will be prompted to agree or disagree.
Next you will then have to reboot.
A [guide]("http://ubuntuguide.org/wiki/Ubuntu:Jaunty#Graphics_Card") on installing the closed ones that come with ubuntu or the ones found on the nvidia site with this [guide]("http://ubuntuforums.org/showthread.php?p=7853897") it applies to all versions you find on the nvidia site.

---

