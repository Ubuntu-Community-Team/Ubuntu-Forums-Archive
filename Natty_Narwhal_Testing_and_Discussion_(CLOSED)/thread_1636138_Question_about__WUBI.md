---
title: "Question about  WUBI"
date: 2010-12-02
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by xcadenxbrewerx on 2010-12-02
So im trying to install Ubuntu 11.04 i got alpha 1, and i use win rar, i opened it clicked wubi and it is offering me 10.10?
 
I probably sound stupid but can someone help?

---

### Post by alzie on 2010-12-02
Quick search shows that it is reported as a bug.  It appears the WUBI installer is still for 10.10.

[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=10191955](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=10191955)

says that the next build hopes to have the corrected WUBI version.

[https://bugs.launchpad.net/ubuntu/+bug/684076](https://bugs.launchpad.net/ubuntu/+bug/684076)  <<correct link ooops

---

### Post by xcadenxbrewerx on 2010-12-02
alright but your link sends me to reply to this thread and should i jsut go into ubuntu 10.10 and do the terminal command?

---

### Post by cariboo on 2010-12-02
As alzie said there isn't a wubi version for 11.04 yet, you'll have to install it on an open partition, or wait until there is the correct version available.

---

### Post by bcbc on 2010-12-02
you could try wubi-r200.exe at [http://people.canonical.com/~evand/wubi/natty/](http://people.canonical.com/~evand/wubi/natty/)

I haven't...

---

### Post by Arrowstar on 2010-12-02
> **bcbc said:**
> you could try wubi-r200.exe at [http://people.canonical.com/~evand/wubi/natty/]("http://people.canonical.com/%7Eevand/wubi/natty/")

I haven't...

I just tried this.  The new executable appears to grab the correct ISO, but the WUBI install does not boot correctly.  It fails shortly after the MS bootloader and does not display GRUB.

---

### Post by bcbc on 2010-12-03
There is a problem with the wubildr. I installed it, and it hung at: Try (hd0,0) FAT32: 

I copied over a wubildr.mbr and wubildr from a previous install to c:\, didn't help. I mounted and copied the same files over the first hidden restore partition which also gets these apparently.
Then it booted to a grub prompt.

From there, I could get the wubi install going by:
configfile (hd0,msdos2)/ubuntu/winboot/wubildr.cfg

During the install I got a screen:
> Bootloader install failed

How would you like to proceed:
1. Choose a different device to install the bootloader on (drop down box empty)
2. Continue without a bootloader
3. Cancel the installation
I selected 2 and it warned:
You will have to manually install a bootloader to start Ubuntu

Then it finished. On reboot, I got a grub prompt. This time I had to manually boot it as the wubildr.cfg trick didn't work:
error: no such device /ubuntu/install/boot/grub/grub.cfg
error: no such device /grub.cfg
...

After that, as I said, I could boot manually. Couldn't use gnome - probably a graphics card issue - screen was zoomed in. From command line I rebuilt the wubildr file, but it didn't help the booting.

So... I guess there's still a bit of work to be done.

---

### Post by retskrad on 2011-01-20
does anyone have a solution?

---

### Post by obsama1 on 2011-04-05
Just download 10.10 and then update to 11.04. Heres how(the instructions to work, the download link is just Oout of Date): [http://www.ubuntu.com/testing/natty/alpha1](http://www.ubuntu.com/testing/natty/alpha1)

---

### Post by bcbc on 2011-04-06
a fresh install on wubi.exe rev206 should work. An upgrade will succeed but likely fail until the patch for  [https://bugs.launchpad.net/wubi/+bug/742967](https://bugs.launchpad.net/wubi/+bug/742967) is released.

---

