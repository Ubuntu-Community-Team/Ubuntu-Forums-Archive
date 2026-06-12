---
title: "MythWeb creates zero byte thumbnail images"
date: 2008-03-21
forum: Mythbuntu
---

### Post by davilla on 2008-03-21
New Mythbuntu install with updates from existing. I backed up the original database to retain the recorded video. This is a dual PRV-150 with IR blasters to two Dish 301 receivers for SD content and a dual tuner HDHomeRun for HD content. Everything is working fine except MythWeb thumbnail generation. 

The video storage is in /video/disk1, /video/disk2, /video/disk3, /video/disk4. There's a sym link in /var/lib/mythtv/video to all four drive mount mounts.

Mythweb creates pngs in /var/www/mythweb/data/cache but they are all zero byte count. pngs are also created for each saved video in the four drive mount points.

Suggestions?

---

### Post by Prefader on 2008-03-21
Fix here:
[http://www.gossamer-threads.com/lists/mythtv/commits/258540](http://www.gossamer-threads.com/lists/mythtv/commits/258540)

basically, just edit the file /var/www/mythweb/modules/tv/tmpl/default/recorded.php.
Change the line (~300) that says
```
><img src="<?php echo $show->thumb_url(100,0) ?>"></a>
```
to
```
><img src="<?php echo $show->thumb_url(160,120) ?>"></a>
```

---

### Post by davilla on 2008-03-21
That fixed it, thanks.

---

### Post by SeanOB on 2008-06-08
I had the same issue - thanks for the fix!

I scoured the internets for this - and couldn't find it anywhere...  until now.

Thanks!

---

