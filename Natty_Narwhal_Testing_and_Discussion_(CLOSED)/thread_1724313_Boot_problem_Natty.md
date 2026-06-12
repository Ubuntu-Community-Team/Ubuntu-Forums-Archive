---
title: "Boot problem: Natty"
date: 2011-04-08
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by willthong on 2011-04-08
Dear all,

I upgraded from Maverick to the Natty beta a little while ago. It all worked fine. Then, this morning, I was unable to boot. I got to GRUB, picked the first option and it went to the Ubuntu 11.04 with the dots, then returned this:

```
Begin: Loading essential drivers ... done.
Begin: Running /scripts/init-premount ... done.
Begin: Mounting root file system ... Begin: Running /scripts/local-top ... done
Begin: Running /scripts/local-premount ... done.
Begin: Running /scripts/local-bottom ... done.
done.
Begin: Running /scripts/init0bottom ... done.
fsck from util-linux-ng 2.17.2
/dev/sdb2: clean, 330110/2170880 files, 7302427/8683520 blocks
init: udevtrigger main process (367) terminated with status 1
init: udevtrigger post-stop process (372) terminated with status 1
init: udevmonitor main process (366) killed by TERM signal
init: ureadahead-other main process (428) terminated with status 4
init: udev-fallback-graphics main process (373) terminated with status 1
init: ureadahead-other main process (453) terminated with status 4
init:ureadahead-other main process (459) terminated with status 4
 * Starting mDNS/DNS-SD daemon [OK]
 * Starting network connection manager [OK]
 * Starting CUPS printing spooler/server [OK]
```

Then it doesn't load into GUI.

Help me!

Other info:
* I'm dual-booting with Vista
* I'm running it all on a Sony VAIO laptop (model number VGN-AR51M)
* I've tried recovery mode, but it basically does a similar thing

---

### Post by willthong on 2011-04-08
Sorry to ****BUMP**** but I really need my computer to work!

---

### Post by ChrisRatahi on 2011-04-08
*BUMP*

I'm having a similar problem. Updated to Natty two days ago. Have run numerous updates (nearly 300mb worth), and multiple error reports. Still cannot get Unity to load on it's own. Was going to start a new thread but figured bumping this may help solve both our problems. Luckily I run guake on netbook and can force unity to load. I attached an error output from this.

Thanks in advance.

---

### Post by uRock on 2011-04-08
Please wait 24 hours before bumping.

Moved to NNT&D

---

### Post by ChrisRatahi on 2011-04-08
Solved my own problem. On the login screen instead of logging into Ubuntu Netbook Edition (my default session), I changed it to Ubuntu. I've also changed that to my default session. Perhaps this may help others?

---

### Post by aasdfasdfg on 2011-04-19
I had the exact same issue as the OP as far as I can tell. For me, the issue was caused by a power outage during upgrade to Natty, leaving my system in a broken state. I think the main issue was that the udev package hadn't been upgraded while the kernel and other key packages had been upgraded, causing udev to fail during bootup.

Regardless of what actually was happening, I dug up a thread from two years ago [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/433943](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/433943)
where comment 2 provided a sure-fire way to recover from this kind of position.

All would be fine and dandy, if I had an optical drive to use with the bootable CD - which was not an option. Next logical option: bootable USB. Before going that route, I decided to see if I couldn't hack something together.

Luckily, something worked, so the good news is you DO NOT need another bootable medium to recover. I was able to recover as follows:
1) Pause boot during initramfs by passing in break=init into boot arguments; the easiest way I found was to modify the recovery mode of the most recent kernel installed in the grub menu by appending break=init and replacing ro with rw (you'll see why in a second)
2) Once dropped to the busybox prompt, open up a bash shell by typing bash at the prompt
3) Since we unlocked as rw instead of ro (not usually recommended but this is an exception), we are free to run something like dpkg --configure -a or anything else to restore your broken system. Or, just follow the instructions given in the previous thread I referenced, picking up after he has successfully chroot'ed into the broken system. Note: if you need to download packages on the fly to fix your system, be sure to have an ethernet cable handy (I take wifi for granted but in this case, the necessary drivers haven't loaded yet for wifi)

That should more or less restore your system to a usable state, let me know how it goes.

---

### Post by dino99 on 2011-04-19
booting into recovery mode and then choosing repair package may help

---

