---
title: "Freeze with ATI driver 8.33.6"
date: 2007-02-15
forum: Multimedia &amp; Video
---

### Post by Beliar on 2007-02-15
Hello,
I have installed Kernel 2.6.20-11 on Ubuntu Edgy and after that ATI driver 8.33.6
But now my System freezes when X Server starts.

When I boot with a Live CD and restore my old xconfig, i can boot but X wont work.

Ive got a Mobility Radeon x700, any ideas? Any known issues with this driver?
I didnt uninstall the driver that was installed before. can that be a problem? But I never uninstalled a driver I had installed with the ATI installer after upgrading a Kernel before. And no problems.

TIA,
greets, 
Beliar

---

### Post by Beliar on 2007-02-16
Nobody has this problem??

---

### Post by GoingDown on 2007-02-16
Two questions:

* is that kernel from some unofficial repo or where you did get it? 

* Have you compiled drm support in, but not radeon driver? Do you have agp support on your kernel?

* When installing fglrx driver, are you sure that it was compiling succesfully? Because I don't think that fglrx 8.33.6 driver will install on kernel 2.6.20 without a patch. See this thread:

[http://www.ubuntuforums.org/showthread.php?t=353772](http://www.ubuntuforums.org/showthread.php?t=353772)

EDIT: There is actually four questions :-)

---

### Post by Beliar on 2007-02-17
D'OH! Im' sorry, I made a mistake. ](*,) 
Its 2.6.17-11 (I think).
Its just the latest Kernel from the official Repo, its an Ubuntu Kernel and not self compiled.

The ATI setup was succesful. 

Im' sorry, I was short on time so I couldnt investigate more and post more information. I will try to boot it again and look at dmesg and so on.

greets,
Beliar

---

### Post by Beliar on 2007-02-20
Hmm, well dmesg doestn show anything special. modprobe loads the module, no problems there.

But starting X with fglrx as driver will cause the system too freeze and starting it with radeon driver will give me an error, that the card was not found.

Any ideas or do I have to reinstall?? :(

TIA,
greets, Beliar

---

### Post by shrimphead on 2007-02-20
I had exactly the same problem with my x1600xt with the 8.33.6 driver that I compiled from source, with mine it wouldn't freeze on startup but it would lock up my PC and force a hard reset whenever i tried to play a video. the only way I could fix this was to roll back my drivers to the older version that is in the repo.

---

### Post by tseliot on 2007-02-20
Try Envy and follow the instructions on my website:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

