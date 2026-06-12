---
title: "Recompiling kernel with SLAB to get suspend working with fglrx?"
date: 2007-12-09
forum: Multimedia &amp; Video
---

### Post by Gadren on 2007-12-09
I have a Dell Inspiron 6400/e1505 with an ATI X1400 running Ubuntu 7.10.  Suspend and hibernate don't work, and I've heard that one way to get it working without going to another driver or downgrading to Feisty is to recompile the kernel with SLAB.

Would this be a good thing to try?

And if so, how exactly would I do it?

---

### Post by steveneddy on 2007-12-09
[This]("http://ubuntuforums.org/showthread.php?p=3900319#post3900319") worked for me.

---

### Post by Gadren on 2007-12-09
Thanks, but I've gone through all these various fixes.  It's been shown that in Gutsy, for the X1400, none of them work.  According to the ATI Linux Wiki, the only solutions are:

> - Boot using the older kernel (ver 2.6.20)

- Return to Feisty (with 2.6.20 kernel, and apply specific solutions: see Feisty installation guide).

- Use default Mesa Drivers (the easiest way is to disable ATI driver from Restricted Driver Manager).

- Recompiler your Kernel to use SLAB. 

That last one sounds like the one for me, but I need help knowing if it actually would be the best way to go, and, if so, how exactly to do it.

---

### Post by TrinitronX on 2008-02-05
I've been trying to get suspend working on a Gateway C-140x, with no luck so far.
In the default Gutsy install it will go to sleep and I can see the slow blinking LED showing that it made it into suspend.  However, it just wouldn't come back from that.

I read a couple threads, tried changing settings in /etc/default/acpi-support, which didn't help at all.  Then I read about the SLUB/SLAB issue, and decided to build the zen kernel from source (a patched form of 2.6.24, which some have been able to get it working in.. it also had iwl3945 wifi drivers that I needed), making sure to select SLAB in menuconfig.  I had to follow the two edits here to one file in the source to get fglrx to actually compile, as it was an -rt kernel.  [http://gentoo-wiki.com/HOWTO_ATI_Drivers#Build_ati-drivers_on_rt-kernels_failed](http://gentoo-wiki.com/HOWTO_ATI_Drivers#Build_ati-drivers_on_rt-kernels_failed)

After this, everything compiled fine, fglrx built fine, kernel boots ok, DRI and compiz are working.... but still no suspend!
However, this time, when I suspend it, I never even see the blinking LED... the screen goes dark, and LED remains lit without blinking... leading me to think something isn't going well along the way to suspending this time.
Has anyone gotten suspend working with fglrx and an ATI Radeon X2600 HD?

---

### Post by TrinitronX on 2008-06-24
Fixed suspend by using radeonhd driver.  This driver does not yet support DRI accelleration.  For me, suspend support has a higher priority than 3D accelleration, so if this is the case, I recommend using this driver if you have a compatible card.

---

