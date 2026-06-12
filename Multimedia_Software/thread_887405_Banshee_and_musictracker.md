---
title: "Banshee and musictracker"
date: 2008-08-12
forum: Multimedia Software
---

### Post by Sain on 2008-08-12
Hi!

I've installed Musictracker plugin for Pidgin, but it doesn't seem to work. It always sets the status to "Banshee is OFF". Well it's not.

I figured it might be the fact that i installed Banshee 1.2, which is banshee-1 package, rather than banshee package from the repos.

Is there a way to fix this?  To "make" banshee-1 ==> banshee or something :)

---

### Post by mikenelsen on 2008-08-13
+1

Got the same problem...

Maybe there is a config file for the plugin?

---

### Post by mikenelsen on 2008-08-13
Nevermind, there are no configs for it...

---

### Post by Sain on 2008-08-14
I've done some research... :) Seems that musictracker 0.4.1 is out of date, and doesn't support recent versions of Banshee regardless of configuration.

User Hyperair wrote a patch for Banshee to work, you can find DEB packages in this [THREAD]("http://ubuntuforums.org/showthread.php?t=724337&page=31")

However, there is also a "fork" of musictracker with working Banshee support, and some new minor features and bugfixes. I recommend that you use this version, as it's development has continued where original musictracker stopped (it is currently version 0.4.5)

You can find it in Hyperair's PPA [HERE]("https://edge.launchpad.net/~hyperair/+archive")

---

### Post by ikebowen on 2008-11-14
Having gotten the [disabled flag](http://ubuntuforums.org/showthread.php?p=6177442#post6177442) issue out of the way, I have yet to see this plugin successfully retrieve *any* data from Banshee. Works perfectly with Rhythmbox:

```
(10:51:34) core-musictracker: org.gnome.Rhythmbox
(10:51:34) core-musictracker: proxy
(10:51:34) core-musictracker: call
(10:51:34) core-musictracker: Rhythmbox,Assemblage 23,Storm,Ground (LP Version),2
(10:51:34) core-musictracker: Formatted status: Ground (LP Version) by Assemblage 23
(10:51:34) core-musictracker: Formatted status: Ground (LP Version) by Assemblage 23
(10:51:34) core-musictracker: Status set for all accounts
```

Just not Banshee.

```
(10:51:54) core-musictracker: org.gnome.Banshee
(10:51:54) core-musictracker: proxy
(10:51:54) core-musictracker: call
(10:51:54) core-musictracker: Banshee,,,,0
(10:51:54) core-musictracker: Formatted status: 
(10:51:54) core-musictracker: Status set for all accounts
```

I'm using banshee_1.2.1-3ubuntu2+hyper2_i386.deb in combination with pidgin-musictracker_0.4.1-1_i386.deb, both from the hyperair ppa. Any ideas?

---

### Post by ikebowen on 2008-11-14
Never mind, turned out it was more straightforward to build the release at [code.google.com/p/pidgin-musictracker](http://code.google.com/p/pidgin-musictracker/). This copy also includes last.fm support. ;)

---

