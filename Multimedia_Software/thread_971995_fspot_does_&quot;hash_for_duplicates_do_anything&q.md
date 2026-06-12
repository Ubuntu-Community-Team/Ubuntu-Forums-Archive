---
title: "fspot: does &quot;hash for duplicates do anything?&quot;"
date: 2008-11-05
forum: Multimedia Software
---

### Post by philnoon on 2008-11-05
Fspot 0.5.0.3, ubuntu 8.10.

I've been looking forward to the new duplicate detection in fspot, but I seem to have a problem. 

If I try to import the same image twice, the duplicate is detected - good. 

However, to enable the existing database for duplicate detection, I need to run "Tools->Hash for Duplicates"; this gives a dialogue with three buttons:
- execute
- stop
- close

When I press execute there is no feedback at all, no message, no change of test on the screen, nada. And fspot does not subsequently identify duplicates of the existing images.

Any ideas?

---

### Post by chadeldridge on 2008-11-06
same thing here, does the button actually do anything at all?

---

### Post by blackbird-xx on 2008-11-08
Same thing on AMD-64.  Running Hardy self-compiled f-spot 0.5.0.3.

Sorry, no solutions at the mo.

---

### Post by slight on 2008-12-09
It seems the GUI doesn't give any feedback but F-Spot does slowly hash the images after you click the button.

You can try this SQL command to query how many images in your collection have hashes:

**sqlite3 ~/.gnome2/f-spot/photos.db "SELECT count(*) FROM photos WHERE md5_sum IS not NULL AND md5_sum != ''"**

(all on one line)

Run that command, then open F-Spot, click the execute button for has detection, then run the above sqlite command again in 20 seconds or so, and you should see the number increase.

I believe there may be a bug in the current hash detection code that doesn't look to empty md5s (md5_sum='') as well as null md5s, as there's a mention of this on the latest CVS version. If you get a result greater than 0 for this:

**sqlite3 ~/.gnome2/f-spot/photos.db "SELECT count(*) FROM photos WHERE  md5_sum = ''"**

That number of photos may not get caught by the current version.

It's easy to convert the ones with empty md5s to null md5s but there's a chance that f-spot allows the two different versions for a reason so I'm not going to post the SQL to do that. If someone wants it you can email me and I'll give it to you, but only after hefty warnings about the (probably small, but potentially serious) risks :)

tolan _a_t_ overtops d-o-t o,r,g

---

### Post by jared_c on 2008-12-17
It looks like all my files imported under 8.04 have blank md5sums, instead of NULL.  I guess I'll just have to delete pictures off of the camera, instead of reimporting them time and time again.  

Manual organization!  So difficult!

---

### Post by meonkeys on 2008-12-29
> **slight said:**
> I believe there may be a bug in the current hash detection code that doesn't look to empty md5s (md5_sum='') as well as null md5s

I changed rows in photos with md5_sum = '' to NULL and hash detection appeared to work properly. Thanks for the tip!

---

### Post by chadeldridge on 2008-12-29
[QUOTE=slight;6339348]
sqlite3 ~/.gnome2/f-spot/photos.db "SELECT count(*) FROM photos WHERE md5_sum IS not NULL AND md5_sum != ''"/QUOTE]

That command shows 2204 which is = to the total number of pics in this gallery, although there are obvious duplicates.  Any ideas?

---

### Post by jouke.postma on 2009-01-04
This is what I did to solve the general empty field problem. 

1) backup your database (don't skip)
2) sqlite3 ~/.gnome2/f-spot/photos.db "UPDATE  photos set  md5_sum = NULL where md5_sum == ''"

use it add your own risk - messing around with your photo database could potentially destroy it.

---

### Post by Joeybuntu on 2009-01-31
Same problems here you guys have. After all the pics were hased i expected to have a tool to at least identify them. So, i wrote a script to do just that. What this does:

-- create worktable 1 with distinct md5sums and counts
-- create worktble 2 with just the counts
-- create tag names from counts and set category
-- create the tags
-- create some indexes to speed up the final step
-- finaly, link the photos to the tags
-- drop the things we've created

In other words: you get a 'Duplicates' tag with underneath it tags with the number of duplicates ('2 copies', 3 copies' etc.). Attached to your collection ofcourse.

As always, FIRST close f-spot and MAKE A BACKUP OF photos.db!

On a Inspiron 1525 this runs under 6 seconds on a 44.845 photo database, creating 6 tags for 8.229 photos.

update 4-feb-09: removed index on worktable, doubles the speed of execution.

```

echo "
.echo on
.bail on

-- create worktable 1 with distinct md5sums
create table duplicates_w01
as select md5_sum as md5_sum, count (1) as count
from photos
group by md5_sum
;

-- create worktble 2
create table duplicates_w02 (
  tag_id    INTEGER PRIMARY KEY AUTOINCREMENT,
  count     INTEGER,
  tag_name  TEXT,
  category  INTEGER)
;

-- add first tag to w02
insert into duplicates_w02
select max (id) + 1, 0, 'Duplicates', 0
from tags
;

-- insert the other tags from w01
insert into duplicates_w02 (count)
select distinct (count)
from duplicates_w01
where count > 1
;

-- create tag names from counts and set category
update duplicates_w02
set tag_name = quote(count)||' copies',
    category = (select min (tag_id) from duplicates_w02)
where count > 0
;

-- create the tags
insert into tags (id, name, category_id, is_category, sort_priority)
select tag_id, tag_name, category, 1, 0
from duplicates_w02
;

-- create some indexes to speed up the final step
CREATE INDEX idx_photos_md5_sum ON photos(md5_sum);

-- and finaly, link the photos to the tags
insert into photo_tags (photo_id, tag_id)
select p.id, w02.tag_id
from photos p, duplicates_w01 w01, duplicates_w02 w02
where w01.md5_sum     = p.md5_sum
and   w01.count       = w02.count
;

-- drop the things we've created
DROP INDEX idx_photos_md5_sum;
DROP TABLE duplicates_w01;
DROP TABLE duplicates_w02;

"|sqlite3 ~/.gnome2/f-spot/photos.db

```

Good luck.

Joe

---

### Post by yoav on 2009-02-22
Hi,

This solution seemed to work well - thanks! There's only one little problem. f-spot seem to have imported duplicate images into its directory and added a "-1", "-2", etc. to the filename. The method you suggest above assigns the "duplicate" tag to the original image, and not to the copy, so that deleting them will leave me with a bunch of of filenames with the extra "-1". 

I don't have any experience with sqlite, so I wouldn't know where to start, but maybe there's a way to tell it to assign the "duplicate" tag to the images that were added *last* to the database?

Thanks!
Yoav

---

### Post by m8ryx on 2009-03-23
just wanted to clarify that joeybuntu's script does _not_ do the hashing, it just tags duplicates as such.  Be sure to have f-spot do the hashing for you first.  

I do see that he says pretty much that in the first sentence of his post, but it wasn't quite clear to me, so I puzzled over the thousands of dupes that didn't appear to be dupes.  Thanks all for some good posts, hope this helps a little ;)

Perhaps a summary will help too.  Most of my photos are from pre-0.5.

```
sqlite3 ~/.gnome2/f-spot/photos.db "SELECT count(*) FROM photos WHERE md5_sum IS not NULL AND md5_sum != ''"
```

yields the number of post-0.5 photos

```
sqlite3 ~/.gnome2/f-spot/photos.db "SELECT count(*) FROM photos WHERE md5_sum = ''"
```

if non-zero says tells you what images *might* be ignored (they were in my version...i.e., the hashing algorithm in my version skips all of these.

**Exit F-spot**
```
 cp .gnome2/f-spot/photos.db{,.bkp}
```

creates a backup of your image database (not your images)

[COLOR="Red"]Use at your own risk...modifies database.  This could render F-spot unusable (but probably won't).  Be sure that you made a backup.[/COLOR]
```
sqlite3 ~/.gnome2/f-spot/photos.db "UPDATE photos set md5_sum = NULL where md5_sum == ''"
```

Sets md5_sum from empty to null so that F-spot will see it as hashable.  Rerun the counts from earlier, the former should be the same, the latter should now be zero.

**Start F-spot**
```
Tools->Hash for Duplicates
```

Tell F-spot to start hashing the photos.

Then, either use Joeybuntu's script or F-spot's to remove hash photos.

---

### Post by Majiq on 2009-05-12
I have been having hash problems (especially since I forget to format my SD card), but I just decided today to follow through with the above. I did have to set everything to NULL first, so I followed those instructions. Then I ran Joeybuntu's script (actually, I did try it as a script and it didn't do anything, so I instead did it straight as input to command line) for tagging, and I came up with the following error: 

SQL error near line 41: column name is not unique

Suggestions? I also have to drop the tables, now, because it's being pissy.

---

### Post by Majiq on 2009-05-12
I thought I'd mention that it did ID duplicates, but I don't know if it got them all. I found 533, and manually removed them. It tagged both copies as having the tag, though, so it was a little annoying.

---

### Post by scarf on 2011-06-07
what is the method now for lucid?  i have a ton of duplicate photos that i want to delete.  i found that the photos.db is now in ~/.config/f-spot  and i ran the sqlite3 commands using that path.  

when i open f-spot it says i have 0 photos needing md5 calculation and 0 pending jobs.  clicking on 'execute' doesn't seem to do anything.  it says 'processing images' but i don't really see any activity in top or anything...

then how am i supposed to actually delete the duplicate photos from the hard drive?  where do i see the duplicates in f-spot, or how do i run joeybuntu's script?

---

