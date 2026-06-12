---
title: "unable to play mp3 sounds"
date: 2008-07-08
forum: Multimedia Software
---

### Post by emigrant on 2008-07-08
hai there how to enable mp3 sound playing in ubuntu 7.10

---

### Post by Afkpuz on 2008-07-08
you need the codec.

Goto Applications>Add/Remove and click the drop down box in the top right and select "all available applications"

Then, search for "gstreamer"

Install every package with gstreamer in it's name and also install ubuntu restricted extras.  That will actually install nearly every codec you'll ever need.  If you just want the mp3 codec, its in the "gstreamer-extra plugins" package

---

### Post by emigrant on 2008-07-09
i think without internet i cant install the additional features. since i installed ubuntu from live cd. 
is there a way to donload the codecs in windows and install them in ubuntu?

---

### Post by Afkpuz on 2008-07-15
Go here and pick a convenient mirror.  At the bottom of the page, choose your cpu architecture, then pick a mirror close to you.
[http://packages.ubuntu.com/gutsy/ubuntu-restricted-extras](http://packages.ubuntu.com/gutsy/ubuntu-restricted-extras)


Use a jump drive, or cd, or something to get the file into ubuntu.


Then in ubuntu, copy the file onto the hard drive and just double click it.  An installer will start and install the package.  It's not all the codecs you'll need, but it'll get you mp3 support.

---

