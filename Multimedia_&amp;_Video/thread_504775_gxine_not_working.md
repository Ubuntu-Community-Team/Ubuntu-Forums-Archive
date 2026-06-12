---
title: "gxine not working"
date: 2007-07-19
forum: Multimedia &amp; Video
---

### Post by petroskhan on 2007-07-19
For a long time, I have been using gxine, and had no trouble with it.  All of a sudden, it's not working, and giving me a Fatal Error - Segmentation Fault.  At or around the same time, Amarok stopped working as well.  Anyone have any ideas on this?  I'm pretty confused here.

---

### Post by DoruHush on 2007-07-19
Did you update your qt4 from 4.2.3 to 4.3 version?
It was an update that came from the backports channel two days ago.
The reason I ask that is that I do that and my smplayer 
do not work since than, and I use that program every day.
Even mplayer starts to act funny.
I know it is not a solution, and I'm sorry for that, but maybe it is a start 
for somebody who can really help.

---

### Post by Gremlinzzz on 2007-07-19
did ya try uninstalling then reinstall. 
sudo apt-get autoremove gxine
sudo aptitude install gxine

---

### Post by Gremlinzzz on 2007-07-19
> **DoruHush said:**
> Did you update your qt4 from 4.2.3 to 4.3 version?
It was an update that came from the backports channel two days ago.
The reason I ask that is that I do that and my smplayer 
do not work since than, and I use that program every day.
Even mplayer starts to act funny.
I know it is not a solution, and I'm sorry for that, but maybe it is a start 
for somebody who can really help.

[http://ubuntuforums.org/showthread.php?t=503828&highlight=smplayer](http://ubuntuforums.org/showthread.php?t=503828&highlight=smplayer)

---

### Post by DoruHush on 2007-07-19
@Gremlinzzz

Thanks!
It solved some problems, but not all.

---

### Post by petroskhan on 2007-07-20
I was pretty sure I had tried that already, but I decided to double-check, and it doesn't work.  I keep getting a Fatal Error - Segmentation Fault.  I really hate this, since I do use gxine a lot.  I've un- and re-installed now a couple of times, through Synaptic, and manually through the terminal, but it's still giving me the same problem.  It's really curious, since around the same time, and for sure in the same day, Amarok stopped working, too.  Help...sniff...I need a hug.

---

### Post by Gremlinzzz on 2007-07-20
Maybe if you reinstalled from a package
[http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fg%2Fgxine%2Fgxine_0.5.11-3_i386.deb&md5sum=2d0e1cfa7197d0ad5982e8eabe4e3ae4&arch=i386&type=main](http://packages.debian.org/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fg%2Fgxine%2Fgxine_0.5.11-3_i386.deb&md5sum=2d0e1cfa7197d0ad5982e8eabe4e3ae4&arch=i386&type=main)

---

### Post by petroskhan on 2007-07-20
One weird problem after another.  Now, when I try to install the package, it tells me that there is a dependency that is not satisfiable - libc6.  Odd thing, it's already installed.  Could the package be looking for it in the wrong place?

---

### Post by petroskhan on 2007-07-23
Anybody else out there have any clues/hints/ideas on this?  I'm really confused, and I don't even know what the hell a Segmentation Fault is.

---

### Post by Gremlinzzz on 2007-07-23
try this again 
sudo apt-get autoremove gxine
sudo aptitude install gxine
that update has been fixed

---

### Post by petroskhan on 2007-07-23
Grrr...same thing.  Fatal error - Segmentation Fault

---

### Post by Gremlinzzz on 2007-07-23
Did ya get your updates
sudo apt-get update
sudo apt-get upgrade
or use your update manager

---

### Post by petroskhan on 2007-07-23
Sorry about the delay in answering.   Yeah, I have done all the updates, and the upgrades.  Still giving me the same problem

---

