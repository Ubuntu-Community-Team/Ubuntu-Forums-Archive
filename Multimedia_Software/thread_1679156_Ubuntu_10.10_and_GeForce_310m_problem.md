---
title: "Ubuntu 10.10 and GeForce 310m problem"
date: 2011-01-31
forum: Multimedia Software
---

### Post by meredith on 2011-01-31
Hello all, I´m new to this forum and to Ubuntu.
I bought a notebook Asus K52Jc with i5 and 8gb ram almost two weeks ago, and since then, I have been trying to make the GeForce 310m included to work properly, with the 3D acceleration. I´ve read all available guides online I could find, including all the guides on this forum. I read Nvidia forums, Ubuntu forums in english, spanish and italian, random guides in blogs, and I tried everything, but nothing worked to make the 3D acceleration to work.

I tried to install from root the drivers provided from Nvidia, but the system doesn´t even recognize them. Then I reinstalled Ubuntu from scratch and tried to install Nvidia drivers from repository, but I get the message "The drivers are enabled but currently not in use" or something like that, when I check system hardward.

Any attempt to create the configuration file, with sudo nvidia-xconfig, resulted in no graphic environment for Ubuntu, I only had the login screen. I manipulated the file xorg.conf following I don´t know how many different guides, but it didn´t work, if I do have a file named xorg.conf, no matter what´s inside this file, the graphic environment won´t load, I just get console mode.

This experience helped me a lot to learn about Ubuntu, because I never used it before, but I´m feeling lost and powerless and all the many guides online say so many different things, none of them worked, and I want to stop configuring my notebook and start using it, so any help will be appreciated. :)

---

### Post by cchhrriiss121212 on 2011-01-31
The bad news:
This laptop has Optimus graphics, which means that it has an integrated Intel GPU in addition to the 310m. It is designed so that you can switch between GPUs when using the OS, on Linux this does not work and you are stuck with the Intel chip. Nvidia has no plans to support this type of setup on Linux.

The good news is that you don't need to install any drivers.

---

### Post by meredith on 2011-01-31
Oh, I see, thank you for the reply!

I will install Windows XP and Ubuntu in another partition, because I really need 3D acceleration for some of the applications I use. :)

---

### Post by cchhrriiss121212 on 2011-02-01
Just found this out: Apparently a few optimus laptops have an option that allows you to switch between the GPUs from the BIOS menu, meaning you could have Nvidia on all the time. It is worth a check, before installing a new OS.

---

### Post by cascade9 on 2011-02-01
> **cchhrriiss121212 said:**
> Just found this out: Apparently a few optimus laptops have an option that allows you to switch between the GPUs from the BIOS menu, meaning you could have Nvidia on all the time. It is worth a check, before installing a new OS.

Worth checking, but not many optimus laptops have this option..and some of the ones that did have the option have had it removed with BIOS updates. :( 

Damn optimus.

---

### Post by cascade9 on 2011-02-01
> **cchhrriiss121212 said:**
> Just found this out: Apparently a few optimus laptops have an option that allows you to switch between the GPUs from the BIOS menu, meaning you could have Nvidia on all the time. It is worth a check, before installing a new OS.

Worth checking, but not many optimus laptops have this option..and some of the ones that did have the option have had it removed with BIOS updates. :( 

Damn optimus. 

BTW,  being technical optimus isnt actually switchable graphics. From what I understand, the nvidia GPU only displays teh accelerated part of the the display, then overlays it on top of teh output from the intel video chip. 

This is also interesting- 

[http://forum.notebookreview.com/asus/539174-asus-k52jc-ami-bios-bios-mod-request-nvidia-optimus.html](http://forum.notebookreview.com/asus/539174-asus-k52jc-ami-bios-bios-mod-request-nvidia-optimus.html)

---

### Post by realzippy on 2011-02-01
[http://www.nvnews.net/vbulletin/showthread.php?t=153816](http://www.nvnews.net/vbulletin/showthread.php?t=153816)


..on this laptop there is a BIOS switch to power off the nvidia card,
so it does not suck power.Running the nvidia card is not possible.

---

