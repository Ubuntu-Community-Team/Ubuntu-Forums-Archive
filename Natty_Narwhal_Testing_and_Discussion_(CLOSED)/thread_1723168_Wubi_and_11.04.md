---
title: "Wubi and 11.04"
date: 2011-04-06
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Gamegoofs2 on 2011-04-06
I'm rather confused by this bug report
[https://bugs.launchpad.net/wubi/+bug/742967](https://bugs.launchpad.net/wubi/+bug/742967)

It says fix released. Does that mean I can upgrade my wubi 10.10 to 11.04? Or is the bug not fixed yet?

---

### Post by beew on 2011-04-06
> **Gamegoofs2 said:**
> I'm rather confused by this bug report
[https://bugs.launchpad.net/wubi/+bug/742967](https://bugs.launchpad.net/wubi/+bug/742967)

It says fix released. Does that mean I can upgrade my wubi 10.10 to 11.04? Or is the bug not fixed yet?

Sorry man, Wubi is only a kind of demo,--a limited version of Ubuntu working out of a Windows folder. if I were you I wouldn't even bother with upgrading,--and I am sure that there will be weird bugs that only affect WUBI upgrade.  I would get a real install then it would make sense to worry about upgrade.

Just my 2 cents.

---

### Post by Gamegoofs2 on 2011-04-06
What do they remove from the install then that makes it different?

---

### Post by bcbc on 2011-04-07
There's nothing different that you would notice. 

It uses a virtual disk instead of a partition. It boots a little differently. The key thing is the ease of installation and more importantly uninstalling. That's the benefit of Wubi for people that just want to try out Ubuntu without the risk of partitioning or committing to a full install.

The downside is that the loop-mounted virtual disk is more prone to corruption so if you decide you like Wubi it's better to do a partition install (or make sure you're good about keeping backups).


So... regarding that bug report - the fresh install has been confirmed to work. The upgrade is supposed to be fixed but there is no confirmation yet (I'm running a test now).

The thing to remember about Beta testing is that devs don't worry as much about promoting changes - so you should anticipate that things might break - even if they do work today.

Edit: my first upgrade test worked perfectly. That one had Wubi installed to the C: drive. I'm about to test the other one (not installed on C: ). There is a difference that has caused Grub problems on Lucid installs as well as upgrades to Maverick.
Edit2: my second upgrade on a non-Windows install worked as well. No issues or misleading grub messages.

---

### Post by beew on 2011-04-07
> **bcbc said:**
> There's nothing different that you would notice. 

It uses a virtual disk instead of a partition. It boots a little differently. The key thing is the ease of installation and more importantly uninstalling. That's the benefit of Wubi for people that just want to try out Ubuntu without the risk of partitioning or committing to a full install.



As a limited demo I don't see any advantage of WUBI over a live usb with persistence. If you want a full blown installation without partitioning your hard drive you can install Ubuntu in an external drive and boot from it. It gives you full Ubuntu performance and speed without the limit imposed by Windows and virtualization. Unlike WUBI, it wouldn't change a thing in your Windows installation (whereas WUBI would, as it has to be installed in Windows!) As it is a full fledged Ubuntu system you can install proprietary graphic cards, do system and kernel update just as you would in a 'normal' internal install. 

My main work OS is Ubuntu 10.10. But i have an external drive multi-booting Ubuntu 10.10 (with only FOSS drivers so I can run it on different PCs) , Ubuntu 11.04 beta, Fedora 14 and qomo (a Chinese Linux distro) I use it as a portable on many pcs with different specs and there is no diminishing in performance and speed commonly suffered in virtualization.

---

### Post by bcbc on 2011-04-07
> **beew said:**
> As a limited demo I don't see any advantage of WUBI over a live usb with persistence. If you want a full blown installation without partitioning your hard drive you can install Ubuntu in an external drive and boot from it. It gives you full Ubuntu performance and speed without the limit imposed by Windows and virtualization. Unlike WUBI, it wouldn't change a thing in your Windows installation (whereas WUBI would, as it has to be installed in Windows!) As it is a full fledged Ubuntu system you can install proprietary graphic cards, do system and kernel update just as you would in a 'normal' internal install. 

Wubi isn't a virtual machine. So it runs natively (not in windows) using full access to hardware. You can install proprietary graphic card drivers, do system and kernel updates etc.

---

### Post by rhc on 2011-04-07
> **beew said:**
> As a limited demo I don't see any advantage of WUBI over a live usb with persistence. If you want a full blown installation without partitioning your hard drive you can install Ubuntu in an external drive and boot from it. It gives you full Ubuntu performance and speed without the limit imposed by Windows and virtualization. Unlike WUBI, it wouldn't change a thing in your Windows installation (whereas WUBI would, as it has to be installed in Windows!) As it is a full fledged Ubuntu system you can install proprietary graphic cards, do system and kernel update just as you would in a 'normal' internal install. 

My main work OS is Ubuntu 10.10. But i have an external drive multi-booting Ubuntu 10.10 (with only FOSS drivers so I can run it on different PCs) , Ubuntu 11.04 beta, Fedora 14 and qomo (a Chinese Linux distro) I use it as a portable on many pcs with different specs and there is no diminishing in performance and speed commonly suffered in virtualization.

Please, if you are not experienced on a matter; do not behave decisive. You are misleading newbies. I understand that you didn't use Wubi even once. Funny.

---

### Post by shuttleworthwannabe on 2011-04-07
I was just about to ask **beew **to post a link on a step by step guide on how to install on an external harddrive without affecting the native host system (boot menu at least).

---

### Post by Gamegoofs2 on 2011-04-07
Thanks bcbc and everyone else! I'll back up my current wubi install and try upgrading.

---

