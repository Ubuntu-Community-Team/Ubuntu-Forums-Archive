---
title: "Miro closes on video playing"
date: 2009-05-11
forum: Multimedia Software
---

### Post by Jboxer on 2009-05-11
I have installed miro multiple times from ubuntu and miro repo, but the problem of crashing on the instance of playing a video I have previously downloaded.
```
$ miro
location: /usr/lib/xulrunner-1.9.0.10/libxpcom.so 
before 3
2009-05-11 22:52:17,759 INFO     Starting up Miro
2009-05-11 22:52:17,800 INFO     Version:    2.0.4
2009-05-11 22:52:17,806 INFO     OS:         Linux 2.6.28-11-generic i686
2009-05-11 22:52:17,808 INFO     Revision:   https://svn.participatoryculture.org/svn/dtv/tags/Miro-2.0.4/tv/resources - 9360
2009-05-11 22:52:17,811 INFO     Builder:    pbuilder@mercury
2009-05-11 22:52:17,812 INFO     Build Time: 1240933362.53
2009-05-11 22:52:17,812 INFO     Starting event loop thread
2009-05-11 22:52:17,877 INFO     Restoring database...
2009-05-11 22:52:17,878 INFO     Python version:    2.6.2 (release26-maint, Apr 19 2009, 01:56:41) 
[GCC 4.3.3]
2009-05-11 22:52:17,878 INFO     Gtk+ version:      (2, 16, 1)
2009-05-11 22:52:17,879 INFO     PyGObject version: (2, 16, 1)
2009-05-11 22:52:17,879 INFO     PyGtk version:     (2, 14, 1)
2009-05-11 22:52:17,880 INFO     Language:          [('LANG', 'en_US.UTF-8')]
2009-05-11 22:52:17,881 INFO     set_renderer: trying to add xinerenderer
2009-05-11 22:52:17,965 INFO     Xine version:      1.1.16.3
2009-05-11 22:52:19,517 INFO     Xine video driver: xv
2009-05-11 22:52:19,518 INFO     set_renderer: successfully loaded xinerenderer
2009-05-11 22:52:19,523 INFO     Connecting to /home/foo/.miro/sqlitedb
2009-05-11 22:52:19,976 TIMING   Database load slow: 0.453
2009-05-11 22:52:19,977 INFO     Database size on disk (in bytes): 887808
2009-05-11 22:52:19,977 INFO     Database object count: 132
2009-05-11 22:52:20,341 TIMING   idle (finish startup) too slow (2.527 secs)
2009-05-11 22:52:20,343 INFO     Checking movies directory '/home/foo/Videos/Miro/'...
/var/lib/python-support/python2.6/miro/eventloop.py:179: DeprecationWarning: socket.ssl() is deprecated.  Use ssl.wrap_socket() instead.
  result = func(*args, **kwargs)
2009-05-11 22:52:25,036 INFO     Starting auto downloader...
2009-05-11 22:52:25,049 TIMING   Icon clear: 0.000
2009-05-11 22:52:25,050 INFO     Starting movie data updates
2009-05-11 22:52:25,051 INFO     Checking for updates...
2009-05-11 22:52:25,433 INFO     No updates for this platform.
Segmentation fault

```

I have found a that the problem is a segfault error upon finding this I tried switching to gstreamer and back to xine, both did not work. I also have tried running a couple of older fixes and nothing has worked. help yo?

edit: I have also installed boxee and have had the same problem which leads me to believe that i am missing a dependency.

---

### Post by Jboxer on 2009-05-12
I went to the miro package page [http://packages.ubuntu.com/jaunty/miro]("http://packages.ubuntu.com/jaunty/miro") and installed all the required suggested and recommended packages with no such luck in fixing my problem.

---

### Post by Jboxer on 2009-05-13
I have found out that have a problem with .mpg files so I installed Mplayer in order to fix that. tried then failed again. I have install win32codecs and the ubuntu restricted extras... this must be an issue with the package manager so then I also added some archive support because I read an article on ubuntu geek on how to fix this.

TLDR: I'm stuck help me

---

### Post by Jboxer on 2009-05-13
I cant even play .avi or movie files any more I think I am just going to reinstall ubuntu.I prolly screwed myself over a while ago installing a corrupted package or some other bull

---

### Post by kilgore9 on 2009-05-15
Hey there.  I was having a similar problem with all of my video programs.  Trying to open a video file always crashed the system.  I fixed it by changing the video output module (or driver).  It is usually somewhere in the preferences.  For me it works as long as I change the driver to "X11".  If you don't have that one I would say just try each one until you find the one that works!

---

