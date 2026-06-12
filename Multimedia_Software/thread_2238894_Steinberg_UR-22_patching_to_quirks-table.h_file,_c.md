---
title: "Steinberg UR-22 patching to quirks-table.h file, cannot compile kernel"
date: 2014-08-10
forum: Multimedia Software
---

### Post by rod-polako on 2014-08-10
Hello everyone,
    I'm trying to get some assistance in appling a patch to the quirks-table.h file in ALSA so that my Steinberg UR-22 can function.

I discovered at [http://linux-audio.4202.n7.nabble.com/Support-for-Steinberg-UR22-Yamaha-USB-chipset-0499-1509-td82888.html](http://linux-audio.4202.n7.nabble.com/Support-for-Steinberg-UR22-Yamaha-USB-chipset-0499-1509-td82888.html) and at [http://ubuntuforums.org/showthread.php?t=2150401](http://ubuntuforums.org/showthread.php?t=2150401) that adding an entry to the quirks-table.h file will enable it to work.   After much searching on the computer for this file with no success, I finally learned that this is a source code file and not installed by default on a regular installation.  I've since learned that this means compiling a kernel.

I then followed the instructions at [https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel](https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel), then [http://www.linuxmao.org/Steinberg+UR22](http://www.linuxmao.org/Steinberg+UR22), also [http://mdcc.cx/debian/module-assistant_patched_alsa.txt](http://mdcc.cx/debian/module-assistant_patched_alsa.txt), and then finally [http://www.remastersys.com/forums/index.php?topic=2698.0](http://www.remastersys.com/forums/index.php?topic=2698.0) that each explain differently how to download and build a new kernel but none of them have worked.  Each of them give errors when attempting to either build or boot.  There were several others I have visited but the instructions were very old (10.04 or even earlier).  This [https://www.youtube.com/watch?v=cc8082h0fS0](https://www.youtube.com/watch?v=cc8082h0fS0) was also tried but did not work.

Every new site I visit provides different instructions that don't match what I'm seeing and seem to require new tools or dependencies so I'm adding packages like crazy and STILL nothing works.  It can't possibly be this hard to build a kernel with a really trivial change, can it?

There was also some mention of just recompiling ALSA itself but when I download the alsa-source package I can't find the file I need to modify and then even if I did I don't know what to do after that.  Research here just pointed me to module-assistant again but with no specific build/installation instructions.

I see that this is been brought up as a bug ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1317244](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1317244)) but there is no information on when a possible fix would be available.  The patch there is for an older kernel and I don't know if installing that will mess up my system.

I am currently running Lubuntu 14.04 amd64 with kernel 3.13.0-24-generic (at least this is what is output from uname -r).  The system itself is an HP dx7500 (Core 2 Duo with 8GB ram) and runs perfectly fine.

My output of lsusb -v is exactly the same as the first link above so there isn't an issue with the device itself.  It also works perfectly in Windows.

Could anyone please provide some basic step-by-step instructions on how to download, modify and then build a new kernel for 64-bit on 14.04?  

In the meantime, kernel compile #7 (hour: who knows at this point) is ongoing...

Thanks in advance for any help you can provide.

Rod

---

### Post by rod-polako on 2014-08-10
Just a followup,
   Looks like 7th time was the charm...

For any poor soul that needs to do this, I followed the instructions on [http://www.remastersys.com/forums/index.php?topic=2698.0](http://www.remastersys.com/forums/index.php?topic=2698.0) and it finally worked.  Don't know why it worked this time but I'll take it. 

Rod

---

