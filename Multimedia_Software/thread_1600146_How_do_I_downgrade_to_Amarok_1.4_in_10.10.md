---
title: "How do I downgrade to Amarok 1.4 in 10.10"
date: 2010-10-18
forum: Multimedia Software
---

### Post by supermandudekid on 2010-10-18
First post.

I searched for this everywhere but only found ways in older versions.  I just wiped windows and installed 10.10 and would like to use the old amarok 1.4. Will I have to compile it? Or can I downgrade my current version.

If this has been posted or another thread has a tutorial could someone point me in the right direction? 

I've tried to use some forks but they just aren't the same..

Any help would be appreciated.

Thanks

---

### Post by mc4man on 2010-10-18
> Will I have to compile it? Or can I...
You may find a ppa for amakok14, maybe not.
I'd say better to build - here's the latest lucid how-to w/ patches, should build nicely in maverick
(have it here
In the build deps it's libmysqlclient-dev but apt-get should adjust for you if you copy as is.

[http://ubuntuforums.org/showthread.php?t=1559002](http://ubuntuforums.org/showthread.php?t=1559002)

I use checkinstall rather than make install, if you do so then add --fstrans=no to command (or adjust checkinstallrc

---

### Post by ubfu on 2010-10-20
Sorry to interfere , having the same problem compiling giving some error about ruby programming language which I am not sure which lib to install.

[http://pastebin.com/TjgDkmhR](http://pastebin.com/TjgDkmhR)

Thanks hope for solution :)

---

