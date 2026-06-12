---
title: "Trouble installing DEB. Files. Ubuntu 10.10"
date: 2010-09-02
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by tjeremiah on 2010-09-02
I literally just updated to BETA and everything is running smooth. One minor annoyance is the fact that deb files wont install. At first, when clicked on a deb file, it would direct me to the Ubuntu Software store. Thats when I figured I might not have the program that installs debs. 

So within the store, I downloaded GDebi and was able to now run the deb file. But the problem is, no matter the deb file, I receive an error , a fail that reads 
```
dpkg: unable to read filedesciptor flags for <package status and progress file decriptor>: Bad file descriptor
```

How do I solve this issue so that I can install debs once again?

---

### Post by kansasnoob on 2010-09-02
I've seen that too, I suspect that's why gdebi is removed by default. So I just use:

```
sud dpkg -i <packagename>
```

Example, if the .deb is in my Home folder:

```
sudo dpkg -i w32codecs_20071007-0medibuntu2.1_i386.deb
```

If it were in my Downloads folder I'd first "cd Downloads" so it's looking in the right location.

---

### Post by ktp on 2010-09-02
> **tjeremiah said:**
> ISo within the store, I downloaded GDebi and was able to now run the deb file. But the problem is, no matter the deb file, I receive an error , a fail that reads 
```
dpkg: unable to read filedesciptor flags for <package status and progress file decriptor>: Bad file descriptor
```

How do I solve this issue so that I can install debs once again?

This has been reported few times...here is one thread..can search for others:

[http://ubuntuforums.org/showthread.php?t=1563534](http://ubuntuforums.org/showthread.php?t=1563534)

---

### Post by tjeremiah on 2010-09-02
> **ktp said:**
> This has been reported few times...here is one thread..can search for others:

[http://ubuntuforums.org/showthread.php?t=1563534](http://ubuntuforums.org/showthread.php?t=1563534)

crap, I hate when this happens. When I search I didnt see that result but thanks guys.

---

### Post by kyleabaker on 2010-09-02
Can we get one of these threads stickied? This is starting to crop up too much lately and no one seems to like searching. That makes at least 2 threads for this in less than 24 hours..
[http://ubuntuforums.org/showthread.php?t=1566059](http://ubuntuforums.org/showthread.php?t=1566059)

---

### Post by ktp on 2010-09-02
> **tjeremiah said:**
> crap, I hate when this happens. When I search I didnt see that result but thanks guys.

no biggie...at least you tried to search.

Make sure to click the "this bug affects me too" link in the bug at the end of thread I posted.

---

### Post by West201 on 2010-09-05
> **kansasnoob said:**
> I've seen that too, I suspect that's why gdebi is removed by default. So I just use:

```
sud dpkg -i <packagename>
```

Example, if the .deb is in my Home folder:

```
sudo dpkg -i w32codecs_20071007-0medibuntu2.1_i386.deb
```

If it were in my Downloads folder I'd first "cd Downloads" so it's looking in the right location.

Thanks for posting that. I'm new to ubuntu and i've been having that problem for days and I've googled that problem like crazy. Thanks for making this easy

---

### Post by jpeddicord on 2010-09-05
> **tjeremiah said:**
> I literally just updated to BETA and everything is running smooth. One minor annoyance is the fact that deb files wont install. At first, when clicked on a deb file, it would direct me to the Ubuntu Software store. Thats when I figured I might not have the program that installs debs.

That's because the software center is able to install .deb packages directly, much like GDebi. When you open it, you'll see a software page like others in the repository, but it installs the package you already downloaded instead.

---

### Post by mc4man on 2010-09-06
> That's because the software center is able to install .deb packages directly

Can also be used directly in browser as shown, 'gdebi-gtk', while it will probably be fixed, is somewhat unneeded.
(though a weakness in sc is it  doesn't appear atm to allow or do re-installs

Edit: sc now allows re-installs here, plus is also the default for dl'ed .debs.
gdebi-gtk has also been fixed if one wants to use

---

