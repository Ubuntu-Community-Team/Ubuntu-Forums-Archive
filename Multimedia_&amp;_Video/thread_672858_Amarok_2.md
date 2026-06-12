---
title: "Amarok 2"
date: 2008-01-20
forum: Multimedia &amp; Video
---

### Post by ryuuk86 on 2008-01-20
I compiled Amarok2 on kde4 form this howto

Building Amarok

NOTE: Amarok will only build correctly if your Strigi library was built with "clucene" support. Install clucene and clucene-dev, then rebuild Strigi (in kdesupport), then build Amarok.

Amarok can now be built without the multimedia directory.

1. sudo apt-get install libtag1-dev ruby1.8-dev libxine-dev
2. svn co svn://anonsvn.kde.org/home/kde/trunk/extragear/multimedia/amarok
3. cd amarok
4. mkdir amarok-build
5. cd amarok-build
6. cmake -DCMAKE_INSTALL_PREFIX=$KDEDIR -DCMAKE_BUILD_TYPE=debugfull ../../amarok && make VERBOSE=1 && make install

Note that your cmake preferences are saved in CMakeCache.txt, so you don't have to have the -D options every time you run cmake.

ccmake ../amarok will give you a nice ncurses interface

When I run amarok Its give me erorr :Amarok can't found your sound engine.Any ideas??

---

### Post by barsanuphe on 2008-01-20
i have the exact same problem. can't seem to fix it for now.

---

### Post by raevin on 2008-02-19
Not sure if the OP is the same one as who posted here: [http://amarok.kde.org/forum/index.php/topic,14988.0.html](http://amarok.kde.org/forum/index.php/topic,14988.0.html)

But, if you go there, the trick seems to be this:

[quote="barsanuphe"]
my KDEDIR was empty, so i changed it to KDEDIRS (in your #6) and then everything went fine.
[/quote]

I can't confirm this, but it's worth a shot. :)

---

