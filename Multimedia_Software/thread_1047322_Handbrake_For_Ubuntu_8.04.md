---
title: "Handbrake For Ubuntu 8.04"
date: 2009-01-22
forum: Multimedia Software
---

### Post by goochpsk on 2009-01-22
I'm extremely new to ubuntu. I recently built a htpc and am using ubuntu 8.04 and then installed boxee. The downloads for Handbrake are for ubuntu 8.1. Does anyone know how to install handbrake for ubuntu 8.04? Any help would be greatly appreciated.

---

### Post by wolfen69 on 2009-01-22
[Here]("http://trac.handbrake.fr/wiki/CompileGuide#cli") is a very easy to follow guide to compile your own. plus, you'll be able to brag to your friends that you know how to compile something from source.

---

### Post by doug1212 on 2009-01-22
Hi,
Some kind soul seems to have already built Handbrake for 8.04:

[HTML]https://edge.launchpad.net/~handbrake-ubuntu/+archive/ppa[/HTML]

Doug.

---

### Post by brake16 on 2009-05-20
> **wolfen69 said:**
> [Here]("http://trac.handbrake.fr/wiki/CompileGuide#cli") is a very easy to follow guide to compile your own. plus, you'll be able to brag to your friends that you know how to compile something from source.

Good Morning

I followed this guide to install Handbrake on my 8.04 system, and I get this error after typing make:

make: *** No targets specified and no makefile found.  Stop.


I had previously tried Doug1212's suggestion, but that was a dead link.  Any ideas?

Thanks
brake16

---

### Post by Arup on 2009-05-20
> **brake16 said:**
> Good Morning

I followed this guide to install Handbrake on my 8.04 system, and I get this error after typing make:

make: *** No targets specified and no makefile found.  Stop.


I had previously tried Doug1212's suggestion, but that was a dead link.  Any ideas?

Thanks
brake16


sudo apt-get build-essentials

extract the handbrake source and cd, then do .make

---

### Post by tacantara on 2009-05-20
I ran a Google search and came up with this link for guidance on installing Handbrake on Ubuntu 8.04

[http://en.flossmanuals.net/Handbrake/InstallingUbuntu](http://en.flossmanuals.net/Handbrake/InstallingUbuntu)

I skimmed over it, and it seems pretty detailed.  If this doesn't work, run a Google search.  There's quite a bit of information on this in search land.

---

