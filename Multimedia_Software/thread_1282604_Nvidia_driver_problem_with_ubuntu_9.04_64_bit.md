---
title: "Nvidia driver problem with ubuntu 9.04 64 bit"
date: 2009-10-04
forum: Multimedia Software
---

### Post by damnated on 2009-10-04
I have an Nvidia 8600 GT graphic card, and something got messed up. This is what i did:

-fresh ubuntu 9.04 install
-installed the driver through trying to apply desktop effects. ubuntu said driver downloaded and installed.
-after the necessary reboot, the ubuntu splash screen appeared. but after then, ubuntu didn't load, the screen blacked out, and after a few seconds my monitor didn't have any signal.

these things happened in windows too, when there was something wrong with the driver. so i started ubuntu with the recover option, said to try and fix video errors, after then the system booted normally, however the desktop effects could not be applied, leading me to think again that there is a driver problem.

i'm stressing driver problem because about a month ago i've installed the 32 bit version of ubuntu 9.04; installed the driver the same way, and didn't have any problems.

i switched to the 64 bit version because i have 6 gigs of ram installed, so going back to that version is not really an option.

any ideas are greatly appreciated.

---

### Post by norwoods on 2009-10-04
try installing a driver with System>>Administration>>Hardware Drivers.
i am using the 190 driver.

---

### Post by ifraser on 2009-10-04
> **damnated said:**
> 
-after the necessary reboot, the ubuntu splash screen appeared. but after then, ubuntu didn't load, the screen blacked out, and after a few seconds my monitor didn't have any signal.
any ideas are greatly appreciated.

I had this same problem after upgrading to 4GB of RAM, though I didn't have it with Windows (32-bit).  Though you may indeed have driver issues, this is often an issue caused by problems with outdated BIOS.  Check your motherboard manufacturer's website to see if this is the case.  I updated mine and the problem was fixed.

---

### Post by damnated on 2009-10-05
Updated the bios, nothing changed.
I also reinstalled ubuntu, and installed the 180 driver from Hardware Drivers, after that didn't work i disabled it, installed the 173 driver. After that failed too, i installed manually the 185 driver from real terminal, nothing changed. Going to try the 190 version now, although i don't have much hope, considering it's still a beta. 
Any other ideas?

---

### Post by damnated on 2009-10-06
I uninstalled everything, and started over. 

[LIST]
[*]Installed the 173 driver, same error. Uninstalled it.
[*]Installed the 180 driver, same error. Uninstalled it.
[*]Installed the 185 driver, same error. Uninstalled it.
[*]Installed the 190 driver, same error. Uninstalled it.
[/LIST]
I even tried installing the drivers with Envyng. Same error. Please think of something..

---

### Post by damnated on 2009-10-08
bump.

---

### Post by ostruvek on 2009-10-10
> **damnated said:**
> bump.

Hi, I had the same problem. Everything seems to be solved by updating BIOS on my motherboard.

---

### Post by BaNnEd on 2009-10-12
I got the same problem, here with a GF 9600 (tried GF 8500 and worked well)
But not with my 9600, i already changed one from palit against another model from leadtek because i thought the card was damaged, but obviously it wasn't :(

then i tried the card with my hd in another pc, there it worked, so it hat nothing to do with the ubuntu system.
returned my motherboard to test it for damages, they didn't find any but updated my bios. i still have this same damn error :(

now i'm probably changing card with my brother, he's got a 8500 which worked well with my motherboard... unless anyone finds another solution ;-)

---

### Post by Rodart on 2009-10-13
> **ostruvek said:**
> Hi, I had the same problem. Everything seems to be solved by updating BIOS on my motherboard.
 
he is right , update the BIOS , you can do that by going into the motherboards manufacturer webpage.

---

### Post by damnated on 2009-10-13
> **Rodart said:**
> he is right , update the BIOS , you can do that by going into the motherboards manufacturer webpage.

I appreciate that you're all trying to help, but please read my replies too. > **damnated said:**
> Updated the bios, nothing changed.

---

### Post by Malta paul on 2009-10-13
I have the same graphic card as you have, when I had a Ubuntu Kernel update I lost the graphic screen.
This is what I did to get things working normal again (It may not work for you though)

1)I rebooted in the recovery mode and reverted to the Ubuntu generic video driver.
2)Removed all the video drivers using Synaptic.
3)Installed Kernel 2.6.30
4)Rebooted again with the generic screen then installed the 185 hardware driver.
5)Finally rebooted and all now worked good again.

Good luck:)

---

### Post by BaNnEd on 2009-10-13
how did you install the 185 driver with the 2.6.30 kernel?
tried to do the same, when it comes to install the 185 driver it tells me that there would be no precompiled kernel and i have to do it manually and so on, but only if i'm experienced... and poorly i'm not :(

so till now i tried it with the actual 2.6.28, but it didn't solve the problem -.-

---

### Post by Malta paul on 2009-10-14
Here is the latest 2.6.30.9 Kernel in .deb format:
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.9/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.9/)

---

### Post by BaNnEd on 2009-10-14
I did install the kernel and it's up and running, thats no problem.

but when i boot up and try to install the Nvidia driver, it always tells me... ah, here, i got a pic for u ;-)

... hm maybe not... with the new kernel there seems to be a prob mounting my sd-card -.- ...
but anyway, thats what it tells me when trying to install:

```
The CC Version check failed:
The Compiler used to compile the kernel (gcc 4.2) does not exactly match the current compiler (gcc 4.3). 
The Linux 2.6 Kernel module loader rejects Kernel modules built with a version of gcc that 
does not exactly match that of the compiler used to build the running kernel. 

```

so... how did you manage to use the 4.3 to compile your kernel?

(i have gcc-4.3 installed, but obviously it doesn't use it to compile the kernel? or did i misunderstand sth?)

---

### Post by Malta paul on 2009-10-15
I just copied the .deb Headers, all & amd64 Then the .deb Image amd64. onto your desktop. Click on the 'Headers all' folder first and it will install,then 'Headers amd64' and finally the 'Image' folder. Reboot your computer and at the grub menu select recovery mode for 2.6.30.9. It should then boot-up I hope! If not just reboot with your original Kernel.

---

### Post by khal03 on 2009-10-15
So I have been fighting this for some time as well. I have to install the most generic system to have 3d graphics and put my extra 6GB of ram in my drawer.

I have tried the same solutions as well.

Bottom line:

Can we run 8.04LTS_amd64 with REAL nVidia drivers, and then utilize all of our ram or not? I have been able to set up an 8GB cooler but without 3d Graphics, and I have set up nVidia drivin' boxes as well, but only with 2GB ram. On another note, I somehow had tuned off my updates. When I realized it I quickly fixed that and updated with like 250 or more updates. Now I have an nVidia 8500GT 1GB cooler that cannot run java aps no matter how or where I try to install them from.

Sadly enough, I was alot happier with Ubuntu when I was broke, and running it on P1 and PII coolers I found on the curb. I had no graphics, I had no ram, but I felt powerful, as I had revived what Windoze Users had abandoned as the pc's seemingly were outdated. Now that I understand Ubuntu better and have saved money to buy new tech I cannot fully utilize it any better than the old PII's could. They were incompatable with the new hardware, and it seems as though, now that I have the tech, that now my OS is incompatable.

Please don't spank me for being negative, but some of us would love to play urban terror some day again. Our Windoze friends still are and laughing at Ubuntu users who need not sign in.

Does anyone know of the right version of ubuntu will allow me to use nVidia drivers and 8gb of ram while I am using AMD64?

Thanx guys.

---

### Post by khal03 on 2009-10-15
How does one change the cup of ubuntu status? I am not on my first cup by any means.

---

### Post by damnated on 2009-10-15
> **khal03 said:**
> 
Can we run 8.04LTS_amd64 with REAL nVidia drivers, and then utilize all of our ram or not?


I'm having this same problem with 8.04 too. Perhaps the cards are faulty. I'm actually thinking about selling half of my ram, as i'm just annoyed. 

Oh, and that cup of ubuntu is a forum ranking, it changes based on the number of your posts.

---

### Post by khal03 on 2009-10-15
Well, I'll probably never be dipped in Ubuntu. LOL I get a little opinionated, and people freak rather than hear the message. Thanx for the explanation.

As well, I have been dual booting between LTS Ubuntu and LTS Xubuntu. Where Xubuntu's partition is really a distro testing partition. I have tried a few other releases of Ubuntu and Kubuntu and Xubuntu and I always end up hitting a stone wall with all these ram and vid issues. Lately I have been considering going back to my original testing of all Linux Distros. I was really happy when I found Ubuntu amongst the many distros, because it ***seemed*** to be ready to be installed on boxes for retail sale with only minor modifications. The problem is twofold: the end user typically doesn't want to become a so-called computer nerd to be able to use their computer. For this reason I have tried hard to let others do the research and development, and I have attempted to limit my involvement to thoroughly testing the distros as an end USER, not a programer/coder/bash-scripter. It may seem unorthodox coming from a die-hard Linux user, but most people buy pc's to make there lives easier, for entertainment, for gaming, etc., not so they can hack them for weeks and months and years.  So, this leads to the second problem: most consumers don't want to do a lot of hit or miss research to upgrade boxes with new hardware and/or software. How can I sell a pc to someone that just connot play video games in hi-dollar 3d while being 64bit and housing more than 3GB ram? 

See? I'm ranting. LOL

Bottom line IMO is that beta shouldn't expire and become a release until it is known to work with available hardware, drivers, etc. Otherwise Ubuntu, and those of us who try to provide intelligent computer solutions to our customers, both risk being scoffed and ignored.

You get the point. I'm sorry for ranting. 

Hey, admin, can I be awarded ubuntu beans for total K/b's of posts rather than total number of posts? he he.

In the meantime, I guess I can drink my coffee with cream or with sugar but apparently not with both?! :confused:

I'll post again in a year or two.

---

