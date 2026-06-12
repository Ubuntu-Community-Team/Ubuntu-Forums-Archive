---
title: "recordMyDesktop"
date: 2007-12-30
forum: Multimedia &amp; Video
---

### Post by Adler on 2007-12-30
Hi All,

I've worked with recordMyDesktop forever. 

I've got almost 30K hits on my Linux 3D YouTiube videos.

Recently, recordMyDesktop has not done what it had done in the past.

The performance has been poor.

Is there a repo out there?

Adler

---

### Post by papatrpt89 on 2007-12-30
Seems to me that Trevino has a repo out which includes it (for Feisty):

[http://3v1n0.tuxfamily.org/apt-repository/dists/feisty/3v1n0/](http://3v1n0.tuxfamily.org/apt-repository/dists/feisty/3v1n0/)

/etc/apt/sources.list lines:
```
deb http://download.tuxfamily.org/3v1deb feisty 3v1n0
deb-src http://download.tuxfamily.org/3v1deb feisty 3v1n0
```

You could also try a complete remove sudo apt-get remove --purge recordmydesktop and then reinstall.  If there is a directory called something like .recordmydesktop inside of your home folder, it may have some junk in it.  Be careful what you remove, though, your videos might be stored in there as well?

---

### Post by Adler on 2007-12-30
papatrpt89,

Thanks for that. Have you made any desktop videos using recordMyDesktop lately? 

I may just need to alter some of my GUI settings. 

Just a comment - I'm staying away from Trevino, and other repositories that aren't hosted in the official repositories. A good example here is Automatix - I used to "mix and match". But, that ended up being a mess! 

Let's see if any other Video Guys jump in here. There has to be a bunch.

Adler

---

