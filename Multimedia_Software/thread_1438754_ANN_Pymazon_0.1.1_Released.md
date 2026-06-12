---
title: "ANN: Pymazon 0.1.1 Released"
date: 2010-03-25
forum: Multimedia Software
---

### Post by sccolbert on 2010-03-25
I'm happy to announce the release of Pymazon 0.1.1! 

This release brings a big enhancement in the form of PyGtk support in addition to the PyQt4 and Command line interfaces already available. 
A special thanks to Ray Meyers for his gtk commits!

Pymazon Changelog

0.1.1
-----
- Added support for command line options and configuration file
- Added support for save name templates
- Added a threaded downloader which runs a user-specified simultaneous threads when in gui mode
- Added a PyGtk Gui (Submitted by Raymond Myers)
- Rewrote the QT Gui with Qt Designer and pyuic4 - this simplified and cleaned up a bunch of stuff
- Added graphical progress bars to the Gui's
- Removed a check that asserted the downloaded file size was the same as specified in the amz file
  as Amazon was misreporting file size and it was causing Pymazon to erroneously fail
- Cleaned up code all over the place: logging, settings, etc...


Pymazon is available in the cheeseshop and google code. 

Pymazon is a Python implemented downloader for the amazon mp3 store. 

You can read more about Pymazon at [http://code.google.com/p/pymazon/](http://code.google.com/p/pymazon/).

I always appreciate comments and bug reports.

Cheers!

Chris

---

