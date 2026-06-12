---
title: "Copy DVD movie to blank DVD"
date: 2008-12-23
forum: Multimedia Software
---

### Post by JGT on 2008-12-23
I'd like to copy ordinary (dual layer) commercial movie DVDs onto ordinary writable single-layer blank DVDs, i.e. back up movies onto blank disks that can play in ordinary DVD players.

I'm not interested in ripping to the hard drive except as required as a temporary measure in the encoding/shinking process, etc.

I know there are a lot of tools available but it's a complex area.

Many tutorials contain complex information about selecting what parts of the DVD I would like, and convesion to other file formats, but I would just like to make clones of disks, albeit with loss of quality due to shrinkage to fit the single side.

Is there a simple command line way to do this (i.e. so I don't have to choose from zillions of options in different programs) or otherwise a simple and reliable way to do this?

Thanks

---

### Post by rudy.elgato on 2008-12-23
Hi JGT,

I'm running Ubuntu 8.04.1 and have just started doing exactly what you're asking for, and it's really, really simple.  Alot simpler then I ever thought it would be.

I'm using "k9copy" to rip an existing dvd to an online *.iso image.  And then use "k3b" (or brasero, which is preinstalled with Ubuntu 8.04) to burn the *.iso to a blank 4.7GB dvd.  There are several other sets of tools that can do the same thing, but k9copy and k3b worked fine the very first time I even tried, so I'll stick with them.  

k9copy and k3b are not installed by default, but are available in the repositories, so if you decide to use them you'll have to install them (using synaptic package manager).  Here's a link I used that provided enough information to get me started using k9 copy, [http://www.dvd-guides.com/content/view/213/59/]("http://www.dvd-guides.com/content/view/213/59/").  To make an exact copy of everything on the dvd simply select the main title name.  After that it's pretty much just providing the location and name of your output iso image, then let it run.  

An hour or so later you'll have an iso image that you can burn to your blank dvd.  After that, you should have an exact copy of your original dvd, complete with menus and all options.  You can remove the online iso image and all k9copy intermediate files to free up that space.

It can be made a good deal more complicated if you want to be selective in what you rip from an existing dvd, but for complete copies, it's really quite simple.  It might seem a little confusing the first time you try, but after that, you'll realize it takes about 3 clicks in k9copy and 2 more clicks in k3b to get a complete copy.

Give it a go.  Good luck...

---

### Post by binbash on 2008-12-23
k9copy is a good one but i prefer wine + dvdshrink

---

### Post by SuperSonic4 on 2008-12-23
k9copy and k3b is an excellent kombo ;) but it'll require a lot of KDE dependencies. I tried burning an ISO with K3b but it won't play in my dvd player (the iso being tom and jerry :p)

---

### Post by JGT on 2008-12-23
Thanks for the quick replies. I'll give them a go.

Cheers

---

