---
title: "mplayer repository?"
date: 2006-11-07
forum: Multimedia &amp; Video
---

### Post by NutMonkey on 2006-11-07
I did a fresh installation of Kubuntu Edgy.  I uncommented the universe and multiverse repositories in the sources.list and did an apt-get update.  I then tried to install mplayer but it says:

Package mplayer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mplayer has no installation candidate

What repository can I find mplayer in?  I know automatix will install it but I'm running Kubuntu and I don't want to have to install all of it's gnome dependencies.  Same question for the w32codecs?

---

### Post by kerry_s on 2006-11-07
Make sure you have this line-> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse

I use this for the codec--> deb [http://www.debian-multimedia.org/](http://www.debian-multimedia.org/) etch main

---

### Post by NutMonkey on 2006-11-07
Thanks, now that I doublecheck the only entry in sources for multiverse was for edgy-backports.  I appended multiverse to the universe entry and mplayer installs ok.  The w32codecs repository also worked, but is there an ubuntu one?

---

