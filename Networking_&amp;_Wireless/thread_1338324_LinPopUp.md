---
title: "LinPopUp"
date: 2009-11-26
forum: Networking &amp; Wireless
---

### Post by Mike Easter on 2009-11-26
I would like to install linpopup in Ub 9.10. Previously ie 9.04 and other similar distros, it could be found in the ub repos, but not 9.10.

Linpopup requires sambaclient stuff

I downloaded linpopup_1.2.0-8.3_i386.deb from the debian archives.  It sez (in the package installer) that it is maintained by the Ub MOTU developers.

When I tried to install the .deb in 9.10 I got an alert:

Error: Dependency is not satisfiable: libglib1.2ldbl (>= 1.2.10-18)

Presumably that is because my 9.10 libglib is 2.

From synaptic:  
Package: libglib2.0-0 Version: 2.22.2-0ubuntu1

How do I deal with this older libglib dependency issue?  Should I learn how to compile something for linpopup?

---

### Post by Mike Easter on 2009-11-30
> **Mike Easter said:**
> I would like to install linpopup in Ub 9.10.

Should I learn how to compile something for linpopup?

I've never compiled anything, but I decided to try this.  It seems to be more complicated than I expected.

I downloaded linpopup-2.1.0.tar.gz

The install file gives no advice about needing to install lots of other stuff, but in order to get the package ready it was necessary for me to install the following:

build-essential
libgtk1.2-dev
libxmu-headers
libxmu-dev

If anyone is interested in all of that, the details of the difficulties can be seen in the newsgroup thread:

alt.os.linux.ubuntu Sub: LinPopUp Nov 26 
Message-ID: <7n5a41F3k45jeU1@mid.individual.net>

---

### Post by Ubuntolonius on 2009-12-05
Unfortunately linpopup is not supported anymore by Ubuntu 9.10. But you still can load it from the Ubuntu 9.04 repository.
Do the following:

add "deb [http://ftp.energotel.sk/pub/linux/ubuntu/](http://ftp.energotel.sk/pub/linux/ubuntu/) jaunty universe" to your packet sources as third party software.

When you are done, you can simply install linpopup in the Synaptic package management.

It is recommended to remove the Ubuntu 9.04 repository afterwards from the packet sources.
 
Cheers,
Ubuntolonius

---

