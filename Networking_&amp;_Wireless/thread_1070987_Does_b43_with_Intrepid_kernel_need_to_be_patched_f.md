---
title: "Does b43 with Intrepid kernel need to be patched for packet injection?"
date: 2009-02-15
forum: Networking &amp; Wireless
---

### Post by kevdog on 2009-02-15
Im currently running the b43 driver with the 2.6.27-11-generic kernel.  Do I need to patch either the b43 sources or the mac layer in order to be able to perform packet injection?

---

### Post by kevdog on 2009-02-16
I can answer part of this question after further research myself.  The b43/openfwwf sources do not need to be patched with kernel >=2.6.27 (Intrepid Kernels).

Aircrack-ng recommends patching of the mac80211 module even in these kernels, however I'm not sure the real reason.  From what I understand its to speed up the IV collection process.  I believe however even without the patch, packet injection will work with the stock mac80211 module.  I need confirmation of this assumption however and have failed to find it thus far.

---

### Post by Ayuthia on 2009-02-16
> **kevdog said:**
> I can answer part of this question after further research myself.  The b43/openfwwf sources do not need to be patched with kernel >=2.6.27 (Intrepid Kernels).

Aircrack-ng recommends patching of the mac80211 module even in these kernels, however I'm not sure the real reason.  From what I understand its to speed up the IV collection process.  I believe however even without the patch, packet injection will work with the stock mac80211 module.  I need confirmation of this assumption however and have failed to find it thus far.

You are correct.  I have tested it without the patches on 2.6.27 and it does work.  However, it does take some time (~45 minutes for WEP :( ) before it is able to produce the results.

I am currently compiling 2.6.28.5 with the patch to see if it works.  I did not have too much luck with it last time in 2.6.27, but I will try again if I am successful with 2.6.28.5.

---

### Post by kevdog on 2009-02-16
Maybe Im just a novice however it only took me 1:45 (1 minute 45 seconds) with WEP with the unpatched MAC layer.  I can find instructions how to patch this module correctly beginning with the 2.6.27 kernel.  I found the patch, patched the kernel sources, but didn't know how to install the patched modules. sudo make modules_install kept failing for me.  Note that I wasn't attempting to compile the entire kernel source only something similar to these instructions (Please note the word SIMILAR):

sudo patch -p1 < mac80211_2.6.24.4_frag.patch
sudo make net/mac80211/mac80211.ko drivers/net/wireless/b43/b43.ko drivers/net/wireless/b43legacy/b43legacy.ko
sudo make modules_install

---

### Post by Ayuthia on 2009-02-16
> **kevdog said:**
> Maybe Im just a novice however it only took me 1:45 (1 minute 45 seconds) with WEP with the unpatched MAC layer.  I can find instructions how to patch this module correctly beginning with the 2.6.27 kernel.  I found the patch, patched the kernel sources, but didn't know how to install the patched modules. sudo make modules_install kept failing for me.  Note that I wasn't attempting to compile the entire kernel source only something similar to these instructions (Please note the word SIMILAR):

sudo patch -p1 < mac80211_2.6.24.4_frag.patch
sudo make net/mac80211/mac80211.ko drivers/net/wireless/b43/b43.ko drivers/net/wireless/b43legacy/b43legacy.ko
sudo make modules_install

I have not compiled modules individually, but it looks right.

As for me, I am not for sure if the issue is with my card or my router.  The packet injection does not produce any ARP requests for me all the time (patched or unpatched).

---

### Post by kevdog on 2009-02-16
I actually ran into these instructions for compiling the mac80211 module individually.

[http://aircrack-ng.org/doku.php?id=links#compiling_kernels](http://aircrack-ng.org/doku.php?id=links#compiling_kernels)

 Another question that comes up is how to compile a single driver module. Here are the basics:

First, cd to the directory which contains the source files to be compiled. It assumes you have patched the source if required.

 make CONFIG_ZD1211RW=m -C /lib/modules/`uname -r`/build M=`pwd` clean
 make CONFIG_ZD1211RW=m -C /lib/modules/`uname -r`/build M=`pwd` modules
 make CONFIG_ZD1211RW=m -C /lib/modules/`uname -r`/build M=`pwd` modules_install
 depmod -ae

In the above:

    *
      “CONFIG_ZD1211RW=m” If the module is not “enabled” in the kernel config then you need to set the variable for that specific module to “m” for module. IE Enable it. It is not always required and must be changed to the specific driver you are trying to compile.
    *
      ”-C” This has to be set to the location of your kernel source tree. ”-C /lib/modules/`uname -r`/build” will typically work correctly.
    *
      “M=” This has to be set to the location of the source files to be compiled. If you have already changed to the directory containing the source files then “M=`pwd`” will typically work correctly. pwd specifies the current directory you are in.

There are some considerations regarding installing a single module. You will need to ensure that the new module overwrites the existing one in /lib/modules. Sometimes it ends up being placed in a different location in the /lib/modules tree. If this happens then be sure to delete to the old version and run “depmod -ae”.

Alternatively, manually copy the newly created .ko kernel modules over the existing ones located in the /lib/modules tree


What I ended up with after the above process was the mac80211.ko file that I patched within the /usr/src/linux-source-2.6.27/net/mac80211 folder.  

I backed up the original mac80211.ko file located in /lib/modules/2.6.27-11-generic/kernel/net/mac80211 and copied my compiled version into this folder and reran sudo depmod -ae

If someone could verify this is the correct process it would be great.

---

### Post by kevdog on 2009-02-19
Just a few points.  From the IRC channel it seems the need to patch the mac80211 wireless stack and b43 (in some kernel editions) is for the ability to perform a fragmentation attack or a aireplay #5 attack.  

I went ahead and patched my mac80211 stack (a few different ways), however my fragmentation attack still doesn't work.  I using kernel version 2.6.27-11

Just wondering if anyone has performed a successful fragmentation attack using the b43 driver with any kernel version.  If yes, can you tell me the kernel version, and your method of success.  Did you need to patch the b43 source and/or the mac80211 wireless stack?

Thanks a lot.

---

### Post by gimpchop on 2009-02-21
> **Ayuthia said:**
> I have not compiled modules individually, but it looks right.

As for me, I am not for sure if the issue is with my card or my router.  The packet injection does not produce any ARP requests for me all the time (patched or unpatched).

Hi I have the exact same prob allthough I have managed to crack 1 of my routers a bthomehub on wep but my linsys seems. To produce the same prob as you. I use the caox live cd with b43 drivers I think they r pached. Any input would be greatfully receved thanks.

---

### Post by kevdog on 2009-02-21
I think I was able to patch the mac80211 layer (although I know of 3 different ways to do this).  Additionally I did not patch the b43 stack since according to 2.6.27 documentation, they say this is unecessary.  When running fragmentation attack, I get to the point where it states Use this key, I select yes, and then the injection of this packet fails, meaning the AP fails to respond.  LLC packets are constantly tried, and then eventually the process repeats, asking me to use a different key.

That has been my experience.

---

