---
title: "Network manager Update still bad?"
date: 2011-01-06
forum: Networking &amp; Wireless
---

### Post by Rrory on 2011-01-06
Arg, I just removed the bad update  2. 6.35-24
now update manager wants me to install new ones; is it still the 'bad' update that messed up my wifi or has it been fixed? Heelp.

Rory

---

### Post by gordintoronto on 2011-01-06
I'm using that version of the kernel. My wifi has always worked. Perhaps there is something specific to your wireless adapter? If so, you should mention what one you have, as displayed by lspci or lsusb.

---

### Post by PatchesTheCaveman on 2011-01-07
Rrory:  The bad update is called *linux-image-2.6.35-24-generic*, but there will be others it might try to install based on what you have installed that end with the same version, e.g. *linux-headers-2.6.35-24-generic*.  You can safely install other updates, but make sure that one is unchecked.  

Note tht you never, ever want to install this update.  When Canonical fixes this bug the working version should be *2.6.35-25-generic*.

gordintoronto:  I helped this poster previously and we did determine that the broken kernel caused problems with his hardware.  While many users have no trouble, it does break quite a few devices, more than just wireless cards:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/695509](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/695509)

---

### Post by Rrory on 2011-01-07
PatchcesTheCaveman:  okay thanks,now I understand! will do. Your advice is  very clear and easy to follow.

gordintoronto; I had no idea what a kernel is!. So I didn't know what to do with the new update. I get it now.  I think KIS is a helpful acronym here for the non or new techie set.

:KS
Rory

---

### Post by PatchesTheCaveman on 2011-01-07
The [kernel](http://en.wikipedia.org/wiki/Kernel_(computing)) is the central, critical part of an [operating system](http://en.wikipedia.org/wiki/Operating_system) that provides an interface between normal programs (["userspace"](http://en.wikipedia.org/wiki/Userspace)) and the physical hardware that makes up your computer.

The [Linux kernel](http://en.wikipedia.org/wiki/Linux_kernel) was created by [Linus Torvalds](http://en.wikipedia.org/wiki/Linus_Torvalds) and combined with the [GNU](http://en.wikipedia.org/GNU's_Not_Unix) [toolset](http://www.gnu.org/software/coreutils/) mostly written by [Richard Stallman](http://en.wikipedia.org/wiki/Richard_Stallman) to form [what some call the GNU/Linux operating system](http://en.wikipedia.org/wiki/GNU/Linux_naming_controversy) but is usually just referred to as [Linux](http://en.wikipedia.org/wiki/Linux).

Windows also has a kernel.  If you CTRL+ALT+DEL on a Windows system and go to the processes tab of the Task Manager, you'll see a program running called [*ntoskrnl.exe*](http://en.wikipedia.org/wiki/ntoskrnl.exe).  Mac OS X also uses a kernel called [XNU](http://en.wikipedia.org/wiki/XNU).

The More You Know!  :-D

---

