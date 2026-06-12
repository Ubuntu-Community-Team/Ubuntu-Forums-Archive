---
title: "[banshee] wma support"
date: 2009-01-04
forum: Multimedia Software
---

### Post by FAJALOU on 2009-01-04
First off: This is not a scenario of "I can't play wma's."  The wmas are playing, just badly.
Second:  When I use amarok, all of the wma's play fine (ie no crackling)

So the real issue is the album that I have that is downloaded as WMA's and the songs will crackle.  This primarily happens when I switch viewports (using metacity right now), but this doesn't even really matter because it will do it randomly and sporadically also.  The most peculiar part of this is that Amarok runs these wma files perfectly.  Now I know that they are different engines... but it would be nice to know *why* these files are running so badly in banshee.  I have installed many of the gstreamer codecs along with w32codecs.  Any *any* **any** suggestions are welcome.

---

### Post by kyle2595 on 2009-05-31
How did you get the .wma files to play?

---

### Post by FAJALOU on 2009-05-31
```
sudo aptitude reinstall banshee
```
Try the above (which will reinstall banshee), or try purging banshee all-together (sudo aptitude purge banshee  && sudo apt-get install banshee), and reinstall, that fixed my problems.  Good luck!

---

