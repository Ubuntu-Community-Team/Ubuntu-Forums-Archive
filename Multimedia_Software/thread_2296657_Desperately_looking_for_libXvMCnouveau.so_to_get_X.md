---
title: "Desperately looking for libXvMCnouveau.so to get XvMC support working"
date: 2015-09-27
forum: Multimedia Software
---

### Post by syntaxerror74 on 2015-09-27
Well, this is one of the howto's I love most.
[http://nouveau.freedesktop.org/wiki/VideoAcceleration/](http://nouveau.freedesktop.org/wiki/VideoAcceleration/)

IMO Nouveau people have never been candidates for winning the pole position in documentation quality, and I guess they never will...

> 
Using XvMC
Note: There was a problem with Mesa 9.1 (and 9.0) libXvMCnouveau.so in that it couldn't load. You can use this patch to fix it up. (...)
You need to point your /etc/X11/XvMCConfig at the libXvMCnouveau.so library

Mesa 11 here. 
No **libXvMCnouveau.so** ANYWHERE.

Is there no official package in the Ubuntu repos that includes this shared library?
I just could not believe that.

But it definitely is not in /usr/lib, nor in /usr/lib/i386-linux-gnu, nor in /usr/lib/dri, nor in /usr/lib/i386-linux-gnu/dri.
And this is why I ranted about the howto.
You're told to adjust your /etc/X11/XvMCConfig (already available here!) accordingly, but nobody tells you WHERE this .so is located.
Oh, and I've also used 'locate' to no avail.

I'm about to give up...help please!

---

### Post by Yellow Pasque on 2015-09-28
> Is there no official package in the Ubuntu repos that includes this shared library?

Nope. It would be in the mesa-vdpau-drivers package, but Debian/Ubuntu builds mesa with --disable-xvmc (don't ask me why..)
oibaf's PPA builds with xvmc (and a lot of other changes over the stock mesa): [https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers)

> You're told to adjust your /etc/X11/XvMCConfig (already available here!) accordingly, but nobody tells you WHERE this .so is located. And this is why I ranted about the howto.
Calm down and quit blaming the nouveau devs. It's not their job to document how each distro builds mesa and where they put library files.

> IMO Nouveau people have never been candidates for winning the pole position in documentation quality
I've found their documentation helpful, especially when it comes to extracting VDPAU firmware and dealing with optimus/hybrid graphics. Considering that they have little documentation to work with themselves, it seems like a bonus that they document stuff at all :P

---

