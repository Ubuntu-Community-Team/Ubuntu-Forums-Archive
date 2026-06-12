---
title: "Brasero - won't burn file &gt; 4GB ?????? HELP!"
date: 2007-11-25
forum: Multimedia &amp; Video
---

### Post by riggits on 2007-11-25
Hi, I tried to burn my movies to DVD and Brasero/Gnomebaker/etc will not cooperate. I've never seen this odd limitation before, and cannot figure out a solution.

To reproduce error:
1. use Brasero, add any file > 4GB to the project
2. burn to disc.

Brasero spits out the disc with an error every time. I turned off Windows compatibility, tried different speeds, and always the same result. On the same machine Nero (in Windows XP) has no problems burning any disc, any size, no problems at all. The DVD burner is BenQ DW-1640 and works fine with Windows.

A thought: is there a way to force Brasero to use the UDF file system?????
PLEASE HELP! and thanks in advance :)

Other details: Ubuntu Gutsy 7.10, AMD64, have AMD X2-4200, 4GB RAM
-running on ext3 filesystem exclusively.

Note: I found this rather unhelpful site with Google: [grigio](http://www.grigio.org/tag/udf)
It looks like a lot of rubbish to me. Maybe somebody can explain how to burn a DVD with Brasero using these instructions?

EDIT: NEW SOLUTION
I found that Nero Linux will effortlessly burn UDF dvds with any size file you want. Apparently the free solutions (k3b, Gnomebaker, Brasero) do not support UDF in a useful way as of December 2007.

---

### Post by autocrosser on 2007-11-25
I would contact Luis about it--he seems to have good interaction with Ubuntu--You can get to his address at:   [http://freshmeat.net/projects/brasero/](http://freshmeat.net/projects/brasero/)

---

### Post by riggits on 2007-11-27
Ubuntu feels like Office 2007 now. You can put data in but you can't get it back out.
If/when I find a solution I'll post it here and help free all you people.

EDIT: there is no free solution. Sorry folks.

---

### Post by goonies on 2007-12-10
> **riggits said:**
> Hi, I tried to burn my movies to DVD and Brasero/Gnomebaker/etc will not cooperate. I've never seen this odd limitation before, and cannot figure out a solution.

To reproduce error:
1. use Brasero, add any file > 4GB to the project
2. burn to disc.

Brasero spits out the disc with an error every time. I turned off Windows compatibility, tried different speeds, and always the same result. On the same machine Nero (in Windows XP) has no problems burning any disc, any size, no problems at all. The DVD burner is BenQ DW-1640 and works fine with Windows.

A thought: is there a way to force Brasero to use the UDF file system?????
PLEASE HELP! and thanks in advance :)

Other details: Ubuntu Gutsy 7.10, AMD64, have AMD X2-4200, 4GB RAM
-running on ext3 filesystem exclusively.

Note: I found this rather unhelpful site with Google: [grigio](http://www.grigio.org/tag/udf)
It looks like a lot of rubbish to me. Maybe somebody can explain how to burn a DVD with Brasero using these instructions?

EDIT: NEW SOLUTION
I found that Nero Linux will effortlessly burn UDF dvds with any size file you want. Apparently the free solutions (k3b, Gnomebaker, Brasero) do not support UDF in a useful way as of December 2007.

Ironically we have the same drive and problem.  Does Nero Linux support multi sessions?  Rather not use any KDE based programs on my system.

---

### Post by tkmn on 2007-12-10
It can be done, commandline style atleast.

genisoimage -udf -allow-limited-size -r -J -V "Disc Name" -o ~/image.iso /path/to/bigfile

```
-udf = UDF filesystem
-allow-limited-size = enable files larger than 2 GB (only on UDF)
-r = Rock Ridge
-J = Joliet
-V = volume ID
-o = output file

```
Then burn the image file in Brasero, Gnomebaker etc..

The manual says: "UDF support is currently in alpha status", but it appears to be working fine.

---

### Post by ahaslam on 2007-12-21
Deleted: unrelated problem my end...

---

### Post by berftude on 2007-12-30
> **tkmn said:**
> It can be done, commandline style at least.
genisoimage -udf -allow-limited-size -r -J -V "Disc Name" -o ~/image.iso /path/to/bigfile


Thanks for the tip, tkmn!  This is one of those things I know I will (1) have to do more than once, and (2) not remember how to do, so rather than add clutter to my bookmarks, I wrapped your shell command in a script which I've attached to this post.  Perhaps others will find it useful.

USAGE:  mkudfiso.sh [> 4 GB file] [disc title] [.iso name]

---

