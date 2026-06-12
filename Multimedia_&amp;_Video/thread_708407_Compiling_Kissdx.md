---
title: "Compiling Kissdx"
date: 2008-02-26
forum: Multimedia &amp; Video
---

### Post by Morgonte on 2008-02-26
I'm trying to install Kissdx, which is a media server application intended to send media content to a Kiss networked DVD player. I'm running xubuntu 7.10.

I've followed the instructions found here: [http://www.famille-kahn.com/kissdxmanual/Kissdx_user_manual:Linux_Installation#Debian_:_Installation_from_source](http://www.famille-kahn.com/kissdxmanual/Kissdx_user_manual:Linux_Installation#Debian_:_Installation_from_source)

However, when I do "make" or "make install" all I get is long lines of errors (unfortunately in Swedish). 

I've installed libdvdread3, libdvdread-dev, libjpeg62 and libjpeg-progs.  I cannot find libiconv, and tried to remove -liconv from the makefile, as the makefile suggests, but no success.
When Synaptic tries to install libjpeg62-dev it refuses to install it and I get a message that libjpeg62-dev has "unsolvable bindings" (my translation from Swedish) to libc-dev.

As you may have noticed, I have no great knowledge of what I'm actually doing, I simply try to follow the instructions I've found. 

Is there anyone who can tell me what's the problem and how to solve it?

/Stefan

---

### Post by Morgonte on 2008-02-26
I found a precompiled package at [http://www.mpcclub.com/modules.php?name=Forums&file=viewtopic&t=15036](http://www.mpcclub.com/modules.php?name=Forums&file=viewtopic&t=15036)

However,  after adding the source and typing "apt-get install kissdx" I get:

> Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  kissdx: Depends: libjpeg62-dev but it is not going to be installed
E: Broken Packages
(Actually, the text above was in Swedish, I got the correct English equivalent from another post and changed the package names.)

Seemes like the problem is libjpeg62-dev. How can I install it?

/Stefan

---

