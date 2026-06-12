---
title: "Ack! Kernel recompiled, how do I put wireless back?"
date: 2006-03-05
forum: Networking &amp; Wireless
---

### Post by SirTode on 2006-03-05
Ok, as the header suggests, I just recompiled the kernel (was necessary in order to get my mouse driver installed, or so I was told), and everything seems to work fine, EXCEPT my wireless driver is now gone. 

Now, one of the things that really impressed me about ubuntu when I first installed it was that it found used my wireless card with no problems whatsoever, immediately after installing and adding the WEP key. So, how do I put the default wireless driver, as you find on a fresh install of 5.10, back in after a kernel recompile? Thanks guys.

---

### Post by az on 2006-03-05
[QUOTE=SirTode]Ok, as the header suggests, I just recompiled the kernel (was necessary in order to get my mouse driver installed, or so I was told), and everything seems to work fine, EXCEPT my wireless driver is now gone. 

Now, one of the things that really impressed me about ubuntu when I first installed it was that it found used my wireless card with no problems whatsoever, immediately after installing and adding the WEP key. So, how do I put the default wireless driver, as you find on a fresh install of 5.10, back in after a kernel recompile? Thanks guys.[/QUOTE]
Maybe when you recompiled your kernel, you omitted the driver, or did not install the linux-restricted-modules.

Did you recompile your kernel with kernel-package?  If so, you have an entry for your old kernel in grub.  Boot that and remove the self-compiled kernel package.  If you did it by hand, just reinstall the linux-image you have.  Use synaptic to pick the most recent linux-image package and mark it for reinstallation.  It should give you your proper kernel entry back.

To compile a module for the stock kernel, install the linux-headers package and use that instead of a self-compiled linus source.

You do not need to recompile the kernel just to make an additional driver that was not included.

---

### Post by SirTode on 2006-03-05
[QUOTE=azz]Maybe when you recompiled your kernel, you omitted the driver, or did not install the linux-restricted-modules.
[/QUOTE]

I followed the directions at 

[http://www.ubuntuforums.org/showthread.php?t=85064&highlight=compile+kernel](http://www.ubuntuforums.org/showthread.php?t=85064&highlight=compile+kernel)

I gather from what he wrote that there are instructions for undoing it. The thing is, I recompiled in order to this build thing working, so I could install a driver for my wireless mouse. Will that work if I revert? 

This problem is turning into a troll, I chop off one head, it spawns a whole new troll... argh.

---

### Post by hscottyh on 2006-03-05
Just for the record, with ubuntu I've never had the need to recompile the kernel. And I've gotten every piece of hardware (except for the 4-1 media reader on my laptop) working I've thrown at it. Now, I've had to compile some stuff; just not the kernel. Not saying that was your case, just saying it's a lot easier if you there is another way.

---

### Post by az on 2006-03-05
[QUOTE=SirTode]I I recompiled in order to this build thing working, so I could install a driver for my wireless mouse. Will that work if I revert? 
[/QUOTE]

You don't need to recompile in the first place.  Just use the linux-headers instead of the linux source tree.  That's what the linux-headers packages are for.

So, if you revert to the stock kernel, everyting should work.  Then install the corresponding linux-headers package and build your mouse driver for the stock kernel using that.

---

### Post by SirTode on 2006-03-05
sigh... It's not that I don't really appreciate the advice, but I'm getting mixed signals all over the place. I was told that recompiling the kernel would enable this "build" thing that I need to have working in order to compile the driver for my Logitech Mediaplay mouse. I downloaded that driver, ran make, and it basically got nowhere because the build isn't there. I have already installed build-essentials.

So, if anyone's got anymore ideas... I put the old kernel back and the wireless is working again, which puts me back at square one after working on this thing all day.

---

### Post by Monkeh on 2006-03-05
I get the feeling you need the sources for the kernel (you need them for most module compiles). You should be able to find them in synaptic.

---

### Post by az on 2006-03-06
[QUOTE=SirTode]I was told that recompiling the kernel would enable this "build" thing that I need to have working in order to compile the driver for my Logitech Mediaplay mouse. [/QUOTE]


What build thing?  The linux-headers provides the /lib/modules/`uname -r`/build symlink to your headers (which you use as the source).  Is that what you mean?


Some drivers require that you use the full linux source, but they are few and far between and improperly built.  Does your driver have a url?

---

### Post by SirTode on 2006-03-07
Well, I was trying to use this one:

[http://daemon.prozone.ws/~david/projects/lmpcm_usb/](http://daemon.prozone.ws/~david/projects/lmpcm_usb/)

But I did just find this, in searching for the above:

[http://linux.softpedia.com/get/System/Hardware/Logitech-MediaPlay-Cordless-Mouse-USB-Linux-driver-5962.shtml#](http://linux.softpedia.com/get/System/Hardware/Logitech-MediaPlay-Cordless-Mouse-USB-Linux-driver-5962.shtml#)

which appears to be different, so maybe I'll try that. At the point of my last post, I was on the very edge of putting windows back, but I decided to leave it for a couple days and try again later.

I'm not a complete and utter dfo (I know my way around DOS, for instance), but the three times I've tried getting into Linux it's been an exercise in frustration every time - I encounter one problem, and trying to fix that spawns another, and that one another, and so on. It's like digging into an onion, layer after layer, with a comparable amount of pain and crying. :>

---

