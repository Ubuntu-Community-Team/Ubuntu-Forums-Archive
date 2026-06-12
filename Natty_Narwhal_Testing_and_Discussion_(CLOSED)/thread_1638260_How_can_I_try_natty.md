---
title: "How can I try natty?"
date: 2010-12-05
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Lancro on 2010-12-05
Im afraid of losing something if I install it with my other OS, and I dont see the option in the instalation to do so...

I have tried this...

[http://www.jonobacon.org/2010/11/30/testing-natty-and-unity-safely-with-a-usb-stick/](http://www.jonobacon.org/2010/11/30/testing-natty-and-unity-safely-with-a-usb-stick/)

But It doesnt work for 2 reasons.

1.- It cant install the nvidia drivers, error "SystemError: installArchives() failed, Its not a natty bug, It is the same error in 10.10 from a usb stick, installing it solve the problem.

2.- Configuration is not saved, each time you boot from usb, you can install or try it, each time you press try it starts from zero, so if I were able to install the drivers, that I wont be..., they wont be kept, so Its imposible to try unity at natty.

I have tried to install it in Oracle VM VirtualBox, there isnt an option to install the nvidia drivers, it doesnt detect the nvidia GPU, so one more time, I cant try unity, and I check all graphic options in virtualbox, 3D acceleration and the rest.

So Im done, I dont know what to try next, is there anything I can do to try unity in natty alpha without partitioning my hard disk?.

Thanks.

---

### Post by ajgreeny on 2010-12-05
Download the iso file for natty, then use the startup disk creator to make a live USB version but make sure you have a reserved space for documents and settings.

You should then be able to install the nvidia drivers and keep them for the next bootup.  It certainly works for downloaded wireless drivers on other versions of ubuntu, so I assume will also work for graphics drivers.

---

### Post by Lancro on 2010-12-05
> **ajgreeny said:**
> Download the iso file for natty, then use the startup disk creator to make a live USB version but make sure you have a reserved space for documents and settings.

You should then be able to install the nvidia drivers and keep them for the next bootup.  It certainly works for downloaded wireless drivers on other versions of ubuntu, so I assume will also work for graphics drivers.

1.2GB for documents and settings, dont works, Its quite frustrating, and the drivers dont work as well.

Thanks.

---

### Post by Lancro on 2010-12-06
I have tried wubi, It installs, but at reboot, it dont boots, its bugged, bump.

---

### Post by Mark Phelps on 2010-12-07
Given that this is the initial ALPHA, what did you expect?

Natty is still in development.  You should NOT be posting questions about it in this forum section.

Instead, go to the proper Development forum and look there.

---

### Post by drs305 on 2010-12-07
Thread moved to Natty Narwhal

---

### Post by ronacc on 2010-12-07
there have been problems making a stattup disk with a persistent save file
see this thread 
[http://ubuntuforums.org/showthread.php?t=1636650](http://ubuntuforums.org/showthread.php?t=1636650)

or you can do an actual install to a usb stick and boot from that , also discussed in that thread .

---

### Post by Amroozy on 2010-12-07
> **Lancro said:**
> I have tried wubi, It installs, but at reboot, it dont boots, its bugged, bump.
i had same problem got wubildr  error so i had to get it from other Ubuntu version i was able to complete the setup except the grub2 installation i had to do it manually using Live CD/USB.. now it's working fine..
good luck trying

---

