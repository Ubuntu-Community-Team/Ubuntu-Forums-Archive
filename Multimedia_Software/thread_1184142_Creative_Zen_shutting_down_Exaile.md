---
title: "Creative Zen shutting down Exaile?"
date: 2009-06-10
forum: Multimedia Software
---

### Post by Seamyst on 2009-06-10
After being completely disappointed with Amarok 2, I decided to switch to Exaile to handle my music library and my Creative Zen.  I installed it and the two packages needed for its mtp plugin (libmtp and pymtp), and activated said plugin.  I plugged in my Zen and asked Exaile to connect to it.  No go - it said to wait a few minutes or unplug it, then try again.

I discovered in a thread that ejecting the Zen in Nautilus will make it work if you have this problem, so I quit Exaile, ejected, and then opened Exaile again and tried to connect.

This time it said it was connecting for a few seconds, then suddenly Exaile quit completely.  I've tried this multiple times (including after rebooting), and while Exaile will play my music library, it won't connect to my Zen.

Any ideas how to fix this?  Barring that, what music player (that supports the Zen and other mtp devices) would you recommend, aside from Amarok?

I'm running Ubuntu Jaunty on a MacBook Core Duo, if that makes any difference.

---

### Post by kneewax on 2009-11-25
Did you ever get anywhere with this.  I like you lost MTP support after I ditched the dreadful Amarok 2.  Really would like to get the Zen working in Linux agaain though!

---

### Post by freddybob on 2009-11-26
Banshee* supports MTP devices. Latest version from this PPA: [http://banshee-project.org/download/#ubuntu](http://banshee-project.org/download/#ubuntu)

Amarok 1.4 can still be installed from this PPA: [https://launchpad.net/~bogdanb/+archive/amarok14](https://launchpad.net/~bogdanb/+archive/amarok14)

Rhythmbox probably also works, I've not tried it, see this forum post: [http://ubuntuforums.org/showpost.php?p=8201384&postcount=2](http://ubuntuforums.org/showpost.php?p=8201384&postcount=2)


** Note: Banshee does not fully support dragging and dropping of local playlists to your device. Music and video can easily be dragged to the player but not playlists.*

---

### Post by Seamyst on 2009-11-26
I eventually installed Gnomad and that worked very well in Jaunty.  I just upgraded to Karmic and haven't tried to transfer music yet, but it should still work the same.

---

