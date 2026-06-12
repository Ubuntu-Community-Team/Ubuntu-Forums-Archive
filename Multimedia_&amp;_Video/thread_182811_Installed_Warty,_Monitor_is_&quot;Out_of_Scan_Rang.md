---
title: "Installed Warty, Monitor is &quot;Out of Scan Range.&quot;"
date: 2006-05-26
forum: Multimedia &amp; Video
---

### Post by ryharv on 2006-05-26
Hello all,

I recently reinstalled Warty on a new hard drive (I know Warty's not the newest, but I'm lazy and have the CD).  

Anyway, this never happened before on my old install, but before the desktop will open up, my monitor goes black and says, "Out of Scan Range."  

I've browsed around the forums here and tried two things, to no avail:

1.  Tried to edit /etc/X11/xorg.conf.  Unfortunately, after a fresh install, I do not have a file called xorg.conf.  I can find the /etc/X11 directory, but there is no such file.

2.  Tried "dpkg-reconfigure xserver-xorg"

The system replies "xserver-xorg is not installed."  So I try to install it using apt-get install.  System replies that it "couldn't find package xserver-xorg."  

I am able to boot and get back to a command line, but I can't load up the desktop.  Can anybody help?  My monitor, for what it's worth, is a Sony Trinitron Multiscan 220GS.  I'll do the legwork and find out all its specs, if I can find where in Ubuntu to input them.

Thanks all for your help.

  Ryan

---

### Post by rado_london on 2006-05-26
Well as far as I know warty uses xfree86. So dont be lasy and get breezy or even Dapper that have X.org and much better monitor and res. support.

---

### Post by Sef on 2006-05-26
Warty is no longer supported, so update.  Either download or get the CDs via ship-it.

---

### Post by Mustard on 2006-05-26
Do you have an X86Config file instead of an xorg.conf?

Sounds like it would be easier to upgrade to the latest Ubuntu.

---

