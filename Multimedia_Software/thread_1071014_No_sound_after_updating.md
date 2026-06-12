---
title: "No sound after updating"
date: 2009-02-15
forum: Multimedia Software
---

### Post by CalvinMcGee on 2009-02-15
I've lost the sound since I used update-manager. I have no clue what happened. But when I tried running Amarok I just got error that Xine wasn't loaded or something, which have happened before but it usually solves itself after logging out. I rebooted, and when I tried to play music, it looks like it's playing but no sound comes out and no error messages. These are the packages that were updated:

dpkg (1.14.20ubuntu6) to 1.14.20ubuntu6.1
dpkg-dev (1.14.20ubuntu6) to 1.14.20ubuntu6.1
gvfs (1.0.2-0ubuntu1) to 1.0.2-0ubuntu2
gvfs-backends (1.0.2-0ubuntu1) to 1.0.2-0ubuntu2
gvfs-bin (1.0.2-0ubuntu1) to 1.0.2-0ubuntu2
gvfs-fuse (1.0.2-0ubuntu1) to 1.0.2-0ubuntu2
libgvfscommon0 (1.0.2-0ubuntu1) to 1.0.2-0ubuntu2
rhythmbox (0.11.6svn20081008-0ubuntu4.2) to 0.11.6svn20081008-0ubuntu4.3

While playing around with soundconf i get following messages sometimes:
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Couldn't open sound unit for playback.

Any clues?

---

