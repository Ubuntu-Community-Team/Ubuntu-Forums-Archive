---
title: "flashplugin-nonfree Buggy"
date: 2009-01-07
forum: Multimedia Software
---

### Post by Jesdisciple on 2009-01-07
The [Pandora]("http://www.pandora.com/") Flash movie was freezing in both Opera and Firefox after the first song had just started.  The movie would proceed to the next song, freeze the browser for a bit, and then crash as a white (Opera) or gray (Firefox) box.  I was only able to prevent the freeze by pausing the movie before the first song was skipped.

The problem was apparently in flashplugin-nonfree, because adobe-flashplugin from the Adobe website (and not available in the repos) fixed this problem in Firefox and Opera.

So I wonder why there is no adobe-flashplugin candidate in the repos?  Can it be legally included, and marked as a dependency of flashplugin-nonfree?  If it can't be included, should the broken package be replaced with a notice that the one on the Adobe website should be used instead?

---

### Post by Jesdisciple on 2009-01-12
Just to check, has this been noticed by anyone?

---

