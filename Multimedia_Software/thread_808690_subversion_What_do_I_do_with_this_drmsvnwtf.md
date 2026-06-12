---
title: "subversion: What do I do with this??? drmsvnwtf"
date: 2008-05-26
forum: Multimedia Software
---

### Post by uncleclinto on 2008-05-26
Okay, so I've gone all Ubuntu about 6 months ago, and I'm still in the dog house because all of the music my wife paid for on itunes is now apparently broken... something to do with DRM, according to what I've been reading.  Anyway, I'm getting sick of being the bad guy here, and she says we can't afford to get her a windoze computer.  I'm not about to put Vista back on mine!  It unes through crossover won't run the store, and it crashes in my virtualbox.  Anyway, I looked up this whole Sharpmusique thing mentioned in the forums.  That's apparently no longer available.  I found something about itunes store for banshee, but the site simply has:     

iTunes Music Store (iTms) - Purchase music from the iTunes store. 

svn co svn://svn.banshee-project.org/trunk/banshee-itunes-plugin

and no download link.  It also says "You need to have Subversion installed to run the svn commands listed above".  Okay, I installed it.  I still can't do anything with this crap, and there's no "how-to" available. What do I do with this??  It's been six months, and I'm going to be forced to return to Bill if I can't get this fixed.

Thanks,
Clint

---

### Post by ShodanjoDM on 2008-05-26
It's one of some other unmaintained plugins, but you still can look here:

[http://code.google.com/p/banshee-unofficial-plugins/source/browse/trunk](http://code.google.com/p/banshee-unofficial-plugins/source/browse/trunk)

And this should get you the whole trunk, including the itunes plugin:

```

svn checkout http://banshee-unofficial-plugins.googlecode.com/svn/trunk/ banshee-unofficial-plugins-read-only
```

---

