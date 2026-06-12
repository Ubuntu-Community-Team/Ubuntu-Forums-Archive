---
title: "Want to remove track numbers ( for mp3 files ) - any applications/scripts available ?"
date: 2009-05-22
forum: Multimedia Software
---

### Post by ActiveFrost on 2009-05-22
I've a pretty big mp3 collection but most of these mp3 files are named as _12-artist - song title_ !
Are there any scripts/apps to remove these track numbers ( auto-rename files ) ?

---

### Post by kidders on 2009-05-23
Hi there,

You may not need any particular apps to perform basic rename operations like that. Doing it yourself can be just as quick. For instance ...```
$ ls -l
total 0
-rw-r--r-- 1 kidders kidders 0 2009-05-23 16:18 1-Song A
-rw-r--r-- 1 kidders kidders 0 2009-05-23 16:19 2 Song B
-rw-r--r-- 1 kidders kidders 0 2009-05-23 16:19 3. Song C
$ for f in [0-9]*; do echo $f | sed 's/^[0-9]*\W*//'; done
Song A
Song B
Song C
```
Sed is a handy tool for transforming text using regular expressions. The above example searches for filenames starting with numbers, drops leading digits & non-word characters & spits out the results. Once you've figured out how to mangle your filenames the way you want them, you could turn a test command like that into a bulk renaming operation ...```
$ for f in [0-9]*; do mv "$f" "`echo $f | sed 's/^[0-9]*\W*//'`"; done
$ ls -l
total 0
-rw-r--r-- 1 kidders kidders 0 2009-05-23 16:18 Song A
-rw-r--r-- 1 kidders kidders 0 2009-05-23 16:19 Song B
-rw-r--r-- 1 kidders kidders 0 2009-05-23 16:19 Song C
```

Two other things worth mentioning ...[LIST]
[*]For simplicity, the above is predicated on no two filenames evaluating to the same thing. That's not a big problem to get around, but it's worth pointing it out all the same.
[*]You may also want to work "find" into my examples, so you can traverse entire directory trees in one go.
[/LIST]

I hope that helps.

---

### Post by neo_1in on 2009-05-23
pyRenamer

---

