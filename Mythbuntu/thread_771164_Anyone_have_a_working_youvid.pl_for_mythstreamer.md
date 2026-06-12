---
title: "Anyone have a working youvid.pl for mythstreamer?"
date: 2008-04-27
forum: Mythbuntu
---

### Post by grytpype on 2008-04-27
Hi folks,

I'm trying to watch YouTube vids on my Mythbox using mythstreamer, but it looks like the "handler" script -- youvid.pl -- that comes with version 0.18.1-0ubuntu6 is broken.

Before I dive into trying to fix it, does anyone have a version that works???

---

### Post by sgunther on 2008-04-28
I posted a bug;

[https://bugs.launchpad.net/mythbuntu/+bug/223781](https://bugs.launchpad.net/mythbuntu/+bug/223781)

It is a relatively easy fix.

---

### Post by grytpype on 2008-04-28
Thanks for that patch!

Here's a tip on how to link your YouTube playlists into mythstreamer:

YouTube has native support for RSS feeds for videos having a particular tag:

[http://www.youtube.com/rss/tag/YOURTAGHERE.rss](http://www.youtube.com/rss/tag/YOURTAGHERE.rss)

or videos posted by a particular user:

[http://www.youtube.com/rss/user/USERNAME/videos.rss](http://www.youtube.com/rss/user/USERNAME/videos.rss)

which can be parsed and displayed by mythstream.

Although YouTube does not seem to have native support for an RSS feed based on a user's favorites list, someone has apparently used the YouTube API to fill in that gap:

[http://www.referd.info/favorites/YOURUSERNAME/rss.php](http://www.referd.info/favorites/YOURUSERNAME/rss.php)

will give you a feed of your YouTube favorites.


You can also get a feed of a YouTube playlist as follows:

[http://www.referd.info/playlist/PLAYLISTNUMBER/rss.php](http://www.referd.info/playlist/PLAYLISTNUMBER/rss.php)

---

