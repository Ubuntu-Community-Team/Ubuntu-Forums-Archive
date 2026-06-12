---
title: "Upgraded to Hardy mythweb thumbnails only for new recordings"
date: 2008-08-29
forum: Mythbuntu
---

### Post by scottishnarn on 2008-08-29
I've just upgraded my mythtv system from Edgy to Hardy (finally). It all works fine except in mythweb where it only displays thumbnails for new recordings, not for ones that I imported from the old system (using instructions from mythtv website documentation found [here]("http://www.mythtv.org/docs/mythtv-HOWTO-23.html#ss23.7")).

The png files are there. I deleted them and they were recreated when I loaded mythweb. I deleted them from /var/www/mythweb/data/cache and they were recopied. But they still don't show up. Only the shows recorded since I upgraded have an icon.

I have tried the fix of editing the recorded.php file found in [this thread]("http://ubuntuforums.org/showthread.php?t=731007") but that doesn't work either. 

The png files in /var/www/mythweb/data/cache are of 0 size. By listing the png files for each recording (there are 3  mpg.100x0x64.png, mpg.100x120x64.png, mpg.x0x64.png) and copying the png file from my recordings directory over these 3 files I can get the thumbnails to appear. However, since this applies to 165 recordings this is an impractical solution.  

Any ideas?

Thanks
David

---

