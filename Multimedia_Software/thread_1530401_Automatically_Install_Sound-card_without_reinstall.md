---
title: "Automatically Install Sound-card without reinstalling ubuntu"
date: 2010-07-13
forum: Multimedia Software
---

### Post by hunterhdolan on 2010-07-13
Hello my name is Hunter Dolan I am just started using ubuntu again and I need a little refresher. 

Here is my ALSA DB entry

[http://www.alsa-project.org/db/?f=8acd844be6dc424370e07aef260fc2db1387372b](http://www.alsa-project.org/db/?f=8acd844be6dc424370e07aef260fc2db1387372b)


I was working on my sound card and some how ended up uninstalling it. Anyways I have tried everything!!! I am about to reinstall ubuntu because it worked then. Does anyone know of a command that will make ubuntu search and install new sound cards? It managed to do it at the installer so I don't see why there isn't a way to do it once installed, unless for some reason it needs to be run before ubuntu is fully installed. Any ideas?

When I installed Ubuntu it was 9.04 and I upgraded to 10.04 shortly after install. Then I installed KDE so now my installation is Kubuntu 10.04 LTS. (I know, complex)

Thanks!

-HD

---

### Post by hunterhdolan on 2010-07-13
Anyone?

---

### Post by Yellow Pasque on 2010-07-13
The kernel module didn't load. Check dmesg to see why. This might be a good time to upgrade ALSA: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)
If you do that, then you should also: [http://ubuntuforums.org/showthread.php?t=1455816](http://ubuntuforums.org/showthread.php?t=1455816)

---

### Post by hunterhdolan on 2010-07-15
> **Temüjin said:**
> The kernel module didn't load. Check dmesg to see why. This might be a good time to upgrade ALSA: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)
If you do that, then you should also: [http://ubuntuforums.org/showthread.php?t=1455816](http://ubuntuforums.org/showthread.php?t=1455816)

OMG Thank-you so much!!!!!!

---

