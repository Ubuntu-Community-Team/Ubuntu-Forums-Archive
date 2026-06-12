---
title: "iTunes to Banshee"
date: 2011-06-18
forum: Multimedia Software
---

### Post by AmrH on 2011-06-18
I'm moving from Windows 7 to Ubuntu. I have an iTunes DB that has all my music along with my playlists, ratings, play counts, etc... Now I need to move all that to Banshee on Ubuntu. Is this possible? I don't really care much about the ratings and play counts. All I need is to have my playlists!

---

### Post by tgalati4 on 2011-06-18
There is probably a more elegant way to do this, but here it goes:

I would put the Windows version of floola on your desktop in Windows. ([http://floola.com](http://floola.com))

Point floola towards your iTunes DB location.  It will take a while to index and show up.  Scroll through floola to make sure you can see your playlists.

Now boot into Ubuntu and put the linux version of floola on your linux desktop.  Point floola towards the new index DB that floola created under Windows.  Click on the Windows partition in Nautilus to make sure the Windows disk gets mounted in /media.

If the linux floola can read the Windows-floola-created DB, then a new floola DB should be created within your linux partition.

Bring up Banshee and activate the iPod plugin and point the import toward the new floola DB.  Banshee should now be able to read it.

It's possible that Banshee can directly read the iTunes database on the Windows partition, but floola makes a nice intermediate step because it cross-checks and repairs the database as well.  Plus, you can now put floola on your iPod and use it control your music as well as Banshee.

When you find a more elegant way of doing this, please post it.

---

### Post by AmrH on 2011-06-19
> **tgalati4 said:**
> There is probably a more elegant way to do this, but here it goes:

I would put the Windows version of floola on your desktop in Windows. ([http://floola.com](http://floola.com))

Point floola towards your iTunes DB location.  It will take a while to index and show up.  Scroll through floola to make sure you can see your playlists.

Now boot into Ubuntu and put the linux version of floola on your linux desktop.  Point floola towards the new index DB that floola created under Windows.  Click on the Windows partition in Nautilus to make sure the Windows disk gets mounted in /media.

If the linux floola can read the Windows-floola-created DB, then a new floola DB should be created within your linux partition.

Bring up Banshee and activate the iPod plugin and point the import toward the new floola DB.  Banshee should now be able to read it.

It's possible that Banshee can directly read the iTunes database on the Windows partition, but floola makes a nice intermediate step because it cross-checks and repairs the database as well.  Plus, you can now put floola on your iPod and use it control your music as well as Banshee.

When you find a more elegant way of doing this, please post it.

This is brilliant. Thanks a lot :D. But is there a way to reverse this process to go from Banshee on Linux to iTunes?

---

### Post by AmrH on 2011-06-19
> **homefactor said:**
> Is Banshee really nice? What is its edge over iTunes?

iTunes is much better of course; however, I'm moving to Ubuntu so I need to move from iTunes to Banshee.

---

