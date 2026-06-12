---
title: "Dell OEM Radeon HD 2400 Core2 64bit at wits end"
date: 2007-12-07
forum: Multimedia &amp; Video
---

### Post by wintrmute on 2007-12-07
Hi,
I have a Dell PC running Ubuntu Gutsy 64bit, with a Core 2 Quad CPU, 4 GB DDR2 ram, and one problematic beast: A Dell OEM version of the PCI-E AMD Radeon HD 2400 graphics card.

I am a very experienced Linux user, and I have successfully used the ATI fglrx drivers with X800 and X700 video cards before. However I cannot for the life of me get it to work with the 2400 card.

As soon as DRI is enabled in xorg.conf, any attempt to load X results in a blank screen and hard lockup. I am using the latest ATI Catalyst 7.11 drivers (internal module version 8.43.2). I have tried using the install to create .deb files and then install them with module-assistant, and I've also tried compiling and installing it manually.

I have been using the Ubuntu default kernel, and also tried using a self-compiled vanilla 2.6.23.9 kernel (both SLAB and SLUB).

According to the web, the drivers I'm trying /should/ support this card. I can't work out what I am doing wrong!
Does anyone have any advice for me? Can anyone confirm they have the Dell OEM version of this card working? How about the genuine version?

lspci lists the card as:
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 94c1

Capturing the /var/log/Xorg.0.log output with my /var partition mounted synchronously is unhelpful - the log output is almost identical to how it looks when I load with DRI disabled (with works), apart from the bits saying DRI enabled successfully, etc..

Is there other info that would help you?

Thanks in advance for any help,
Toby

---

### Post by wintrmute on 2007-12-09
*bump*

Anyone? Anyone? Beuller?

---

### Post by glenstewart on 2007-12-16
See this article.  Although it may be intended for Ubuntu, I used it with my Kubuntu setup using Radeon 2400 HD PCI-e on 64-bit, and it worked well.

[http://ubuntuforums.org/showthread.php?t=606859&highlight=radeon+2400]("http://ubuntuforums.org/showthread.php?t=606859&highlight=radeon+2400")

---

### Post by wintrmute on 2007-12-16
Thanks for the link.

I've done pretty much that, but unfortunately it all falls down for me whenever X starts - machine just reboots. Only thing I haven't tried is the clean install of Ubuntu, but this install is fairly clean to start with - only installed a few weeks prior - and it's a PITA to backup and reinstall from scratch, and I can't really see how that'd help.

It's a pity this is a work machine, otherwise I'd have just returned the bleeding ATI card and bought an nVidia! (it's also a PITA because we have a whole dept of these machines and this issue is making the Linux desktop project look terrible..)

---

### Post by wintrmute on 2007-12-16
I'm wondering if there's something specific about the Dell OEM version of these cards that makes them barf?

---

### Post by tgalati4 on 2007-12-17
Try loading a Fedora or OpenSuse Live CD.  The hardware detection is slightly different and the graphics drivers are somewhat tweaked.  If another distro boots successfully then print out the xorg.conf to capture the modlines.

I would imagine that OEM cards are built to low-cost specifications.  "Give me a $100 graphics card but we'll only spend $8 on it.  Otherwise we'll go with an Intel chipset."

So if ATI or the OEM vendor wants the business, they come up with creative ways to reduce the cost.  Reduce on-board memory, reduce mosfets (power chips), reduce cache memory.  Just about anything is game.

Try running some benchmarks in Windows and compare:

[http://www.tomshardware.com/2007/10/29/geforce_8800_gt/index.html](http://www.tomshardware.com/2007/10/29/geforce_8800_gt/index.html)

If you don't get the same numbers as the Real Deal cards in Windows then you can safely assume that your OEM card as been "Dellified".

---

### Post by wintrmute on 2007-12-17
I'd be happier with the Intel chipset! they have open-source drivers and work reliably >:/

---

### Post by uraslacker on 2008-02-29
It work(ed) for me until I upgraded to 4GB of RAM.  Now, I see the same symptoms as you.

It appears that there's a problem with the ATI proprietary drivers, 64-bit Linux, and 4GBytes of RAM.  With 2GB of RAM my machine works just fine.

I, too, am only looking for functionality, and would take (will take) the non-proprietary (Xorg) driver....once it supports the HD 2400.

I've just identified the issue, and plan to do some searching on the ATI forums (etc.) to see if this is a known problem.  In the meantime, I have to _settle_ for a 2GB system :-(

---

### Post by uraslacker on 2008-03-01
Ok...I got the radeonhd (Xorg) driver functional, following the instructions, to build radeonhd from git sources, by tgilber1 given here:

[http://ubuntuforums.org/showthread.php?t=641247](http://ubuntuforums.org/showthread.php?t=641247)

I combined this with the iommu=noaperture kernel option (edited Grub menu.lst), like so:

```
kernel          /vmlinuz-2.6.22-14-generic root=/dev/sda1 ro iommu=noaperture
```

I'm pretty sure that this last option is not necessary, but I don't feel like futzing any longer tonight.  Jeez!  I, **finally**, have a functional HD2400Pro card with 4GB of RAM....  Now, I can get some real work done!

...and one more piece of advice:  Do NOT attempt to use fglrx, again, for a while!  Anytime you use it, you will have to reboot, as the crapola fglrx driver doesn't exit cleanly.  I sure wish I had read that on the radeonhd Wiki...earlier.  It would have saved me an hour (or so) of tinkering!

---

### Post by uraslacker on 2008-03-01
It's still not completely stable, and I have to use the

```
 Option "NoRandR"
```

option, as the radeonhd Xorg wiki suggests.  It also appears that the iommu=noaperture kernel option **is** necessary, contrary to what I stated earlier.  My feeling is that this is a BIOS, kernel, AGP, 64-bits, _and_ >=4GB of RAM issue.  Lovely!

Here's a list of bugs I'm currently tracking:

[LIST]
[*]Freedesktop (Xorg) #[8513]("https://bugs.freedesktop.org/show_bug.cgi?id=8513").
[*]ATI proprietary #[941]("http://ati.cchtml.com/show_bug.cgi?id=941").
[/LIST]

I haven't (yet) found the "magic" recipe (for my hardware) to always get functional X, as it appears that DPMS events will send me back to some unstable state.

QUICK UPDATE:  It appears that when the monitor is turned off (via DPMS or the power switch), the radeonhd driver has difficulty regaining sync....most of the time requiring me to CTRL-ALT-BACKSPACE and restart X and, occasionally requiring a reboot.

---

### Post by zappbrannigan on 2008-03-04
Please dump your mtrr table with:
cat /proc/mtrr
I got this:
```

reg00: base=0xd0000000 (3328MB), size= 256MB: uncachable, count=1
reg01: base=0xe0000000 (3584MB), size= 512MB: uncachable, count=1
reg02: base=0x00000000 (   0MB), size=4096MB: write-back, count=1
reg03: base=0x100000000 (4096MB), size= 512MB: write-back, count=1
reg04: base=0x120000000 (4608MB), size= 256MB: write-back, count=1

```

My system hangs with the old table. I've changed it to:
```

reg00: base=0x00000000 (   0MB), size=2048MB: write-back, count=1
reg01: base=0x80000000 (2048MB), size=1024MB: write-back, count=1
reg02: base=0xc0000000 (3072MB), size= 256MB: write-back, count=1
reg03: base=0x100000000 (4096MB), size= 512MB: write-back, count=1
reg04: base=0x120000000 (4608MB), size= 256MB: write-back, count=1

```
Now the 8-01 fglrx driver works!

---

### Post by Yellow Pasque on 2008-03-04
You can turn DPMS off with the appropriate Option line in the monitor section of xorg.conf. I forget the exact syntax (Disable, Off?), but you seem intelligent enough to look that up yourself. :)

---

### Post by wintrmute on 2008-03-04
> **zappbrannigan said:**
> Please dump your mtrr table with:
cat /proc/mtrr
/snip/
Now the 8-01 fglrx driver works!

Interesting - do you know what in particular caused that to fix it?

I chucked the Radeon HD2400 card a while back and swapped to another model that worked, so can't give you relevant mtrr stuff right now, but will swap back to it and dump the variables sometime.

It's a pity that Windows "just works", as all the difficulties us Linux people have had with ATI here at work have hurt the effort to justify linux-based desktops here.

Thanks for the info!

---

### Post by wintrmute on 2008-06-10
> **zappbrannigan said:**
> Please dump your mtrr table with:
cat /proc/mtrr
I got this:
```

reg00: base=0xd0000000 (3328MB), size= 256MB: uncachable, count=1
reg01: base=0xe0000000 (3584MB), size= 512MB: uncachable, count=1
reg02: base=0x00000000 (   0MB), size=4096MB: write-back, count=1
reg03: base=0x100000000 (4096MB), size= 512MB: write-back, count=1
reg04: base=0x120000000 (4608MB), size= 256MB: write-back, count=1

```

My system hangs with the old table. I've changed it to:
```

reg00: base=0x00000000 (   0MB), size=2048MB: write-back, count=1
reg01: base=0x80000000 (2048MB), size=1024MB: write-back, count=1
reg02: base=0xc0000000 (3072MB), size= 256MB: write-back, count=1
reg03: base=0x100000000 (4096MB), size= 512MB: write-back, count=1
reg04: base=0x120000000 (4608MB), size= 256MB: write-back, count=1

```
Now the 8-01 fglrx driver works!

Hi,
I've swapped back to the HD2400 now, so can post the MTRR tables, which are:
```

$ cat /proc/mtrr 
reg00: base=0x00000000 (   0MB), size=65536MB: write-back, count=1
reg01: base=0xbef00000 (3055MB), size=   1MB: uncachable, count=1
reg02: base=0xc0000000 (3072MB), size=1024MB: uncachable, count=1

```

Note that this is with 3GB of RAM installed; I'll try and find the other 1GB stick to experiment with it again too..

---

