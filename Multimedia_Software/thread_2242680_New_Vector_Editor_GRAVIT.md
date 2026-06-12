---
title: "New Vector Editor: GRAVIT"
date: 2014-09-03
forum: Multimedia Software
---

### Post by samigina on 2014-09-03
A german company have released a beta for his new design tool Gravit:[ http://gravit.io/]("http://gravit.io/")

From the site:

> Meet Gravit &#8211; the cutting-edge design app that will take your creativity to new heights. Gravit offers the creative possibilities of a full-scale design suite - but in a snug app-sized package. Powerful yet easy-to-handle, Gravit has been custom designed from the ground up with an emphasis on versatility, fluidity and elegance &#8211; complex design tasks are made simple through its robust suite of tools and highly responsive smart work environment. Express yourself in a new way with Gravit &#8211; the new must-have tool for today&#8217;s pioneering design professionals!

They have plans for CMYK and PANTONE support.

Interview in Libregraphicsworld: [http://libregraphicsworld.org/blog/entry/quasado-opensources-gravit-web-based-design-tool](http://libregraphicsworld.org/blog/entry/quasado-opensources-gravit-web-based-design-tool)

Sourcecode in github: [https://github.com/quasado/gravit/tree/master/src/gravit](https://github.com/quasado/gravit/tree/master/src/gravit)

Linux binary: [https://github.com/quasado/gravit-hub/releases/download/v0.0.3.1/Linux.zip](https://github.com/quasado/gravit-hub/releases/download/v0.0.3.1/Linux.zip)

---

### Post by dgriffiths on 2014-09-03
It should be noted that while this is a pretty cool project, the Linux downloadable doesn't work (at least for me) due to a version conflict with one of it's libs, and the source won't compile due to missing npm requirements... Web version worked well enough though!

---

### Post by samigina on 2014-09-06
> **dgriffiths said:**
> It should be noted that while this is a pretty cool project, the Linux downloadable doesn't work (at least for me) due to a version conflict with one of it's libs, and the source won't compile due to missing npm requirements... Web version worked well enough though!

Workaround for the libudev issue:

For x64:
sudo ln -sf /lib/x86_64-linux-gnu/libudev.so.1 /lib/x86_64-linux-gnu/libudev.so.0

For x32:
sudo ln -sf /lib/i386-linux-gnu/libudev.so.1 /lib/i386-linux-gnu/libudev.so.0

---

### Post by Sasha_Aderolop on 2014-09-15
When trying to run the linux binary on Ubuntu 14.04 (and Manjaro) I get this error:
  error while loading shared libraries: libudev.so.0: cannot open shared object file: No such file or directory
  But libudev is installed.

---

### Post by myrkat on 2014-09-18
Just downloaded it now and checked it out.  I use Xara extensively, and have not had any luck finding something remotely close to it in terms of performance and capabilities; but, I am hopeful.

Gravit seems quick, but it really isn't doing anything spectacular.  The basics are there, and I like the style and linking (especially the master page setting); however, some obvious shortcuts are missing - most notably, the pan feature using the middle button on the mouse, and the zoom in/out via CTRL+mousewheel.  Standard stuff (or something similar), as selecting the pan tool to move around will get old fast.

For what is there, I do like the layout of it... reminds me of the old Freehand days before it was devoured by Adobe... twice.

Thank you for the info, I'll be keeping my eye on this one - even though it has a ways to go, it seems off to a good start.

---

### Post by Steve_Rose on 2014-09-20
Hi myrkat 
i thought Xara was sadly, pretty much dead. It was a great app with huge potential, but the development trail died out about 2009. I've been looking for a suitable Linux based vector illustration app since MicroSoft went to Vista etc.. I've used CorelDraw professionally since version 2 and wouldn't choose anything else from a productivity / quality of artwork point of view, but along with Adobe CS they're become stuck on MicroSoft/Apple platforms and now their rental/ license model totally sucks. 

My Xp machines are over due replacement. Linux is the logical step forward. Fine for everything except graphic design. Wine doesn't seem capable of supporting CorelDraw versions after 9. Or at least not without flakiness. 

If Xara really is a viable graphic design app on current distros that'd be great news.
Cheers

---

### Post by Sasha_Aderolop on 2014-09-20
> **myrkat said:**
> Just downloaded it now and checked it out.  I use Xara extensively, and have not had any luck finding something remotely close to it in terms of performance and capabilities; but, I am hopeful.

Gravit seems quick, but it really isn't doing anything spectacular.  The basics are there, and I like the style and linking (especially the master page setting); however, some obvious shortcuts are missing - most notably, the pan feature using the middle button on the mouse, and the zoom in/out via CTRL+mousewheel.  Standard stuff (or something similar), as selecting the pan tool to move around will get old fast.

For what is there, I do like the layout of it... reminds me of the old Freehand days before it was devoured by Adobe... twice.

Thank you for the info, I'll be keeping my eye on this one - even though it has a ways to go, it seems off to a good start.

What can you tell about Xara? Really Gravit is better that Xara?

---

### Post by myrkat on 2014-10-13
Sorry for such a late reply (forgot to subscribe to thread!) - anyway, Xara IS dead on linux, and has been for a number of years.  That said, under Windows it is absolutely brilliant!  It is the sole application for keeping windows around for me.  Thankfully, it runs *somewhat* well under an Oracle VM (it's not as quick as native via dual booting into windows).  They just released Xara Designer X10 (I am on X9, haven't done the upgrade yet).  If you keep windows because linux is a dead end for graphic design (sorry, but it is as of this writing), then I recommend checking out Xara.

I'm forcing myself to use Inkscape, but it is SO clumsy and cumbersome, not to mention slow as molasses...  Xara has spoiled me, I think.

---

### Post by Drizz on 2015-01-31
Sadly I have to agree. Although I'm still running Xara Xtreme 5 on my Windows install, it's a great app. But currently running Xara Xtreme v2 in a Windows 7 VM which seems stable, using that to work on some old .xar files. Pity inkscape doesn't support that file type.

---

### Post by Cope57 on 2015-01-31
Seen the title of this topic, and I thought that Gravit was a [gravity simulator for linux]("https://en.wikipedia.org/wiki/Gravit") that uses OpenGL.
Apparently another individual has used the same name for their application.  This could be interesting since Gravit was created ten years ago.

**Edit**: More links for gravit.

[https://github.com/gak/gravit/](https://github.com/gak/gravit/)
[https://www.openhub.net/p/Gravit](https://www.openhub.net/p/Gravit)
[http://slowchop.com/](http://slowchop.com/)

---

