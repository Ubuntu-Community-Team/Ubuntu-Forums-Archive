---
title: "kernel 2.6.35-999 generic and ndiswrapper"
date: 2010-06-29
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by anewguy on 2010-06-29
Not getting any help on Absolute Beginners Forum, so I hope I'm in the right place now.

I have problems with USB hot-plug devices not being recognized at all by the current Lucid kernel.  I did some searching and found a bug report on launchpad and it said to use a newer kernel.

I found a wiki which walked me through downloading the "current mainline kernel", which says 2.6.35-999 generic.  I installed it and the headers, and have 3 issues at boot:  ERST (?) table not found, some kind of message about power"something"K8, and then the default boot line for it uses vga=7xx (forgot the exact numbers).  I've been ignoring the ERST and power"something"K8 messages and manually edit the boot line from the grub menu to remove the vga=xxx stuff in order to boot (with the vga=xxx left in I never get to the desktop and my monitor says no signal).

However, this kernel does fix the hot-plug USB devices problem.

I read somewhere on the net while trying all of this that this kernel is going to be used in Meerkat (love those little guys!) so I thought I'd try posting here with the main issue stopping me from continuing with this kernel:

I can run ndiswrapper from the command line and everything loads fine.  However, there appears to be no ndiswrapper kernel module, as it doesn't show in lsmod and trying to modprobe it returns a message about ndiswrapper not being found.  I'm suspecting this may mean I need to rebuild ndiswrapper with the new kernel headers, etc.,  but I really don't know.

If at all possible, I'd like to get this working, but also have a fall-back plan to the current Lucid kernel (2.6.32-22 generic) that I'm running.  This would mean some way to make ndiswrapper work again in the current Lucid kernel *if* I have to rebuild it for the 2.6.35-999 generic kernel.

I hope I have this in the correct place now, and would appreciate any help.  I have Ubuntu on my netbook as well, so I actually wouldn't mind testing Maverick Meerkat on my desktop, but I have no idea how to go about doing so.

Thanks in advance!

Dave ;)

---

### Post by dino99 on 2010-06-29
why are you using vanilla kernel and ndiswrapper ?
better to use maverick repo to get latest tuned kernel (35-6)

---

### Post by Starks on 2010-06-29
You need 2.6.34 or earlier. 2.6.35 won't work at all with ndiswrapper.

Wait for Leann to fix this.

---

### Post by anewguy on 2010-06-29
> **dino99 said:**
> why are you using vanilla kernel and ndiswrapper ?
better to use maverick repo to get latest tuned kernel (35-6)

Mainly because I've never done anything like this before - so I followed the wiki which had a clickable link that just said "cuurent" and started the download of 2.6.35-999.  I don't even know where to find the maverick repo.

[quote=starks]Starks  	

You need 2.6.34 or earlier. 2.6.35 won't work at all with ndiswrapper.[/quote]

Okay.  

Now, as mentioned, I wouldn't mind just putting the dev release of Maverick on my desktop to just be a tester.  I don't do anything fancy at all, unless you consider 1 program in C that I wrote that uses libusb calls and requires a special udev rule.

So......if I can be just a dumb user testing Maverick, and if the kernel supplied with it will support ndiswrapper and hot-plug USB devices, I would be happy to do so if you can point to where I need to start.

Thanks for the help!

Dave ;)

---

### Post by anewguy on 2010-06-29
Here's the wiki I followed:

[https://wiki.ubuntu.com/KernelTeam/MainlineBuilds]("https://wiki.ubuntu.com/KernelTeam/MainlineBuilds")

I just followed what it said there.

Since it seems that I'm not supposed to post here, and my question isn't getting any answers on the beginners forum, I'm just going to close them both.

I was hoping there would be a solution to actually using a hot-swap USB drive without having to have it plugged in and turned on at boot time with the current Lucid release.  The launchpad bug report for this problem is what got me started on this whole thing.

I guess when I need to hot-swap I'll boot Windows and wait for Ubuntu to catch up.

BTW - I tried the 2.6.34 kernel from the download site that was listed as Lucid.  Still no ndiswrapper.  I think the launchpad solution should be directed to something better to follow if the wiki I was pointed to isn't the way to do things.  It gave no warnings about ndiswrapper or anything else.

---

### Post by Starks on 2010-06-29
You need ndiswrapper-dkms too.

Also, these worked for me to get ndiswrapper up and running...

[http://launchpadlibrarian.net/49660925/linux-headers-2.6.34-5_2.6.34-5.14_all.deb](http://launchpadlibrarian.net/49660925/linux-headers-2.6.34-5_2.6.34-5.14_all.deb)
[http://launchpadlibrarian.net/49660936/linux-headers-2.6.34-5-generic_2.6.34-5.14_i386.deb](http://launchpadlibrarian.net/49660936/linux-headers-2.6.34-5-generic_2.6.34-5.14_i386.deb)
[http://launchpadlibrarian.net/49660935/linux-image-2.6.34-5-generic_2.6.34-5.14_i386.deb](http://launchpadlibrarian.net/49660935/linux-image-2.6.34-5-generic_2.6.34-5.14_i386.deb)

You gotta install them together with a sudo dpkg -i *2.6.34-5.14*.deb command.

---

