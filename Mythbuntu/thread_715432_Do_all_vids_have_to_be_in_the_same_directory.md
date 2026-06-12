---
title: "Do all vids have to be in the same directory?"
date: 2008-03-04
forum: Mythbuntu
---

### Post by MythMattS on 2008-03-04
Hi there,

I have a lot of movies I've ripped from my own DVDs, some music videos previously recorded from TV, as well as a bunch of funny videos.  All in all more than 1,000 files.  They are currently nicely organized in their own directories on an external drive.  This makes me happy.

When I add a new location I can view the files in that directory, but nothing else.  When I add a different one via the config it complains about having lost all of the other stuff.

Question - do I really have to jam everything together in to one location?  That would make me sad.  <sob>

- Cheers, MythMatt

---

### Post by newlinux on 2008-03-04
You can do this two ways:

1. Use symlinks to put all videos under one parent directory (mythvideo can scan the parent directory and all of it's child folders)
2. You can have multiple directories (separated by a colon) as your mythvideo directory

---

### Post by MythMattS on 2008-03-05
Excellent answer, thank you so much!

---

