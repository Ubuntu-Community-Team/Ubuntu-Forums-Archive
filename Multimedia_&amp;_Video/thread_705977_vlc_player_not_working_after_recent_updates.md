---
title: "vlc player not working after recent updates"
date: 2008-02-23
forum: Multimedia &amp; Video
---

### Post by mitsugiri on 2008-02-23
I recently updated some libraries as the Synaptic update manager had suggested and I think it may have created some problems.

My VLC player, Amarok and the System monitor have stopped working.

VLC player and Amarok player do not start at all when I select them from the Applications menu.  When I try to run them from the terminal I get the following messages

VLC:
--------------------
VLC media player 0.8.6c Janus
[00000293] skins2 interface error: no suitable dialogs provider found (hint: compile the wxWidgets plugin, and make sure it is loaded properly)
[00000293] skins2 interface: skin: VLC 0.8.5 Default Skin  author: aLtgLasS

---------------------------------

How can I compile the wxWidgets plugin and make sure it's loaded properly?

Amarok gives the following error:

---------------------------------

amarokapp: error while loading shared libraries: libpcreposix.so.3: cannot open shared object fil

---------------------------------

This might have been one of the library files that got upgraded.

The System monitor is running on the panel  but when I click it to view the statistics, it tries to open up but nothing happens.

Has anybody else experienced this?
I'm a quite new to linux.  Please help.

---

### Post by Bubba64 on 2008-02-24
In synaptic click on custom filters then broken packages and look to see if anything is broken, this is a simple start.

---

### Post by mitsugiri on 2008-02-24
No broken packages on Synaptic package manager

---

### Post by Bubba64 on 2008-02-25
Not knowing what you have installed or not installed or if you have the appropriate repositories access and codecs this link is one of many that gives a lot of info on what should make everything work.
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

---

### Post by mitsugiri on 2008-02-26
Thanks Bubba,
I'll check the link and see if it will help my case.

---

