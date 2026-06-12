---
title: "Nautilus is slow and crashes a lot"
date: 2010-08-20
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by kyleabaker on 2010-08-20
Has Nautilus been crashing a lot lately for anyone else? It seems very slow to open a browser and seems to be leaking memory somewhere.

Apport tries to catch the error, but I apparently don't have enough memory to collect it.

Any tips? Its making everything pretty much unusable.

---

### Post by ranch hand on 2010-08-20
I have totally failed to have any of the problems that people have had with Nautilus in the last 3 releases counting 10.10.

Sorry.

---

### Post by woodbj on 2010-08-21
Mine (latest updates) is heaps slow and takes forever to open up folders

---

### Post by ronacc on 2010-08-21
not seeing that here on either of my maverick installs , one upgraded from lucid and with many PPA's and the other fresh from A3 and no add on's .

---

### Post by kyleabaker on 2010-08-21
> **woodbj said:**
> Mine (latest updates) is heaps slow and takes forever to open up folders

That sounds like the exact same problem I'm seeing, though mine eventually crash and restart nautilus.

---

### Post by holiday on 2010-08-21
I find nautilus bloated and spits out too many warnings. I've switched to thunar.

$ sudo apt-get install thunar

It's a lighter weight file browser.

---

### Post by kyleabaker on 2010-08-21
I've recorded System Monitor while opening Nautilus browser windows several times to show how the memory usage goes crazy. You'll have to fullscreen it to see details.

Notice that each time I press Ctrl+N to open a new window, the memory usage goes up by ~30-60mb. It eventually crashes and respawns toward the end. Very annoying.

[http://vimeo.com/14327149](http://vimeo.com/14327149)

---

### Post by ktp on 2010-08-21
wow is there bug for this...that seems like massive memory leaks.

---

### Post by srirammurali on 2010-08-21
One more here. Apparently removing appmenu-gtk does bring down the memory consumption as suggested here ([http://www.webupd8.org/2010/07/nautilus-memory-leak-fix-ubuntu-1004.html](http://www.webupd8.org/2010/07/nautilus-memory-leak-fix-ubuntu-1004.html))

My nautilus memory consumption is now down at 10-15M range after removing appmenu-gtk.

I removed docky too, so the culprit might be docky too. :)

---

### Post by kyleabaker on 2010-08-22
> **srirammurali said:**
> One more here. Apparently removing appmenu-gtk does bring down the memory consumption as suggested here ([http://www.webupd8.org/2010/07/nautilus-memory-leak-fix-ubuntu-1004.html](http://www.webupd8.org/2010/07/nautilus-memory-leak-fix-ubuntu-1004.html))

My nautilus memory consumption is now down at 10-15M range after removing appmenu-gtk.

I removed docky too, so the culprit might be docky too. :)

Thanks. That was the problem... I had installed appmenu to test it out and apparently only uninstalled the indicator components. Now the performance is right back to dandy. =D>

I don't recommend anyone install appmenu-gtk for any reason.

---

### Post by NightwishFan on 2010-08-22
I can confirm the memory leak as well using Unity on Lucid.

---

### Post by ktp on 2010-08-22
> **kyleabaker said:**
> Thanks. That was the problem... I had installed appmenu to test it out and apparently only uninstalled the indicator components. Now the performance is right back to dandy. =D>

I don't recommend anyone install appmenu-gtk for any reason.

can you write a bug if you haven't already and post a link here?

---

### Post by kyleabaker on 2010-08-22
> **ktp said:**
> can you write a bug if you haven't already and post a link here?

[https://bugs.launchpad.net/appmenu-gtk/+bug/609524](https://bugs.launchpad.net/appmenu-gtk/+bug/609524)

---

### Post by ktp on 2010-08-22
> **kyleabaker said:**
> [https://bugs.launchpad.net/appmenu-gtk/+bug/609524](https://bugs.launchpad.net/appmenu-gtk/+bug/609524)

thanks

---

### Post by sgage on 2010-08-22
As an experiment, I installed appmenu*, and wow! Nautilus memory usage just ballooned! I removed it all, and it's back to normal. For anyone dealing with this, you have to log out and back in for the change to take effect, so if you've removed appmenu* and don't see an improvement, make sure to re-log.

---

### Post by kyleabaker on 2010-08-22
> **sgage said:**
> As an experiment, I installed appmenu*, and wow! Nautilus memory usage just ballooned! I removed it all, and it's back to normal. For anyone dealing with this, you have to log out and back in for the change to take effect, so if you've removed appmenu* and don't see an improvement, make sure to re-log.

No need to logout. Just uninstall and run:
```
killall nautilus
```

---

### Post by sgage on 2010-08-22
> **kyleabaker said:**
> No need to logout. Just uninstall and run:
```
killall nautilus
```

That's a bit more convenient I'd say! Thanks for the tip...

---

### Post by VMC on 2010-09-13
This is an old topic, but nonetheless I compared Maverick nautilus with Lucid on either moving/copying files from one partition to another. Mavericks nautilus is at least twice as slow. Searched Launchpad for any reference bugs. 

Besides the memory leak that has been reported, anyone else experience or know why the slowdown?

---

### Post by cariboo on 2010-09-13
I would suggest that the slow down, is because Unity is still in heavy development, just like gnome-shell is slower that gnome-desktop, it may have something to do with mutter.

---

