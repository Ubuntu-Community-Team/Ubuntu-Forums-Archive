---
title: "Wired ethernet repeatedly disconnects and reconnects"
date: 2011-06-09
forum: Networking &amp; Wireless
---

### Post by ratcheer on 2011-06-09
I have a fresh install of Ubuntu 11.04 on a brand new PC. Every minute or so, the wired ethernet connection drops and then a few seconds or minutes later, it comes back on. This is not happening on any of the other PC's on my LAN, but since this is a new PC with a new install of Ubuntu, I have no idea whether the problem is hardware or OS related.

However, the old PC (also Ubuntu) on this LAN port did not have this problem, nor did this new computer while it was running Windows 7. So, I tend to believe that Ubuntu is the problem. Maybe it is related to the NIC driver?

I have rebooted the PC several times, with no improvement. I also rebooted the LAN router a while ago, but that made no difference, either.

How can I troubleshoot this problem?

Thanks,
Tim

---

### Post by ratcheer on 2011-06-09
It seems to be a bug in the kernel. I signed up with an "affects me too" on bug 770708. Problems with driver r8169 have been continuing since about 2006.

I am going to the Realtek web site to try to find a better driver.

Tim

---

### Post by ratcheer on 2011-06-09
I found the driver for my card. According to the Realtek site, Ubuntu has not even loaded the correct driver for my card.

I downloaded the correct driver, r8168, and followed the instructions to install it. The script correctly unloaded my bad module, but failed trying to create the new one. I'm not sure what to do next.

```

sudo ./autorun.sh
[sudo] password for tim: 

Check old driver and unload it.
rmmod r8169
Build the module and install
make[2]: *** No rule to make target `NIC'.  Stop.
make[1]: *** [modules] Error 2
make: *** [modules] Error 2


```

Thanks,
Tim

---

### Post by ratcheer on 2011-06-10
I found more detailed instructions on another web site for installing the correct driver. But they fail, too.

```

sudo make all
[sudo] password for tim: 
make -C src/ clean
make[1]: Entering directory `/home/tim/Realtek NIC Driver/r8168-8.024.00/src'
rm -rf *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags .tmp_versions Module.symvers Modules.symvers Module.markers *.order
make[1]: Leaving directory `/home/tim/Realtek NIC Driver/r8168-8.024.00/src'
make -C src/ modules
make[1]: Entering directory `/home/tim/Realtek NIC Driver/r8168-8.024.00/src'
make -C /lib/modules/2.6.38-8-generic/build SUBDIRS=/src modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.38-8-generic'
scripts/Makefile.build:44: /src/Makefile: No such file or directory
make[3]: *** No rule to make target `/src/Makefile'.  Stop.
make[2]: *** [_module_/src] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/tim/Realtek NIC Driver/r8168-8.024.00/src'
make: *** [modules] Error 2

```

It basically looks like a more extensive version of the same error.

Would someone please give me a hand?

Tim

---

### Post by ratcheer on 2011-06-10
Never mind, I figured out that the spaces in the parent directory name were throwing the scripts a curve ball. I renamed "Realtek NIC Driver" to "RealtekNICDriver" and the make ran, successfully.

This is a big bug in Ubuntu that has been going on for several years. There is a correct driver and a wrong driver for this hardware, and they insist on installing the wrong driver. From what I can see, it is very common hardware, too. There are many, many bug reports about it on launchpad. I wonder why they refuse to fix it? I am going to file a new bug just to make sure they have to look at it, again.

Tim

---

### Post by ratcheer on 2011-06-10
Added Answers #160984 on Launchpad.

Tim

---

