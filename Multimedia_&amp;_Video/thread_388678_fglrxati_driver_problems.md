---
title: "fglrx/ati driver problems"
date: 2007-03-19
forum: Multimedia &amp; Video
---

### Post by dwiel on 2007-03-19
So, I've been through countless tutorials, forum searches and howtos installing ATI drivers every which way.  What I've got right now is this:

$ fglrxinfo
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

in my xorg.conf file:

Section "Extensions"
	Option	    "Composite" "0"
EndSection

I'm not sure where to go from here since it seems that everyone who has the XFree86-DRI missing on display ":0.0" error gets it fixed by adding the code to the end of the xorg.xonf file.

I had gave up on trying to solve this problem a week or two ago and have recently gotten back to it.  Not, In a few other attempts to get things reinstalled, I tried running the following commands:
sudo apt-get install fglrx
sudo apt-get install fglrx-xorg-driver
sudo apt-get install xorg-driver

and they all respond with:
E: Couldn't find package fglrx
or whichever it is I am trying.

It seems this might be something missing from my soruces.list, but it seemed ok:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main
deb [http://ntfs-3g.sitesweetsite.info/ubuntu/](http://ntfs-3g.sitesweetsite.info/ubuntu/) edgy main main-all
deb [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) edgy main main-all
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe multiverse

Might I be missing something there?
I don't think that is my main problem, as this problem was not occurring before, only now that I revisit the issue.

Any ideas about what might be going on?

Thank You

---

### Post by jocko on 2007-03-19
The correct name of the package you want to install is **xorg-driver-fglrx**.
**Hint:** If you don't remember the complete name of a package, use the search function in synaptic.

---

### Post by dwiel on 2007-03-19
Thanks.  I put that in, and it looks like It was one of the packages I installed last week when I was working on this.  Searching synaptic would definitely have been a good idea.  I hadn't thought to use it like that.

Any other ideas about what could be going on?

---

### Post by NT4usB on 2007-03-19
I didn't see which ATi card you are running...
Did you try tseliot's skript? Works great for the 9600 Pro in my Edgy box.
[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)
Remember to uninstall (via the skript) first before installing.

---

### Post by dwiel on 2007-03-19
So, I was looking at this: [http://albertomilone.com/instructions.html](http://albertomilone.com/instructions.html)

I saw at the very end:
    WARNING!
    Make sure that neither the word "nv" or the word "flgrx" is  in inverted comas after the word DISABLED_MODULES= in your /etc/default/linux-restricted-modules-common

This was infact in my DISABLED_MODULES= list.  I have absolutely no idea why.  Anyway, that fixed my Xlib: extension "XFree86-DRI" missing on display ":0.0". error.  However I am still getting this for fglrxinfo:
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

So it doesn't look like it is using the right drivers.  Should I try uninstalling and reinstalling my drivers?  I know that I can use apt-get uninstall or just synaptic to uninstall packages installed with it, however, I alsoI know that at one point, I installed from the drivers located at the ATI website.  How can I uninstall these drivers?

Thank You

P.S. I am trying to get an ATI Radeon 9600 SE configured

---

### Post by dwiel on 2007-03-19
So that fixed it.  Finally.  Thanks for the link.

What fixed it was removing flgrx from the DISABLED_MODULES and then reinstalling everything with the repo from that link.

Thank You

---

