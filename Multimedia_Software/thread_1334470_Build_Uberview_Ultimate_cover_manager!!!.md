---
title: "Build Uberview: Ultimate cover manager!!!"
date: 2009-11-22
forum: Multimedia Software
---

### Post by Marco7 on 2009-11-22
Yes it's true I was once a member of the infamous Ubernet.org where once affiliated you could download anything you wanted.  Alas, years ago, I was booted form the training facility for being a typo monkey, but on my own, in darkness, I did learn to adhere to the [Uber-standard]("http://www.uberstandard.org/").  A wonderful tool another member just threw together was THE BEST COVER MANAGER EVER, and it was called [Uberview]("http://www.uberview.org/").

To my extreme delight, as I have been trying to find a substitute that might work under Ubuntu Linux I ran across this build at [Archlinux,]("http://aur.archlinux.org/packages.php?ID=22508") and it looks like they fixed it, i.e. it wasn't working, i.e. like so many other programs, it wasn't downloading covers from amazon either, even in windows 

I am, however, only just learning to to compile stuff and I can't quite get it.

Code:  

In file included from src/lastfm.h:29,
                 from src/lastfm.cpp:25:
src/mainwindow.h:34:26: error: QFutureWatcher: No such file or directory
In file included from src/mainwindow.h:35,
                 from src/lastfm.h:29,
                 from src/lastfm.cpp:25:
build/ui_mainwindow.h: In member function ‘void Ui_MainWindowDLG::setupUi(QMainWindow*)’:
build/ui_mainwindow.h:171: error: ‘class QAction’ has no member named ‘setIconVisibleInMenu’
build/ui_mainwindow.h:218: error: ‘class QTreeWidget’ has no member named ‘setHeaderHidden’
In file included from src/lastfm.h:29,
                 from src/lastfm.cpp:25:
src/mainwindow.h: At global scope:
src/mainwindow.h:153: error: expected ‘;’ before ‘<’ token
src/lastfm.cpp: In member function ‘void LastFm::httpRequestFinished(int, bool)’:
src/lastfm.cpp:56: error: ‘class QUrl’ has no member named ‘encodedPath’
make: *** [build/lastfm.o] Error 1


Can anyone look at these files and help me please???

[http://www.uberview.org/software/uberview-1.17.tar.gz]("http://www.uberview.org/software/uberview-1.17.tar.gz")

---

