---
title: "OSX and BSD... How similar?"
date: 2008-10-17
forum: Mac OSX
---

### Post by jesushero on 2008-10-17
I have not used a Mac for ages, and I was wondering of the capabilities of modern Macs. Last time I used one, I brought up a man page on the console and noticed that at least some if not all of the man pages are directly ported from BSD. How much of BSD is actually present on OSX? 

More specifically: 

Is pkg_add there?

Can I do this: 
```
export PKG_PATH=ftp://ftp.link.to/tgz/packages
pkg_add -i somepackage
```

?

---

### Post by handy on 2008-10-18
You may find this interesting:

***_[http://www.macports.org/](http://www.macports.org/)_***

I tried it using it about 10 months ago & it didn't work very well for me on my Alu' iMac.  I'm sure that macports has improved & will keep on improving.

Personally I'd rather use Arch on my iMac than Leopard.

---

### Post by techmarks on 2008-10-18
Macs and BSD go back awhile.
The 386BSD was out in 1991 and it was ported to the Mac under the name MacBSD. 

Something I didn't know was that an early Macintosh architecture was running a free Unix before the Intel chip had any BSD at all available for it!

FreeBSD code has been running on some sort of Mac since Darwin, the OSS kernel of Mac OS.

It's interesting to note that quite a few of the FreeBSD developers are Apple employees.

---

### Post by 3rdalbum on 2008-10-19
Macs and Unix go back further. Apple originally investigated implementing a GUI on top of Unix for use on the Lisa, but concluded that it would be easier to write an entirely new operating system than to give Unix support for the mouse and the GUI.

To answer the question: The man pages are from BSD, and some of the packages are the same, but Apple's had its grubby fingers in the code for a lot of the BSD system that ends off in OS X. As well as other open-source software that ends off in OS X. Honestly, if you were into BSD, you'd probably feel more at home with GNU than with Mac OS X, unless you were leet at the command-line and remembered heaps of BSD-specific parameters for the commands.

Where do the FreeBSD developers work at Apple? Wherever they are, they obviously don't have enough power to make Apple design things with a reasonable level of designed security.

---

