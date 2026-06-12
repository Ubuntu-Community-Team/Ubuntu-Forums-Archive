---
title: "Banshee"
date: 2010-02-28
forum: Multimedia Software
---

### Post by Jordii on 2010-02-28
My iPod Nano 4th gen doesn't appear in Banshee. I tried to fix it with this [https://launchpad.net/~banshee-team/+archive/ppa]("https://launchpad.net/%7Ebanshee-team/+archive/ppa"), because that fixed it for many people. I just added the 2 lines
deb [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) karmic main 
deb-src [http://ppa.launchpad.net/banshee-team/ppa/ubuntu](http://ppa.launchpad.net/banshee-team/ppa/ubuntu) karmic main

[FONT=Verdana]to my software sources and reinstalled banshee using the command apt-get install banshee,
but that didn't solve it. I still can't use my iPod in Banshee. Did I do anything wrong at the
website I mentioned before?
[/FONT]

---

### Post by boombox1387 on 2010-03-20
I'm not positive on this one, but the version of Banshee in the PPA might go by the package name 'banshee-1' instead of 'banshee'.  To check which version of Banshee you have, run:

```
banshee --version
```

and

```
banshee-1 --version
```

You probably only have the first one installed.  If you have both installed, you'll want to make sure that all of your Banshee launchers are running banshee-1 instead of banshee.

If you only have 'banshee' installed (not banshee-1), then knowing which version is pretty important.  The version that comes with Ubuntu is 1.5.1.  The version in the PPA is 1.5.5, but it should be switching to 1.5.6 shortly.  If your version of Banshee is 1.5.5 or newer, but you still can't get your iPod to work, try running:

```
podsleuth --rescan
```

This will run Banshee's iPod detection tool.  If it finds an iPod, try running Banshee, and maybe it'll work.  If it doesn't find an iPod, let me know, and we'll see what we can do. Good luck!

---

