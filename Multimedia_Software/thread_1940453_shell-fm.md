---
title: "shell-fm"
date: 2012-03-13
forum: Multimedia Software
---

### Post by ohnonot on 2012-03-13
hello,
who's using shell-fm out there? i'd like to get some talk going.
i love this app and would like to see it thrive & develop.
small bugs, hidden options...?

I'm recently getting this message```
DEBUG: Chunked!
```after every song, twice. any idea?

cheers. 
```
========================================================================
Track:    A Bright Burning Glow Dulls Slowly
Artist:    Funki Porcini
Album:    Plod
http://www.last.fm/music/Funki+Porcini
------------------------------------------------------------------------
Station: artist/Flanger/fans
+++++++
```

---

### Post by Bonster on 2012-03-13
yea same here, is probably changes made to the lastfm server itself

---

### Post by ohnonot on 2012-03-14
so sad. i tried to contact the maker but no success.
i f no-one continues working on this, changes on the website will make shell-fm less fun to use... or eventually even impossible.
the only other alternative (lastbash) is even older.

but hey, for now it works
:-)

btw, is it possible to display tags? and what does E - manually expand playlist - do? nothing afaik.

:popcorn:

---

### Post by ohnonot on 2012-03-18
...

---

### Post by TheBigBakedBean on 2012-05-09
Looks like a [patch has been made in the shell-fm source at github]("https://github.com/jkramer/shell-fm/pull/49").

If you have installed it from the universe repository (via apt-get), you'll want to remove it before installing the version from git:
```
sudo apt-get remove shell-fm
```

Here's how to get a fresh version from git:
```
sudo apt-get install git-core libmad0-dev libao-dev
sudo apt-get build-dep shell-fm
git clone git://github.com/jkramer/shell-fm.git
cd shell-fm
make
sudo make install
cd ..
sudo rm -R shell-fm/
```

---

### Post by Bonster on 2012-05-09
u can use

> sudo checkinstall

instead of *sudo make install*

if you want it to appear in apt and also is easy to remove later on with apt-get remove

---

### Post by ohnonot on 2012-05-11
great! thanks for telling me.
@thebigbakedbean: your instructions work nicely.
@bonster: sorry but neither checkinstall nor check install are recognized by my system.

SHELL-FM IS PERFECT AGAIN!!!

also check the man-page; i think there's 1 or 2 new options.

---

### Post by ohnonot on 2012-11-29
i made a new os install and installing shell-fm was one of the first things to do...
there's been some trouble with the website in the last days but now everything is fine again.
long live last.fm & shell-fm!

---

### Post by ohnonot on 2012-12-10
some issues with last.fm's change of api and/or policy.

a new shell-fm version is available from git, using the new api.

however, i could not get it to work with my free account.
although last.fm themselves are saying that it *is  *possible. at least outside the uk/us/germany.

other experiences?

---

