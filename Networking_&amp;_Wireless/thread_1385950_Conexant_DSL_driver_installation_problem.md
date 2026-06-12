---
title: "Conexant DSL driver installation problem"
date: 2010-01-20
forum: Networking &amp; Wireless
---

### Post by 10amrs on 2010-01-20
A PCI DSL adapter by Conexant I'd like to test and use (in Hardy), but I hit a wall when trying to install its driver from [http://www.zweije.nl.eu.org/~vzweije/accessrunner/](http://www.zweije.nl.eu.org/~vzweije/accessrunner/). When I plug the adapter in, it's detected (visible in lspci), so that's not the issue. I just can't interpret the instructions on the site, namely the following:  >  You will need: The kernel sources of the kernel version you want to insert the     driver into.   Does this mean the linux kernel, like 2.6.x-y? Or does it mean I have to build the whole kernel itself, which is definitely outside my comfort zone.  Next the vague installation instructions:  >  First of all, build the driver and utility programs (no need to do this as root):  Make sure the kernel sources have been unpacked, configured, and     compiled in /usr/src/linux.   I don't have such a folder there, just linux-headers-2.6.24-x(and -generic) for each kernel. And when I made a symbolic link &quot;linux&quot; to the most recent linux-headers folder, it didn't work but just spewed out errors after errors (too long to be posted here, didn't fit in terminal window). Making an empty &quot;linux&quot; folder there didn't make any difference either.  Anyway, I normally untarred the tarball (for the proper kernel) I downloaded from [http://www.zweije.nl.eu.org/%7Evzweije/accessrunner/release/CnxADSL-6.1.2.007-PIM-2.6-1.9.tar.bz2](http://www.zweije.nl.eu.org/%7Evzweije/accessrunner/release/CnxADSL-6.1.2.007-PIM-2.6-1.9.tar.bz2), and then change into the folder, but after I run make, the errors stop the compiling.   ```
 for n in KernelModule/DpController; \         do if [ -d $n ]; then make -C $n all || exit; fi; done for n in KernelModule DownLoadApp; do make -C $n all || exit; done make[1]: Entering directory `/home/am/CnxADSL-6.1.2.007-PIM-2.6-1.9/KernelModule' make CnxADSL.ko make[2]: Entering directory `/home/am/CnxADSL-6.1.2.007-PIM-2.6-1.9/KernelModule' make -C /usr/src/linux SUBDIRS=`pwd` modules make: Entering an unknown directory make: *** /usr/src/linux: No such file or directory.  Stop. make: Leaving an unknown directory make[2]: *** [CnxADSL.ko] Error 2 make[2]: Leaving directory `/home/am/CnxADSL-6.1.2.007-PIM-2.6-1.9/KernelModule' make[1]: *** [all] Error 2 make[1]: Leaving directory `/home/am/CnxADSL-6.1.2.007-PIM-2.6-1.9/KernelModule' make: *** [all] Error 2 
```  Can anybody help me with getting past these hurdles? I've got autoconf and automake installed. It's not like I haven't tried to build other stuff from source before. I'm just overwhelmed with these errors I can't get around.   There's also the question of installing the necessary files that appear after make, but since I'm not that far, I don't know how to go about it. That is, if I can just &quot;sudo make install&quot;, or if something else is needed. But that bridge is nowhere in sight yet.

---

### Post by alexfish on 2010-01-20
hi

can you have a look here see if you can make any progress: also follow the links

[COLOR=#008C00]**[all variants]**[/COLOR] [How To : Conexant or Rockwell Modems]("http://ubuntuforums.org/showthread.php?t=1375694")

---

### Post by 10amrs on 2010-01-22
Unfortunately, none of those links solve anything for me. I've got the driver source downloaded and extracted but can't compile it. make just won't work b/c 1. there's no /usr/src/linux folder and 2. even if I create that folder there or make a symlink to the latest kernel folder in /usr/src, errors follow (no rule for modules in the folder, so the make process is interrupted). And I don't know where I might find the modules rule stuff and if a symlink linux to that folder (or some file) might kick off the whole process. Nor can I interpret the Makefile that well. I'm not too eager for messing with the kernel stuff anyway, but I wish I could've installed the required driver for the DSL adapter (not some ancient 56k pci modem like in those earlier links).

---

### Post by zweije on 2010-01-28
I'm running this on a debian system, and I'm working on a debian package that should automate the building of the modem driver. If you're interested you could try it out. Vincent.

---

### Post by 10amrs on 2010-02-02
I'd really appreciate that. I already sent you a PM but didn't get a response. It would definitely be helpful to have a less complicated installation of that driver, without the need for manual kernel-tweaking/-building.

---

