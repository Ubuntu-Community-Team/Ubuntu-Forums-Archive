---
title: "Aqua On Linux!"
date: 2006-12-14
forum: Mac OSX
---

### Post by jclmusic on 2006-12-14
i was reading about OSX86 (hacking OSX to work on PCs) the other day, and i wondered how hard it'd be to port the aqua GUI to Linux?

(and yes, this is just a for instance. i know it's illegal, and i'm not geeky enough to be able to do it myself anyway!)

---

### Post by happy-and-lost on 2006-12-14
Have a look on gnome-look.org as it's probably already been done!

EDIT: [http://www.gnome-look.org/content/show.php?content=13548](http://www.gnome-look.org/content/show.php?content=13548) ;)

---

### Post by jclmusic on 2006-12-14
no, u misunderstand me. i've seen all the themes, etc.

i meant if someone hacked osx like they have done with osx86 and put it on top the linux kernel.

---

### Post by Lord Illidan on 2006-12-14
I don't think it would be out and out impossible, as after all, BSD and Linux are not that far off. But, since Mac OSX is closed source, you'd have to reverse engineer things.

---

### Post by wgscott on 2006-12-14
It is possible.  I have a DVD on my desk.  I won't run it for legal reasons, but I had a look. Also it is fairly broken and not much runs on it.  But it is a marketing decision not a technological limitation.

---

### Post by 3rdalbum on 2006-12-14
This would be so difficult, without any reasonable gain. Aqua uses Display Postscript, and PDF is an internal file format of OS X for screenshots and text clippings and things. These PDFs are often incompatible with Acrobat Reader for Windows, and probably for Linux too.

If I wanted to run a mongrel operating system based on a low-performance version of FreeBSD, a 1990s m68k operating system, a 1980s m68k operating system, and some crippled open-source userspace programs, I'd buy a Mac thank you very much.

---

### Post by marlls1989 on 2007-10-09
:lolflag:
The Darwin, the system which Aqua runs on, is completely different from linux linux in many aspects:

First, binary format. Linux, almost *BSD use ELF. While Darwin uses mach-o.

Even if it was ported from darwin, the second problem is the sys-calls, which are based, but not compatible with FreeBSD, again a completely different approach from linux, you'd have to almost rewrite the whole kernel.

Even worse, the osx kernel uses Mach Ports to communicate with several parts of the system, an hybrid kernel with a micro kernel approach for device drivers.

The IOkit is responsible for managing the graphics adaptor, again different from linux, which is X11 (Users Space) managed

And the ObjC runtime, which cocoa is wrote, has a very tied relationship with the kernel and Mach ports. A huge different approach from GNUstep.

Long and Prosper Life!!!
cheers from the master, Spock

---

### Post by marlls1989 on 2007-10-09
And speaking of OSX86, All was done was modifying the HAL (Hardware abstraction Layer) from Darwin to fits the generic PC arch.

And of course the insertion of some dummy code into the kernel to bypass some hardware verification and provide an fake EFI environment for the system.

---

### Post by igknighted on 2007-10-09
I think you misunderstand OSX86.  It is NOT running OSX on windows, it is running it on x86 hardware (as opposed to apple's PPC hardware, or specific x86 hardware).  There is no real change to the kernel or anything like that.  It is not running on a windows kernel as opposed to the mach (*NOT* BSD... but probably about as close to BSD as linux is) kernel.  To change the kernel over would require a re-write of almost all the programs that interface it (most of them), and without the source code it would be impossible.

Besides, I am curious why linux would want a proprietary graphical interface when it already has incredibly competant free ones?  What could possibly be good about it?  Either it would make a small niche happy and not change the majority of users lives, or it would catch on and subvert the efforts of a lot of equally good (if not better) free software projects.

---

### Post by marlls1989 on 2007-10-10
> **igknighted said:**
> I think you misunderstand OSX86.  It is NOT running OSX on windows, it is running it on x86 hardware (as opposed to apple's PPC hardware, or specific x86 hardware).  There is no real change to the kernel or anything like that.  It is not running on a windows kernel as opposed to the mach (*NOT* BSD... but probably about as close to BSD as linux is) kernel.  To change the kernel over would require a re-write of almost all the programs that interface it (most of them), and without the source code it would be impossible.

Besides, I am curious why linux would want a proprietary graphical interface when it already has incredibly competant free ones?  What could possibly be good about it?  Either it would make a small niche happy and not change the majority of users lives, or it would catch on and subvert the efforts of a lot of equally good (if not better) free software projects.

Pardon me, but I never said to run OSX on the NT kernel, I said PC arch in the meaning of generic x86, not apple specific hardware.

And yes there is kernel modification on the darwin core, there is some hacks to get informations from ACPI, vbe, and other bios specific firmware interfaces.  SSE3 ISA interpreter for non-intel cpus (thus newly AMD don't need it) as I said before, the proprietary part intentionally depends upon EFI. So dummies EFI interfaces are generated for hardware check.

And what I said before, was creating an darwin ABI on linux would be very hard, and still might be unsuccessful, but if some one start the porting of darwin ABI now, it might be ready and stable in 2015 (Just take a look at the wine which started in 96).

Since the complexity from mach kernel, it would be easier to get the darwin and put linux as a modules.

Darwin is ***NOT*** *BSD but contains a BSD layer for networking, filesystem and POSIX compatibility.

It might be a good idea to create a linux layer for darwin...

---

### Post by ashvala on 2007-10-14
probably quite hard. But the entire aqua interface would take around 3 days to write which requires you to do every thing pixel perfect. & the toolbar, Dock would also take some time. But some people have done it using freeBSD & Darwin linux which is a simpler method of doing the aqua interface. Afterall MAC OSX is closed source linux

---

### Post by Alfa989 on 2007-10-14
> **ashvala said:**
> Afterall MAC OSX is closed source linux
Mmm... Not really the case...

---

### Post by 3rdalbum on 2007-10-16
> **ashvala said:**
> Afterall MAC OSX is closed source linux

If there's ever such a thing as "closed source Linux", then there would be many lawsuits launched.

---

### Post by Demio on 2007-10-16
Mac OS X is not even close to a closed source Linux. ;)

---

### Post by Lmnlme on 2008-06-23
Everyone I know thinks that anything that runs on a UNIX core must be linux.  (They also think that all linux'es are free...)

---

### Post by Fzang on 2008-06-24
Anything is possible with linux!

....except making it run on my computer, but I'm behind you guys :)

---

### Post by Le-Froid on 2008-06-25
> Afterall MAC OSX is closed source linux

linux =/= BSD. People already described what Mac OS X is, but it is not closed source either. It is actually "Closed source with **open source components**"..

---

### Post by ian_hawdon on 2009-02-03
> **ashvala said:**
> Afterall MAC OSX is closed source linux

As far as I know, as far as Kernels go, Darwin is just another Unix-Like system, possibly forked from FreeBSD, if not, it's definitely based on BSD! It's just as open source as FreeBSD and Linux. Afaik, it's only the front end and the programs on OS X that are closed.

As for running Aqua on Linux, it would have its benefits, it would make switching from OS X to GNU/Linux a lot more simple! The down side is, at the moment, Apple are the only folks that can update it, and I doubt they'd release the code any time soon!

Although, I think KDE 4.2 is probably a much nicer interface, though I am yet to try it! (I am waiting for the release of Jaunty to make the leap from regular Ubuntu, to Kubuntu :-))

---

### Post by alex.rayu on 2009-02-15
Mac OS X is not just closed-source Linux. It has had so many significant changes to the initial BSD kernel, that they are very different now.

---

