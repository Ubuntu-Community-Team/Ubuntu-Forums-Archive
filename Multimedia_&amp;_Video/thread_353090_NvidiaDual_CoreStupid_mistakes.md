---
title: "Nvidia/Dual Core/Stupid mistakes"
date: 2007-02-04
forum: Multimedia &amp; Video
---

### Post by lukeo on 2007-02-04
Seriously lame, follow all the guides to get Nvidia working. I've spent hours getting Twinview, Direct Rendering, Beryl etc all working on my Dual Core 4800+. 

Only to find out that the "blahblah-386" kernel that has been installed doesnt support SMP, thats right it's single core only. What a fking joke. How stupid is that?

I can load up the "generic" kernel via grub... IF I MANUALLY EDIT xorg.conf and specify driver "nv" instead of "nvidia"...my second TFT doesnt work, no beryl, no direct rendering... nothing. BUT I get two cpu's in system manager.

I mean how fking stupid is this, it's this kind of crap that makes people tear thier hair out and go back to windows.

---

### Post by lukeo on 2007-02-04
My point stands even though uninstalling and reinstalling the nvidia drivers and reconfiguring everything the second time around wasn't quite as time consuming.

1. Both Ubuntu and Windows come with out of the box support for DUAL CORE (SMP). Installing a VIDEO CARD driver in Windows does not remove the OS's ability to support dual core...

2. Installing a video card in Windows is as easy as running the driver installation program, not following cut/paste 70 terminal commands from obscure repositories and manually editing configuration files.

If you want to capture those millions of mums and dad's around the world you have to improve this part of linux (it's been the same for years every time I've installed it)... it absolutely has to get better than this.

---

### Post by Mike'sHardLinux on 2007-02-04
Lukeo, I am truely sorry you are having such problems. I hate to see that. It definitely doesn't help with trying to get people to switch. And, really it's just a bummer that anyone has to suffer in such a way. :( 

1. Windows home does NOT support SMP. I am pretty sure of this. And that is what your average home user has. Ubuntu Edgy supported SMP out of the box for me. (Pentium D 820)

2. Generally, true. I have to say, though, when I upgraded from a 6600 to this 7600GT, I didn't have to do anything at all. The new card works as it should,
But remember, many manufacturers work with MS. They are like buddies. The hardware manufacturers either don't care about Linux users, or some seem to have some kind of deal with MS not to support it. So, much of the blame is on them.

> If you want to capture those millions of mums and dad's around the world you have to improve this part of linux (it's been the same for years every time I've installed it)... it absolutely has to get better than this.

No argument there. This brings up a good point, though. **Linux is not for everyone.** Many Linux users either don't realize this, or forget it at times. I know some distros (like Ubuntu) are trying to change this, but as of right now, it is still true.

Anyway, on to your problems. Are you following a how-to to get your video card working? If so, which one? I am not sure how I got my stuff going, as I had to go through a few steps, and it seems like I didn't follow the how-to exactly. (I know I should have documented, but, well, I didn't.)

You make it sound like the video driver issue and the SMP kernel issue are somehow related, but that doesn't seem right to me. Maybe it's just  coincidence that things happened that way? What all kernels do you have installed, and listed in grub? I know for a fact the generic kernel supports SMP. Did the i386 (non-generic) kernel get installed by default or did you install it?

---

### Post by lukeo on 2007-02-04
I think my annoyance may have been mis-directed 

[http://ubuntuforums.org/showthread.php?t=281823](http://ubuntuforums.org/showthread.php?t=281823)

That guide from the sticky is what I initially tried to follow, using method 1 after I did all of the steps (there are a few) I rebooted and got the error message (blue screen) X could not start blah blah. I had backed up my xorg.conf so I restored it by logging in as root and doing cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf ... which worked thankfully. Why isn't their a built in option to return to the last working version of that file? Just dumping the user back to a terminal isn't very nice in this day and age.

Yeh I understand Linux isn't for everyone, YET. But it should be I'd like to think.

As I said Method 1 failed me so I tried "envy" which is what installed the new kernel (yes it appears in grub). My bad? Maybe. Still not nice to happen in the official stickies of Ubuntu. It took me a few hours to realise that this new kernel wasn't SMP, and all my customisations had been in vain.

I removed everything Nvidia related, and re-ran the sticky as Method 2. Worked fine... still had to manually edit the xorg.conf to specify Twinview etc.

Windows home does NOT support SMP. True. However I don't remember the last PC I've seen go out the door with Home on it, Pro is comparably priced (for the OEM version). I don't remember the last PC I've fixed that's had home on it either. PC vendor's have been flogging Dual core X2's and Core2Duo's for along time now, and they can't ship them with home they have to have Pro for the SMP support. Your point makes no sense. My point is installing video card drivers should not disable SMP on your nice dual core computer... no matter what.

---

### Post by lukeo on 2007-02-07
You guys just going to let this one slide away? I have installed in a vmware virtual machine the latest ubuntu feisty alpha 3 7.04 and it's got exactly the same configuration steps for getting nvidia drivers to work. No change in about the last 3 versions of Ubuntu, about time for some innovation right? Make it easier, make it better! Don't just say it's good enough, lets just continue rolling it out as is.

---

### Post by lukeo on 2007-02-12
Upto the top with you! Still having issues in this thread:

[http://www.ubuntuforums.org/showthread.php?t=357046](http://www.ubuntuforums.org/showthread.php?t=357046)

---

### Post by funnyperson1 on 2007-03-11
I agree setting up dual monitors in xorg with any video card even for 2D mode is much harder than it should be.  Add in 3D rendering and Beryl and its a nightmare.  So much so that I'm not even going to try this time.  It is a shame that I essentially have to choose between a fully functioning dual monitor setup, and having all the cool features of Beryl.

Also Windows XP Home does not support SMP systems with two discrete processors, but it DOES support dual-cores and quad-cores with full SMP as long as they are on the same processor.

---

### Post by larini on 2007-03-12
I just change my amd 64 single core to a dual core, and how to know if my system is using dual core or not?
Thanks.

---

