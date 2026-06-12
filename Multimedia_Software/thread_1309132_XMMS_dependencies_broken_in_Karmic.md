---
title: "XMMS dependencies broken in Karmic"
date: 2009-11-01
forum: Multimedia Software
---

### Post by hydrotemplar on 2009-11-01
When I try to install XMMS from .deb or compile from source, it complains of not having the proper version of libglib (binary wants >=1.2.10-18 and source wants 1.2.2)  and I have libglib 2.0 and the -dev.  If I'm not mistaken, this is the same as was in Jaunty.  Why is it no longer working, and how do I get around it?

Thanks,
David

---

### Post by Yellow Pasque on 2009-11-01
You need a libglib1.2 package (which is not in the Karmic repos)? You can probably get away with installing the version from Jaunty: [http://packages.ubuntu.com/jaunty/libglib1.2ldbl](http://packages.ubuntu.com/jaunty/libglib1.2ldbl)

---

### Post by zeus.jay on 2009-11-06
Guys to get xmms on karmic

Install jaunty versions of (for your architecture)

in order of install
libglib1.2ldbl_1.2.10-19build1
libglib1.2-dev_1.2.10-19build1

libgtk1.2-common_1.2.10-18.1build2_all.deb
libgtk1.2_1.2.10-18.1build2

Then install the jaunty version 

[http://www.pvv.ntnu.no/~knuta/xmms/](http://www.pvv.ntnu.no/~knuta/xmms/)

Only thing I noticed it it didn't install a launcher in Sound & Video, Easy enough to call from temrinal or open music file with custom command xmms. 

I'm sure someone can let us know how to create correct xmms.desktop file for it.

---

### Post by ihitf13anddied on 2009-11-08
Please see my post [here]("http://ubuntuforums.org/showpost.php?p=8272205&postcount=11") for instructions on how to install. I have attached a desktop launcher also.

---

### Post by billstei on 2009-12-13
I am using XMMS (Why? Because it uses libmpg123 which can save the stream to disk *and* play the stream simultaneously).  There is a problem with the packages/build described above... if I enable Options->Double Size, the main XMMS window is trashed (in Ubuntu Karmic).  Anyone know how to fix this?

---

### Post by billstei on 2009-12-21
I figured out what the problem was with Double Size...it is essentially the problem noted here:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=318093#10](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=318093#10)

but I was trying to run it with alltray, so it did not produce the Gdk-ERROR **: BadMatch error.  Ultimately I created a launcher script to start XMMS like this:

#!/bin/sh
export XLIB_SKIP_ARGB_VISUALS=1
alltray xmms

and Double Size (and alltray) are working fine now in Karmic :)

---

