---
title: "How similar are Mac OS X and Linux"
date: 2006-12-27
forum: Mac OSX
---

### Post by gh0st on 2006-12-27
I don't know if anyone has brought this up before but I was wondering how similar Mac OS X is to Linux? I know they are both derived from UNIX but I don't have a lot of knowledge of OS X. I've only ever used a Mac once or twice at a friends house so you'll have to excuse my ignorance here.

I found out a while ago that OS X was UNIX based and then when I saw some software on Source Forge recently with one TAR archive for installation on OS X and Linux it got me thinking, how similar are they? If you can just get the same source and build it on either OS X or Linux would Mac software run on Linux with only minimal alteration or am I just being stupid?

Hopefully someone with more knowledge of OS X (wouldn't be hard :)) can shed some light on this for me.

Thanks in advance.

---

### Post by fuscia on 2006-12-27
all i know is that linux is a monolithic kernel and osx is a micro-kernel. and in the words of the immortal jackie gleason "goodnight, everybody!"

---

### Post by RAV TUX on 2006-12-27
moving to the Mac OS X forum.

---

### Post by neowolf on 2006-12-28
Take a look at the [UNIX History Tree](http://www.levenez.com/unix/history.html), very complicated :p

> 
Mac OS X is based on the Mach kernel and is derived from the BSD implementation of Unix in NEXTSTEP. NEXTSTEP was the object-oriented operating system developed by Steve Jobs's NeXT company after he left Apple in 1985.


AFAIK, both Linux and Mac OS X are POSIX compliant UNIXes so should share some basic similarity.

---

### Post by gh0st on 2006-12-28
Thanks for the Unix History Tree link I'll have a read through this. It may take a while :) 

I read a while ago that Steve Jobs' company developed the OS while he was exiled from Apple and when they brought him back in he brought the OS with him and called it OS X. Thats where I read about it's UNIX base, I didn't realise it was based on BSD though thats useful for know.

I have heard that a lot of the command line stuff is the same in OS X and Linux which would make sense I suppose. Does anyone know if you can use mostly the same commands? I used some really old UNIX legacy systems when I worked at a hospital and I found most of the commands I knew from Linux worked the same.

Thanks for the info

---

### Post by 3rdalbum on 2006-12-28
Not sure if OS X is really POSIX compliant - I for one can't believe that Mac OS's resource forks (which cannot be dealt with on Unix or Linux) really fit in with POSIX specifications. OS X also treats applications differently, in where they are actually placed, and hides certain directories that programs would access on Linux or Unix.

Mac OS X is really derived from Unix in the same way that I'm derived from H.G. Wells - there's undoubtedly some of the original in there, but there are so many differences you might as well treat them as seperate things. Hence the reason why I don't write science-fiction.

EDIT: In reply to gh0st, yes the basic terminal commands are the same, but the GNU userspace utilities from Linux do have some different options to the Unix, Mac OS X and Syllable ones. If a familiar command doesn't work properly, best to check the man page.

---

### Post by Alfa989 on 2006-12-28
> **3rdalbum said:**
> Not sure if OS X is really POSIX compliant - I for one can't believe that Mac OS's resource forks (which cannot be dealt with on Unix or Linux) really fit in with POSIX specifications. OS X also treats applications differently, in where they are actually placed, and hides certain directories that programs would access on Linux or Unix.

Mac OS X is really derived from Unix in the same way that I'm derived from H.G. Wells - there's undoubtedly some of the original in there, but there are so many differences you might as well treat them as seperate things. Hence the reason why I don't write science-fiction.

EDIT: In reply to gh0st, yes the basic terminal commands are the same, but the GNU userspace utilities from Linux do have some different options to the Unix, Mac OS X and Syllable ones. If a familiar command doesn't work properly, best to check the man page.

According to Wikipedia, Mac OS X is fully POSIX-compliant...;) 

[http://en.wikipedia.org/wiki/POSIX#Fully_POSIX-compliant]("http://en.wikipedia.org/wiki/POSIX#Fully_POSIX-compliant")

---

### Post by 3rdalbum on 2006-12-28
> **Alfa989 said:**
> According to Wikipedia, Mac OS X is fully POSIX-compliant...;) 

[http://en.wikipedia.org/wiki/POSIX#Fully_POSIX-compliant]("http://en.wikipedia.org/wiki/POSIX#Fully_POSIX-compliant")

I wouldn't place too much store in that article - it claims that Windows is fully POSIX-compliant. I've been trying to find the /bin directory on my NTFS partition without success :-)

---

### Post by neowolf on 2006-12-30
XNU Kernel + FreeBSD parts + NeXTSTEP = Mac OS X

AFAIK...
I think Apple compile Mac OS X with GCC, I think I saw somewhere, I know GCC is used on Mac OS X for definate though.

---

### Post by 3rdalbum on 2006-12-30
I know that GCC is available for OS X, but the operating system and programs are not compiled with it. Maybe they were in the past, but definately not now.

---

### Post by rccharles on 2007-01-22
> **gh0st said:**
> I don't know if anyone has brought this up before but I was wondering how similar Mac OS X is to Linux? I know they are both derived from UNIX but I don't have a lot of knowledge of OS X. I've only ever used a Mac once or twice at a friends house so you'll have to excuse my ignorance here.


Mac OS X is a layered Operating System. How you view Mac OS X depends on what layer you are using.

The normal user sees a GUI that is Apple specific.  The user will hardly realize that they are using Unix.  About the only GUI reference to unix is when you format a disk. For instance, Mac OS X include the term "mount point".

Mac OS X includes an optional install of X11.  X11 and the a terminal application lets you reference the Unix layer.  I have heard of people running KDE on the Mac.

> 
I found out a while ago that OS X was UNIX based and then when I saw some software on Source Forge recently with one TAR archive for installation on OS X and Linux it got me thinking, how similar are they? If you can just get the same source and build it on either OS X or Linux would Mac software run on Linux with only minimal alteration or am I just being stupid?

Depends on what interface the application was written for.  Application written for the Mac OS X GUI will be more difficult to port.  X11 applications will port with no problem.  

Some folks have ported apt-get to access Open Source projects.  This is the fink project. "The database was last updated at 00:09 GMT on Tuesday, January 23 and currently lists 7575 packages in 24 sections. See:
[http://fink.sourceforge.net/](http://fink.sourceforge.net/)
[http://pdb.finkproject.org/pdb/index.php?phpLang=en](http://pdb.finkproject.org/pdb/index.php?phpLang=en)


> 

Hopefully someone with more knowledge of OS X (wouldn't be hard :)) can shed some light on this for me.

Thanks in advance.

Robert

---

### Post by Auria on 2007-01-27
> **3rdalbum said:**
> I know that GCC is available for OS X, but the operating system and programs are not compiled with it. Maybe they were in the past, but definately not now.

GCC is THE mac OS X compiler. Provided by Apple with all Mac OS X, and defintely very widely used. I think the only other compiler on mac is the Intel one. (Though not widely used i would assume.)

> I for one can't believe that Mac OS's resource forks (which cannot be dealt with on Unix or Linux) really fit in with POSIX specifications.

Resource forks are not used anymore on OS X, just for legacy app support. New apps use data files.


Also you can use a lot of the same terminal commands.

The biggest difference i have seen from a programmatical point of view in the Unix part, is that it doesn't use an X server.

---

### Post by rccharles on 2007-01-27
> **gh0st said:**
> I don't know if anyone has brought this up before but I was wondering how similar Mac OS X is to Linux? I know they are both derived from UNIX but I don't have a lot of knowledge of OS X. I've only ever used a Mac once or twice at a friends house so you'll have to excuse my ignorance here.

Here is an informative write up:

What is Mac OS X?
© Amit Singh. All Rights Reserved.

Here is the link:

[http://www.kernelthread.com/mac/osx/](http://www.kernelthread.com/mac/osx/)

Robert

---

### Post by SunnyRabbiera on 2007-01-27
The only real commality I see is that they are both UNIX based, a few directories and commands are simular but they are on opposite poles of the same tree (Unix)

---

### Post by MaXqUE on 2007-02-07
> **gh0st said:**
> I don't know if anyone has brought this up before but I was wondering how similar Mac OS X is to Linux? I know they are both derived from UNIX but I don't have a lot of knowledge of OS X. I've only ever used a Mac once or twice at a friends house so you'll have to excuse my ignorance here.

Liniux was developed by Linux Torvolds to be a free (as in open code) Unix-type operating system. But there is NO UNIX code in Linux. It was written from the ground up to be free of any proprietary code. So you have GNU Linux ... GUN = GUN is NOT UNIX.

The quest when LInus began writing the Linux kernel was for a UNIX-type operating system that was free from copyright and proprietary ownership. AT&T vs. Berkeley was not decided yet soi there was no FreeBSD,  OpenBSD, or NetBSD yet.

LInux is written to the POSIX standard just like UNIX so in that sense they are alike. 

> **gh0st said:**
> I found out a while ago that OS X was UNIX based and then when I saw some software on Source Forge recently with one TAR archive for installation on OS X and Linux it got me thinking, how similar are they? If you can just get the same source and build it on either OS X or Linux would Mac software run on Linux with only minimal alteration or am I just being stupid?

This is **MUST** know for Mac OS X users and Linux. Its history and part of how both OS's came into existance:

When UNIX was young, just a new operating system created at Bell Labs and owned by AT&T, Bell Labs and AT&T decided that they wanted to make UNIX a standard operating system. To do this, they made sure the people had access to the code. Most certainly Universities had UNIX. USC Berkley was one of them and a major contributor to UNIX.

University policy was to publish research and so they went about to publish what their students had done with UNIX. AT&T objected and this was the resulting court case. All we knew until recently was that UNIX/ BSD 4.3 was, by agreement, free of all proprietary obligation to AT&T. The Agreement was secret and sealed until an enterprising [Groklaw]("http://www.groklaw.net") reader asked the California courts to unseal it. Yoiu can read about it [here]("http://www.groklaw.net/article.php?story=20031124074251389&query=American+Telegraph+Berkeley").

Leaping forward in time, when Apple was writing their new operating system.. soon to be Mac OS X they decided to base if on an existing system. One called BeOS was considered as well as NeXTStep which they already owned. Linux was also considered as a base for OS X. The decision was made to base Mac OS X on FreeBSD 4.3, the same system which AT&T and Berkeley had agreed was free and clear of any proprietary obligation. That is ground zero for Mac OS X.

> **gh0st said:**
> Hopefully someone with more knowledge of OS X (wouldn't be hard :)) can shed some light on this for me. 

So Mac OS X has UNIX code in it, lots of it. It uses UNIX and FreeBSD commands. Liinux does to,  with some slight differences. But there is no UNIX code at all in Linux. It was written to act and run like UNIX but be free of the code and its copyright. LInux has its own copyright and it is licensed under the GPL

If you look in you Terminal application you will find a directory called libexec. You will not find that directory in Linux. There are other differenecs  as well, but you will find those as you go along. Basiscally the usual commands are the same. ls, pwd,  mkdir all do approxamately the same things, they were just written to do those things using different code. You are absolutely right to think they are related.  Do some reading at [Groklaw]("http://www.groklaw.net"), you will find answers for questions you haven't asked yet!

Cheers,
MaXqUE

---

### Post by 3rdalbum on 2007-02-09
> **MaXqUE said:**
> 
Leaping forward in time, when Apple was writing their new operating system.. soon to be Mac OS X they decided to base if on an existing system. One called BeOS was considered as well as NeXTStep which they already owned. Linux was also considered as a base for OS X. The decision was made to base Mac OS X on FreeBSD 4.3, the same system which AT&T and Berkeley had agreed was free and clear of any proprietary obligation. That is ground zero for Mac OS X.

Close, but you don't win the prize sorry :-)

Mac OS X is not directly based on FreeBSD. It is based directly on NeXTStep. NeXTStep is based on kFreeBSD and its basic userspace as it was in the early 90s when NeXTStep was developed.

For instance, a large number of OS X's libraries are direct ports of NeXTStep libraries. If you look through the API documentation, you'll find lots of function calls prefixed with the letters NS.

In reality, Mac OS X is based on FreeBSD as much as SLED is based on Slackware. I'm sure there's bits left in there, but how much?

---

### Post by MaXqUE on 2007-02-10
> **3rdalbum said:**
> Close, but you don't win the prize sorry :-)

Mac OS X is not directly based on FreeBSD. It is based directly on NeXTStep. NeXTStep is based on kFreeBSD and its basic userspace as it was in the early 90s when NeXTStep was developed.

You are only close to being right. Yes, Apple purchased NeXT. Avi Tevenian became Vice-Preseident of Software Engineering. He came from NeXT. But where did NeXT come from? If you want to see a [UNIX time line]("http://www.levenez.com/unix/history.html"), check the link. Its there, you may have to squint a bit unless you have one humoungous monitor.


I was wrong about one thing, Its not BSD 4.3, its BSD 4.4 - lite on which Mach 3 was based. Mach is a micro-kernel, unlike Linux which is a monolithic kernel.


Avi Tevenian was a young grad student at Carnegie-Melon University where as part of his masters thesis he was co-writing the Mach  Kernel. Apple also used Mach3's agility as a hardware interface to make the MKLinux port, which supported Macs with Motorola 668000 chips and PPC Macs iwth NuBus cards which Apple dropped just after the release of the PowerMac which used the PPC 601 chip.

MKLiinux was the first Linux Distro I ran, installed off a MacAddict CD using an installer written in AppleScript!

Mac was intended as a replacement for the BSD kernel which is  why it was based on a BSD variant. The Wikipedia has a fairly good artlcle on the [Mach Kernel]("http://en.wikipedia.org/wiki/Mach_(kernel)").

> **3rdalbum said:**
> For instance, a large number of OS X's libraries are direct ports of NeXTStep libraries. If you look through the API documentation, you'll find lots of function calls prefixed with the letters NS.


Things like NetInfo Manager and its concepts are directly from NeXT. Mac OS X's standard document type is PDF just a little more advanced than the display PostScript which NeXT used. Apple, I believe, wanted to avoid the copyright issues around Display PostScript. The Finder, however, is (unfortuneately) NOT related to NeXT or BSD in any way.
[URL="http://www.stanford.edu/~jhbrown/OSX/Old/final_report.htm"]
Mac OS X Public Betta, final Report[/URL] gives some good background. Of course that was 7 years ago.

Cheers,
MaXqUE

---

