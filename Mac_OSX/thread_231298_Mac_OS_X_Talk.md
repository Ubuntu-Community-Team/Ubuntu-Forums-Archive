---
title: "Mac OS X Talk"
date: 2006-07-28
forum: Mac OSX
---

### Post by &amp;)ky#)^ on 2006-07-28
Nobody can give me a straight answer to this question I have.  Since the new Apple computer use the standard Intel x86 processor architecture, the MacOS X has to have been recompiled for the architecture.  It used to be that if you wanted to use an Apple OS on your PC, all you could do was give Darwin and Open Darwin a shot.  But, in theory, could someone take the MacOS X for Intel Macs and run it on a standard PC?

EDIT:  It's been done.  I found this article about it.

[http://reviews.zdnet.co.uk/software/os/0,39024180,39235916,00.htm]("http://reviews.zdnet.co.uk/software/os/0,39024180,39235916,00.htm")

However, I'd love to hear from anyone who's actually tried this before and what their experience was like.

---

### Post by Dodzey on 2006-07-28
Although i haven't triedto run Mac OS X natively (I used to run it under PearPC emulation on my winbox), I have heard lots of succes stories on the internet.

The issue you will have will be the fact that Mac OS X is only designed for intel mac hardware...in other words, it is very fussy about which main boards, graphics and sound etc, that it will run on. I remember reading an article which went into quite a bit of detail about exactly which chipset to go for and which graphics etc...his choices were based on the testing and development hardware that apple released to developers long before the IntelMacs came out.

The OS also searches for a chip on the mainboard which is kind of like a registration dongle in a way...you would have to patch the operating system to stop it searching for this chip (this has already been done)

And lastly, I'm sure it would break just about every term in Apples licensing agreement, but what the hell! :D 

If i find the article that i am talking about i will edit my post on here.

---

### Post by gruvsyco on 2006-07-28
About a year ago, I had it running natively on my system.  It crashed alot (it was an early hack) and didn't support my video card above 1024x768.  I eventually replaced the install with Ubuntu then just used it as spare space for XP.  There's some guy that keeps cracking Apples DRM within days of release updates, they kept getting his site taken down... not to sure whatever became of all that.

---

### Post by rekahsoft on 2006-07-28
A freind of mine has successfully got Mac OS X working on an Toshiba laptop with an AMD Athlon processor...it took some work...we had to patch the kernel first for the AMD and then patch the kernel for SSE3 (because mac requires it). Then we just had to find the apropriate drivers for the sound card and everything was good :) It runs decently fast (but not as fast as it would on a intel machine because the AMD has to emulate SSE3.

---

### Post by &amp;)ky#)^ on 2006-07-28
Of all the specs I saw regarding the MacOS, only one really shocked me.  It's the only OS I've ever run into that actually *needs* over 5 GBs of hard drive space.  How ridiculous!  Why's it so chunky?

---

### Post by Dodzey on 2006-07-29
It depends what you consider chunky, as far as I am aware Windows Vista will  (and does) require around 11gb of free disk space...that 5gb doesn't seem so chunky now does it!? :rolleyes: 

Microsft should scrap all their editions such as Ultimate etc and have one version

Microsoft Windows Vista Bloatware Edition

:D

---

### Post by &amp;)ky#)^ on 2006-07-29
Holy crap!  I hadn't heard that.  11GB is total crap!  I'm so glad I achieved my goal of switching to Linux before Vista was released.  My god!  I just can't believe that.  That's crazy.  I use seperate partitions for my /home folder and everything else in the filesystem.  Not counting my /home folder, my system is using a little less than 2GB.  Vista is Microsoft's crowning achievement of horror.

---

### Post by Camellia on 2006-07-30
Hi everyone I just came up this idea: Is OSX just another distribution of Linux? Simply because it's based UNIX.

---

### Post by 23meg on 2006-07-30
No. It has nothing to do with the Linux kernel, and doesn't put together the rest of its components from other open source projects but develops them in-house and they're proprietary.

---

### Post by Kernel Sanders on 2006-07-30
OSX is weird, I cant get my head around it. No right click, drag your CD to the trash...... arrrggghhh *head implodes* :(

---

### Post by dio525i on 2006-07-30
> ***John* said:**
> OSX is weird, I cant get my head around it. No right click, drag your CD to the trash...... arrrggghhh *head implodes* :(

hahaha.... seriously

---

### Post by TravisNewman on 2006-07-30
people seem to forget that if you have a mouse with two buttons, you have a right click menu. It sucks that you don't get a two button mouse when you buy the thing, but I've never bought a PC where I kept the default mouse for long. They almost always suck. :)

But no, just because it's unix based doesn't make it a linux distro. FreeBSD is by no means a Linux distro. Darwin is BASED on BSD, but there's a LOT of difference there, and everything built on top of Darwin is totally proprietary. Unfortunately.

---

### Post by IYY on 2006-07-30
OS X is based on FreeBSD, not Linux.

---

### Post by RAV TUX on 2006-07-30
> **IYY said:**
> OS X is based on FreeBSD, not Linux.

actually Mac OS X history is:
> 
Despite its branding as simply "version 10" of the [Mac OS]("http://en.wikipedia.org/wiki/Mac_OS"), Mac OS X has a history that is almost completely independent of the earlier Mac OS releases.
 Mac OS X is based on the [Mach kernel]("http://en.wikipedia.org/wiki/Mach_kernel") and the [BSD]("http://en.wikipedia.org/wiki/Berkeley_Software_Distribution") implementation of [Unix]("http://en.wikipedia.org/wiki/Unix"), which were incorporated into [NEXTSTEP]("http://en.wikipedia.org/wiki/NEXTSTEP"), the [object-oriented operating system]("http://en.wikipedia.org/wiki/Object-oriented_operating_system") developed by [Steve Jobs]("http://en.wikipedia.org/wiki/Steve_Jobs")'s [NeXT]("http://en.wikipedia.org/wiki/NeXT") company after he left Apple in [1985]("http://en.wikipedia.org/wiki/1985").[[1]]("http://en.wikipedia.org/wiki/Mac_os_x#_note-0") Meanwhile, during the years without Jobs at the helm, Apple attempted to create a "next-generation" operating system of its own (see [Taligent]("http://en.wikipedia.org/wiki/Taligent") and [Copland]("http://en.wikipedia.org/wiki/Copland")) with little success.
 Eventually, NeXT's OS—called [OPENSTEP]("http://en.wikipedia.org/wiki/OpenStep") at the time—was selected to form the basis for Apple's next OS, and Apple purchased NeXT outright[[2]]("http://en.wikipedia.org/wiki/Mac_os_x#_note-1"). Jobs was re-hired, and later returned to the leadership of the company, shepherding the transformation of the programmer-friendly OPENSTEP into a system that would be welcomed by Apple's primary market of home users and creative professionals, as a project known as [Rhapsody]("http://en.wikipedia.org/wiki/Rhapsody_%28OS%29"). After some missteps which threatened the loyalty of independent developers to Mac OS, and changes of strategy to ease the transition from Mac OS 9 to the new system, Rhapsody evolved into Mac OS X.
 Mac OS X has evolved through its successive versions, away from a focus on [backward compatibility]("http://en.wikipedia.org/wiki/Backward_compatibility") and toward "digital lifestyle" applications such as the [iLife]("http://en.wikipedia.org/wiki/ILife") suite, enhanced business applications ([iWork]("http://en.wikipedia.org/wiki/IWork")), and integrated home entertainment (the [Front Row]("http://en.wikipedia.org/wiki/Front_Row") media center).

[http://en.wikipedia.org/wiki/Mac_os_x](http://en.wikipedia.org/wiki/Mac_os_x)


And since it is some what similar to "other" OS's which include BSD, BeOS etc. I will move this thread to the "Other" OS thread.

> **ubuntu-geek said:**
> Welcome to the new Other Linux Talk forum. This is the perfect place to discuss other linux distro's and related OS's.

---

### Post by hajk on 2006-07-30
Well, OSX/Darwin-i386 behaves like another *nix distribution for sure -- all the regular Unix commands work in a Terminal window: vi (Vim), ssh/scp, the familiar directory tree. 

I've been playing with my new MacBook for a week now, and I am very impressed with OSX.... if you wonder about the future of Ubuntu, wonder no more! Apple are doing a lot of things right, even the printer installation (with CUPS) that proves so difficult to do in Ubuntu.

Having said all that, my main desktop will continue to run Ubuntu (amd64), just because a lot of numerical software has not yet been ported to Darwin-i386.

---

### Post by dabear on 2006-07-30
Hi, I've had OS X86 installed on my computer for some time now. I works perfectly, except for three issues; 
-wireless Internet doesn't work (although I have an rt2500 based card with opensource drivers)
- No sound
- CD/DVD burner not supported.

---

### Post by Camellia on 2006-07-30
Wow it seems that I got lots of things wrong here.
Thank you all for the inputing, which really helps:)

---

### Post by tseliot on 2006-07-31
It won't install on my systems.

---

### Post by RAV TUX on 2006-08-07
I have decided to start a series of threads specifically for technical help for other Distros...the Distro is listed in the thread title. This is primarily for Ubuntu users who test or use other distros and feel most comfortable seeking help in our own community. In no way does this superceed the help you should also be getting from the perspective Distro., in fact I encourage you to be as active in their forums as you are here and post ideas, knowledge and solutions here to provide a reference point to share, reference links are encouraged.

***Mac OS X Tech Talk***

Threads merged:

[http://www.ubuntuforums.org/showthread.php?t=224508](http://www.ubuntuforums.org/showthread.php?t=224508)
[http://www.ubuntuforums.org/showthread.php?t=231298](http://www.ubuntuforums.org/showthread.php?t=231298)
[http://www.ubuntuforums.org/showthread.php?t=225910](http://www.ubuntuforums.org/showthread.php?t=225910)

---

### Post by &amp;)ky#)^ on 2006-08-09
Can anyone who is using Front Row please take a video capture of it and do a short feature walkthrough for me?

---

### Post by frenkel on 2006-08-10
> **panickedthumb said:**
> people seem to forget that if you have a mouse with two buttons, you have a right click menu. It sucks that you don't get a two button mouse when you buy the thing, but I've never bought a PC where I kept the default mouse for long. They almost always suck. :)


What are you talking about? The Mighty Mouse has 2 buttons on top, and you get it when you buy a PowerMac, iMac or Mac Pro.

---

### Post by jetblack on 2006-08-10
> **frenkel said:**
> What are you talking about? The Mighty Mouse has 2 buttons on top, and you get it when you buy a PowerMac, iMac or Mac Pro.

Oh? How long has that been the case? That's a nice development.

---

### Post by frenkel on 2006-08-11
> **jetblack said:**
> Oh? How long has that been the case? That's a nice development.

I think for 2 years now.
Although most people still think it has one button, because you can't see it has 2 buttons. It's based on touch technology.
Since a few weeks it's also available wireless.

[http://www.apple.com/mightymouse/](http://www.apple.com/mightymouse/)

---

### Post by PenguinMan on 2006-08-16
> ***John* said:**
> OSX is weird, I cant get my head around it. No right click, drag your CD to the trash...... arrrggghhh *head implodes* :(
[COLOR=Purple]Get a two-button mouse and you can right-click, send to trash, etc. with the right mouse button. :)[/COLOR]

---

### Post by 23meg on 2006-08-16
Caveat with the mighty mouse: you can't hit the right button without lifting your finger from the left button position and vica versa. Its sensors will only register one finger action at a time and if they get two, no go. This in my experience makes it totally unusable, sadly, because it's otherwise a very good mouse.

---

### Post by dabear on 2006-08-16
Does anybody know if it is possible to change the look of the mouse cursor?

---

### Post by mike3k on 2006-09-12
> **jetblack said:**
> Oh? How long has that been the case? That's a nice development.

You've always been able to use any USB multi-button mouse with a Mac. I never use Apple's mouse (except the Mighty Mouse which came with my iMac Core Duo). I've always used kensington, logitech, or even cheapie no-name scroll mice. With my MacBook Pro I use a Belkin Bluetooth mouse.

---

### Post by Skia_42 on 2006-09-14
It is a good idea to do a search for similar threads before starting your own. I started a thread [here]("http://ubuntuforums.org/showthread.php?t=237189") that addresses the same idea. Just a suggestion for next time...

---

### Post by frenkel on 2006-09-14
> **Skia_42 said:**
> It is a good idea to do a search for similar threads before starting your own. I started a thread [here]("http://ubuntuforums.org/showthread.php?t=237189") that addresses the same idea. Just a suggestion for next time...
Good suggestion for you, because this thread was started on 28 july, weeks before you started yours.

---

### Post by Skia_42 on 2006-09-14
> **frenkel said:**
> Good suggestion for you, because this thread was started on 28 july, weeks before you started yours.

:confused:
HOW DID I MISS THAT!?! I feel both embarassed and ashamed. A thousand pardons for my ridiculous criticism.
#-o

---

### Post by Donnut on 2006-10-05
I've actually done this, then I bought a mac, now I tripple boot mac, linux, and windows.  It's so beautifull!  Sure, the macs are kinda expensive, and PCs are definately worth the work!  Just find out how mac builds their PCs, and with what componants, and you'll be up and running a huge tripleboot system in no time flat!

---

### Post by Ptero-4 on 2006-10-28
[QUOTE=Dodzey]The issue you will have will be the fact that Mac OS X is only designed for intel mac hardware...in other words, it is very fussy about which main boards, graphics and sound etc, that it will run on. I remember reading an article which went into quite a bit of detail about exactly which chipset to go for and which graphics etc...his choices were based on the testing and development hardware that apple released to developers long before the IntelMacs came out.[/QUOTE]
System76 PC's are based on the same brand Apple uses to build their Mac's, hence you should be able to run OSX in a System76 PC.

[QUOTE=Dodzey]The OS also searches for a chip on the mainboard which is kind of like a registration dongle in a way...you would have to patch the operating system to stop it searching for this chip (this has already been done)[/QUOTE]
The chip OSX looks for is called "TPM" chip and System76 PC's includes one which is again identical to the one used in IntelMacs, so you won't need to patch the OSX kernel, since you get SSE3 support and TPM chip OOTB.

[QUOTE=Dodzey]It depends what you consider chunky, as far as I am aware Windows Vista will (and does) require around 11gb of free disk space...that 5gb doesn't seem so chunky now does it!? [/QUOTE]
Actually Windoze Waste needs 15GB just to be installed.

---

