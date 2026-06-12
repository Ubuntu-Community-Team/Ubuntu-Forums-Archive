---
title: "Can't change genre tag"
date: 2007-12-19
forum: Multimedia &amp; Video
---

### Post by Sepp1 on 2007-12-19
It seems like i can't change the genre on 2 of my album in Rythmbox.
I change them from "Metal" to "Folk-rock", and everything seems to be fine, except that it changes them back if i close rythmbox.
When i next open it again they are changed back to "metal".
It is a very small problem as the two albums just as well could be categorized as "metal", it just puzzles me, because they are the only two albums in my collection that behaves so. 
My brother in law asked me if they were "write-protected", but i cant seem to find were to check that.
Thx in advance.

---

### Post by bom28 on 2007-12-19
It's probably because these files have an APE tag, I saw this problem multiple times on the forum already, rhythmbox seems to modify the id3v2 tag but read the APE tag.
You have to find a program that can remove the APE tag.

---

### Post by Sepp1 on 2007-12-20
Thx for the help.
I didn't find any software in the repository that could remove APE tags as such. But according to wikipedia you can't affix APE tags to Ogg vorbis files.
I solved the problem by converting the files to Ogg, and then back to Mp3 again, using sound converter from the repository.

Everything works fine now.

---

### Post by bom28 on 2007-12-20
You really shouldn't do this kind of conversion, you lose some quality each time. :(

Some software may edit the APE tag without mentioning it
I know gmusicbrowser can edit/remove APE tags, but it's not really practical to use it just to edit a tag and it's not yet in the official repository.
Anyway I guess it's too late now...

---

### Post by Sepp1 on 2007-12-21
I know i lose some quality, which is why i backup'ed the files before converting.:)
So, no it is not too late.
That said, I really can't hear the difference in quality.

I'm still a little new to Ubuntu, so I am very careful about software outside the repository (i do have some though). I tried to edit the tags using EasyTAG, without result.

Only sissies backup.
Real men cry.

---

### Post by ishkabob on 2008-02-06
Hi there, I've had similar problems with my mp3 files and tried several programs to remove those ape tags.  I finally had success using foobar2000 under wine.  Foobar2000 is a player/tagger for windows that loads my entire library (~50 gigs) in under 30 seconds.  Anyway, foobar2000 should be able to strip those ape tags from ogg files just as well as mp3 considering ape tags aren't *supposed* to go in mp3 or ogg files.  Give it a try.

---

### Post by hackle577 on 2008-03-01
Command line APE tag removal tool:

[http://ubuntuforums.org/showthread.php?t=292111](http://ubuntuforums.org/showthread.php?t=292111)

---

