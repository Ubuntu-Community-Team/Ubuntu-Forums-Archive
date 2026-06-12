---
title: "OSX Fink vs Ubuntu"
date: 2006-12-02
forum: Mac OSX
---

### Post by stream303 on 2006-12-02
One of the reasons I bought a Mac was that I had quite a few choices of what to run: OSX, X11 via Fink, or obviously Linux.

[http://www.macdevcenter.com/pub/a/mac/2005/09/30/fink.html?page=1](http://www.macdevcenter.com/pub/a/mac/2005/09/30/fink.html?page=1)

[http://fink.sourceforge.net/](http://fink.sourceforge.net/)

Any hardcore Fink/X11 users here?  I'm running a dedicated Ubuntu Edgy install on my G5 iMac, but toyed with the idea of getting X11/Fink running.

---

### Post by aysiu on 2006-12-02
I've used Fink on my wife's Powerbook. I like it, but the software selection is a bit limited. I wish I had all the Ubuntu repositories available...

---

### Post by wgscott on 2006-12-03
I maintain some fink packages so I am not a neutral observer, but I am very pleased with it and completely dependent upon it and X11, etc to do my work.  I've put together [a website with more details]("http://xanana.ucsc.edu/xtal/wiki/index.php/Main_Page") if you are interested. It was in fact my appreciation of fink that brought me to Ubuntu (fink uses the debian toolset for package management).

BTW if something is missing someone is usually willing to put together a package.

---

### Post by aysiu on 2006-12-03
> **wgscott said:**
> 
BTW if something is missing someone is usually willing to put together a package. Mind if I ask what the general protocol is for requesting a package?

---

### Post by stream303 on 2006-12-03
Wow - that's the kind of info I needed.  Thanks for the nice web-docs.   The furthest I got way back when was just installing the X11 package and running twm and xeyes.  I think I can go further now - your site has motivated me for sure.

---

### Post by wgscott on 2006-12-03
> **aysiu said:**
> Mind if I ask what the general protocol is for requesting a package?

The official way is to request it here:

[http://sourceforge.net/tracker/?atid=371315&group_id=17203](http://sourceforge.net/tracker/?atid=371315&group_id=17203)

Probably a better way is to contact a maintainer of similar packages (say you need a gnome package, find who maintains a lot of them, and drop them an email and get them interested).

If you want, you can also roll your own and submit it to the package tracker for incorporation.

[http://sourceforge.net/tracker/?atid=414256&group_id=17203](http://sourceforge.net/tracker/?atid=414256&group_id=17203)

and in my experience when they get sick of you submitting so many packages, they will make you a maintainer (there's a vetting process, and I was/am a slow learner, but the tradeoff is quality control).

---

### Post by aysiu on 2006-12-03
Thanks for the info, wgscott.

---

### Post by wgscott on 2006-12-03
> **stream303 said:**
> Wow - that's the kind of info I needed.  Thanks for the nice web-docs.   The furthest I got way back when was just installing the X11 package and running twm and xeyes.  I think I can go further now - your site has motivated me for sure.


It is very slanted toward my own interests (biophysics type stuff) but the basic ideas are completely general.  

I think Apple does not publicize this much, but you can compile and run just about anything that does not uniquely depend on the linux kernel on OS X (which is a BSD variant, BTW).  I've been making heavy daily use of all sorts of X11 gui applications on OS X for at least the last four years.

---

