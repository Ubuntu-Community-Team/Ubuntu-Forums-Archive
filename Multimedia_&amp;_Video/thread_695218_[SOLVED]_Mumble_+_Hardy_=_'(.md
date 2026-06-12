---
title: "[SOLVED] Mumble + Hardy = :'("
date: 2008-02-12
forum: Multimedia &amp; Video
---

### Post by FrozenFox on 2008-02-12
I've looked through several threads, but I can't get anything to work. ><

Mumble is refusing to run from the .debs I've tried, probably because they were intended for feisty and just happen to work on gutsy. 

"Mumble failed to install a database in any of the possible locations" is what it tells me when trying to load it, and in the console it gives a nag about QSQLITE driver not loaded. I've tried installing libqt4-sql but no go. I noticed on some non-english websites I found while looking for the answer on google suggest installing both that and libqt4-sql-sqlite i think it was. However, that's not in the repos, and none of the rpm's i've converted to debs via alien helped (no surprise, but i was desperate! hehe). I tried compiling it (which im pretty decently versed in fixing dependency issues of compiling), but I couldn't get that to go either. If necessary, I'll re-download and give the error messages, but odds are they're related to that library. My machine is kinda-sorta LAMP, and I have most of the apache, php-mysql, php5, blah blah stuff installed and working as it is, but no go. libqt4-core, libqt4-gui, and libqt4-sdl are all installed, no go.

Suggestions? This is not a dire issue, as I am currently running and using TS and have been for some time with my friends. I'd just prefer to switch over to mumble if possible.

---

### Post by FrozenFox on 2008-02-13
Wow, I didn't realize the post got so far back in such a short time! hehe. Bump?

---

### Post by FrozenFox on 2008-02-13
Argh.

I finally got the silly thing to compile via sudo apt-get remove qt3-dev-tools and then sudo apt-get install qt4-dev-tools. However, when I sudo make install, it doesn't install anything. Making a deb out of it with checkinstall shows only documentation in installed files, which dont appear in my system after the sudo make install either. I'm so confused. Any help? Or maybe suggestions on how to make use of this page?:

[https://launchpad.net/ubuntu/hardy/+source/mumble/1.1.2-0ubuntu1](https://launchpad.net/ubuntu/hardy/+source/mumble/1.1.2-0ubuntu1)

Edit: ugh. i installed the patch file and recompiled and installed but there's still nothing installed anywhere and making a deb out of it still produces nothing but the documentation. I'm starting to get a little frustrated. Help?

---

### Post by FrozenFox on 2008-02-14
Solved. I have no idea how, but it's solved. Any one or most of the following steps may be completely unnecessary, and it'd be great if someone reports back with how they got it working and cut out some of the work. But this is how it started working for me.

1) Note: remove qt3-dev-tools and install qt4-dev-tools. Download the "original source" and the .gz diff patch deal from the page listed in the post above. Unzip the source, move the .gz diff into the folder with all of the files (like main.pro). Then in console/terminal, cd to that directory, then gunzip -c mumble_1.1.2-0ubuntu1.diff.gz | patch -p1. Then qmake main.pro, then make, then sudo make install.

2) Run and refresh the update manager for (k)ubuntu and install everything there. 

3) Download and install the older version 1.1 of mumble via the deb here [https://edge.launchpad.net/~slicer/+archive](https://edge.launchpad.net/~slicer/+archive) .  Run it and make sure it works. Then update to the newer version 1.2 from [http://sourceforge.net/project/showfiles.php?group_id=147372&package_id=162594](http://sourceforge.net/project/showfiles.php?group_id=147372&package_id=162594) via .deb.

To reiterate, I have no idea what got it to work, since step 1 didn't do anything by itself and installing the 1.2 deb didnt work by itself, but 1.2 is now working on my hardy machine. If someone from a clean machine would tell us what made it work for them and remove some of the above nonsense steps, that'd be great. My guess is the ubuntu devs fixed the qt4-sql stuff in one of the updates, and then installing the 1.2 deb worked from there on, but in case that's not it, i've included all I did, in order, above.

---

### Post by soxs on 2008-02-20
This is not solved. I have the exact same porblem. Did you file a bugreport in that was somwhat *processed*?

---

### Post by erielf on 2008-07-11
Version 1.1.3 works under gutsy and can be obtained here:
[http://www.getdeb.net/](http://www.getdeb.net/)

---

