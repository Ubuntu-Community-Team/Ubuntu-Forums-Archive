---
title: "Getting flash to work with Browser Screenlet/How does Mozilla know Flash is installed"
date: 2009-06-28
forum: Multimedia Software
---

### Post by VOLKOV9 on 2009-06-28
Hey, noob question here:  How does Mozilla know Flash is installed?  Or, when clicking something triggers "this requires flash > n: please install the latest version here," what's it checking?

Flash works in my normal firefox.  I'm trying to get it to work in the Browser Screenlet (where I get an instance of the aforementioned hiccup).  This applet has its own mozilla/ directory, which has Cache, cert8.db, cookies.sqlite, key3.db, mimeTypes.rdf, permissions.sqlite, places.sqlite, pluginreg.dat, prefs.js (the version the app comes with dresses it as an iphone), and secmod.db.  (After backing these up), first I tried symlinking to the prefs.js and puginreg.dat that my functional firefox uses.  no luck.  so i tried replacing all the applet's files in that list with symlinks to real firefox.  still no.  finally, symlinking the whole directory containing the real firefox's files to the applet's did not work.  I clearly have no idea what I'm actually doing.  I think something I don't understand that seems important is the relationship between firefox and mozembed (which the app uses).

If anybody could help me try to get flash working in the Browser Screenlet, I'd appreciate it.  i.e., thanks in advance.

---

