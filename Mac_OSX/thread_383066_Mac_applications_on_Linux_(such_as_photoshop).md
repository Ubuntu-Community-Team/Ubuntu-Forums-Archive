---
title: "Mac applications on Linux? (such as photoshop)"
date: 2007-03-12
forum: Mac OSX
---

### Post by blueraven on 2007-03-12
This is probably something that has been covered by people before, but I did a quick search and couldn't find anything concrete.

Now that there is a Crossover Mac package to run Windows apps in Mac, is seems logical with my limited knowledge that it would be possible to make a WINE compatibility layer for MAC applications to work in Linux?

After all, aren't they both based on Unix? Surely its fairly similar?

I get the feeling that Mac versions of Photoshop for instance would work a lot better than trying to get Windows ones to, as CS2 still doesn't have a clear cut solution.

---

### Post by Tipo on 2007-03-12
You might want to check out the [Mac-On-Linux]("http://mac-on-linux.sourceforge.net/news.php") project

---

### Post by LMP900 on 2007-03-12
> **Tipo said:**
> You might want to check out the [Mac-On-Linux]("http://mac-on-linux.sourceforge.net/news.php") project

Interesting project. Thanks for link. :)

However, I believe the original poster wasn't looking for a virtualization of the whole Mac operating system - just on the application level. Unfortunately, I can be of no help. I haven't heard of any major projects to virtualize Mac apps on Linux.  Although I do wonder how they would deal with the "File Edit Help etc." menu if they did have Wine-type virtualization for Mac apps...

---

### Post by blueraven on 2007-03-12
Thats right. While a cool looking application, emulation iof the operating system isn't what I was after.

I've often asked myself the question - if they are so similar, shouldn't it be easier?

---

### Post by RAV TUX on 2007-03-12
moving to the Mac OS X forum.

---

### Post by BOBSONATOR on 2007-03-12
Yes, i have wanted to run Final Cut on ubnutu..

---

### Post by blueraven on 2007-03-12
A bit of Google and I found this... [http://linuxrevolution.blogspot.com/2006/02/mac-apps-on-linux.html]("http://linuxrevolution.blogspot.com/2006/02/mac-apps-on-linux.html")


> Great idea, but other than the technical reasons why it's not done, there's the legal. Unlike Linux, OS X's GUI (Aqua) is not open-source. If someone ported it to Windows, they would sue on copyright infringement and other things.

Not to mention that there are two main APIs at work on OS X: Cocoa and Carbon. Cocoa uses Objective C and was used on the NeXT cube. This is what GNUStep does. Carbon, on the other hand, uses old code used on classic Macs (i.e. the Toolkit) and has only came to the form we know now when Apple needed a transition API for their old programmers. It uses C++. It is completely Apple's work.

Those are just the main GUI frameworks. The kernel is another story (there's a reason why a program on OS X can run on both PPC and X86 while still being in one file {and I'm not talking bundles}) I think it would be a lot of hard work to get the ls command to work.

Apple is a company. It needs to make money. We wouldn't want to see such an innovative company go down, and neither does Microsoft. How else would it come up with new ideas to suck money out of our wallets?

As for my opinion, I say let Apple be. It needs some edge up from MS, since most of its ideas, while good, seem to pale in comparison to MS's amoral monopoly.
And yes, I'll probably get flamed for this :(

---

### Post by 3rdalbum on 2007-03-13
People don't quite seem to understand what a kernel does.

The kernel handles really low-level stuff - loading things into memory, providing a way for programs to interface with the hardware, that sort of thing. A normal program doesn't communicate directly with the kernel, it communicates with middlemen known as "libraries" and "servers".

For instance, I'm running Firefox right now, typing into this message. The Linux kernel isn't telling Firefox "Right, the user hit this key". The kernel actually tells the "glibc" library that a key has been pressed. Glibc tells the X server that the key has been pressed. The X server notices that the active window belongs to Firefox, and that the GTK library is waiting for keypress events. So X sends the keypress event to GTK, and GTK may send it to Firefox.

So, you see, the kernel only starts the chain of messages. Not one single line of Firefox's source code actually sends any messages directly to the kernel; all the messages go to libraries. Most of the Mac OS X libraries are closed-source, just like Windows' libraries - so you'd need as much reverse-engineering to get Mac OS programs to run on Linux as you would to get WINE working.

And Apple's hacked-up, mish-mashy hybrid of kernels is probably not going to make things much easier for developers - sure, there's a /dev directory that contains familiar device files, but all that could easily be emulated on a non-POSIX kernel anyway.

(By the way, Mac-on-Linux only works on PowerPC).

---

### Post by blueraven on 2007-03-13
Thanks for clearing that up - you learn something new everyday :)

So therefore, the reason this particular application doesn't exist points, probably, more to the fact that there is a smaller fanbase of Mac users and less likelyhood that an experienced programmer has been interested in spending years reverse engineering Mac software to run on linux for no real profit or need?

---

### Post by Auria on 2007-03-14
> it would be possible to make a WINE compatibility layer for MAC applications to work in Linux?

It is technically possible, but you'll need to find a big team of volunteers ready to work for several years before you get something even barely usable. Reimplementing everything Apple has done on OS X is a huge task!

---

### Post by www.rzr.online.fr on 2008-09-25
> **Auria said:**
> It is technically possible, but you'll need to find a big team of volunteers 

IMHO, wine has nothing to share w/ cocoa or carbon ?

Maybe apple binary support is a task related to gnustep :

[http://wiki.gnustep.org/index.php/Cocoa](http://wiki.gnustep.org/index.php/Cocoa)

I need this to test iPhone SDK on GNU/Linux ? Any tracks welcome ?

-- 
[http://rzr.online.fr/q/macos](http://rzr.online.fr/q/macos)

---

