---
title: "not sure where this goes - looking for a photo orginization program like KPhotoAlbum."
date: 2008-07-11
forum: Multimedia Software
---

### Post by Mysticle31 on 2008-07-11
I have been getting all of my computer images off of misc backup DVDs and organizing all of my prints and negatives.  I will soon scan many of my prints and negatives and other "paper" photos.

I have been thinking of using a good photo organizer-tagger-viewer program so I can easily find what I'm looking for instead of making a really long file name and directory structure with a "about this pic" text file (ex Trip to Asia 2004/Nepal/Pic one.jpg and Pic one about.txt)

However, what happens if I use KPhotoAlbum or some other program (any reccomendations) and 10 years from now KPhotoAlbum does not exist.  What happens to the database?  How is it stored?  What if I need to migrate from a KPhotoAlbum database to a XXXXX new photo program in 10-20 years?  The database must be able to evolve.  I don't want to end up with useless junk.  Then I'm back to a bunch of unorganized pictures!

For example, I have lots of stuff stored on AOL organize cabinets files but can't even look at them anymore.

---

### Post by tinny on 2008-07-11
> **Mysticle31 said:**
> I have been getting all of my computer images off of misc backup DVDs and organizing all of my prints and negatives.  I will soon scan many of my prints and negatives and other "paper" photos.

I have been thinking of using a good photo organizer-tagger-viewer program so I can easily find what I'm looking for instead of making a really long file name and directory structure with a "about this pic" text file (ex Trip to Asia 2004/Nepal/Pic one.jpg and Pic one about.txt)

However, what happens if I use KPhotoAlbum or some other program (any reccomendations) and 10 years from now KPhotoAlbum does not exist.  What happens to the database?  How is it stored?  What if I need to migrate from a KPhotoAlbum database to a XXXXX new photo program in 10-20 years?  The database must be able to evolve.  I don't want to end up with useless junk.  Then I'm back to a bunch of unorganized pictures!

For example, I have lots of stuff stored on AOL organize cabinets files but can't even look at them anymore.

Have you tried F-Spot?

Its all ways a good idea to back up your photos too.

---

### Post by Mysticle31 on 2008-07-14
Yes I understand about backups.

I'm wondering about the database of tags and info itself.

For example I have a database of music in banshee with ratings and now it looks like all that is stuck there becouse I can't find a way to convert the database to another program.

I definitely don't want that to happen to tags and info that I put in for pictures.

Can I tag images that I scan with a year to view in the app?  Scroll to the 1991 section lets say?

---

### Post by timcredible on 2008-07-14
well, digikam will build it's database if it doesn't already have one, but i don't know about a way to import/export tags.  i guess if i were you, i'd go with the most popular app and hope that it either continues on for many years or that the next app you want to use will import that database.  there's no guarantees about apps continuing, in the open source world or the commercial world

---

### Post by jure1873 on 2008-07-17
digikam can store tags and other metadata in its database and in the exif of jpg pictures so other programs could import your tags just from the pictures alone, but probably nobody knows what is going to be used in 20 years. The digikam database is in sqlite format so you could export it to sql and then import that into some other program but I haven't heard about any program that would do these things out of the box...

---

### Post by sketching on 2008-08-03
I'm using [mapivi](http://mapivi.sourceforge.net/mapivi.shtml) to store all IPTC info in the JPG files themselves. Not a pretty program but does just what I want to do. Real easy to use and no need to worry about databases being corrupted or out-dated.

---

### Post by SanskritFritz on 2008-10-09
Well, the thread is quite old, i hope i'm not too late with my thoughts. I focused only on Keywords in my research with a similar problem. What I found out, that KPhotoAlbum is well able to synchronise its database with the EXIF and IPTC fields of the picture files. This way the data will be portable. KPhotoAlbum builds its database when it encounters a new set of files tagged by DigiKam of Picasa for example.
DigiKam is able to read and store the Keywords (not sure about other tags) from and in its database. The IPTC Keywords tag is read/written by Picasa. 
So I think the best practice is to write the metadata into the IPTC and EXIF data of the pictures, that will probably change the least and will be probably portable the most.

---

### Post by jis on 2008-10-21
SanskritFritz, can you answer this: [http://ubuntuforums.org/showthread.php?t=530386](http://ubuntuforums.org/showthread.php?t=530386)

In my experience tags of various categories in KPhotoAlbum are not stored as IPTC data in image files even if you do Maintenance > Write metadata to files.

---

### Post by SanskritFritz on 2008-10-22
> **jis said:**
> SanskritFritz, can you answer this: [http://ubuntuforums.org/showthread.php?t=530386](http://ubuntuforums.org/showthread.php?t=530386)
In my experience tags of various categories in KPhotoAlbum are not stored as IPTC data in image files even if you do Maintenance > Write metadata to files.Hi, yes, I can answer that question in detail tonight, when I get to my Kubuntu box at home. In a nutshell though: KPA is able to store the tags in the IPTC section of the files, but not by default. You have to check out the EXIF section in the Settings dialog, I cannot tell the details now, I'm at work, no Linux here. There is also a confirmed bug I found, that is, when you have a picture collection already tagged by DigiKam or Picasa for example (that means, the IPTC Keywords and Caption fields are populated), and create the KPA database, it imports only the first keyword even if there are more defined in the picture (a common scenario!). The bug will not be fixed in KDE3, as the developers are concentrating now on the new KDE4 version, where the tag handling will be completely rewritten, using external scripts or plugins. More on this subject in a while :)

---

### Post by SanskritFritz on 2008-10-23
Ok, so here we go:
The setting in *Settings / Configure KPA / Metadata* see the attached screenshot to get a clue.
If this is set, KPA reads the Keywords from the IPTC sections when building a new database (beware of the bug mentioned in my previous post!). With these settings, choosing *Maintenance / Write metadata to files *from the KPA menu works perfectly (this time for Keywords). See the other tag settings if interested in another tags. I prefer to use only the Keywords and the Caption tags, as they are more or less standard, and read/written by Picasa or DigiKam, so I can use my collection tags in KPA, Picasa, DigiKam transparently. HTH!

---

### Post by jis on 2008-10-23
SanskritFritz, do you mean you use only the Keywords category of all possible categories in KPhotoAlbum?

---

### Post by jis on 2008-10-24
I read somewhere that some IPTC categories are deprecated, so better stick to Keywords category. That is called Events in some future release: [http://websvn.kde.org/trunk/extragear/graphics/kphotoalbum/ChangeLog?r1=833892&r2=835155](http://websvn.kde.org/trunk/extragear/graphics/kphotoalbum/ChangeLog?r1=833892&r2=835155)

I have managed to write keywords (i.e. tags) as IPTC data to image file. Using the (application) tags when uploading to Flickr by a plugin is buggy: it doesn't like some characters in metadata to begin with. (See Bug #288326)

---

### Post by SanskritFritz on 2008-10-25
> **jis said:**
> SanskritFritz, do you mean you use only the Keywords category of all possible categories in KPhotoAlbum?Yes, and the Caption. The reason is simple: compatibility with Picasa and DigiKam!

---

### Post by SanskritFritz on 2008-10-27
> **jis said:**
> I read somewhere that some IPTC categories are deprecated, so better stick to Keywords category. That is called Events in some future release: [http://websvn.kde.org/trunk/extragear/graphics/kphotoalbum/ChangeLog?r1=833892&r2=835155](http://websvn.kde.org/trunk/extragear/graphics/kphotoalbum/ChangeLog?r1=833892&r2=835155)jis, I see you are familiar with programming? Do you have the time and mood and energy to find the Keywords import bug in KPA?

---

### Post by jis on 2008-10-27
Ia have some general programming knowledge, but I am not familiar in programming in linux.

Who told you that the bug will not be fixed in KDE3? Do you have a 
link to the bug report.

---

### Post by SanskritFritz on 2008-10-27
> **jis said:**
> Who told you that the bug will not be fixed in KDE3? Do you have a 
link to the bug report.I spoke with the developer (jkt|) on the IRC, here is the transcript:
> (17:11:25) SanskritFritz: jkt|: did you read my comment above? &#65279;"there is a problem with the import, it imports only the first keyword, the rest is ignored" can you please look into that?
(17:19:35) jkt|: SanskritFritz: yep, that sucks
(17:19:46) jkt|: SanskritFritz: did I tell you the kde3 codebase is dead? :)
(17:19:57) SanskritFritz: jkt|: yeah, you told me ;-)
(17:22:12) SanskritFritz: but that is strange to me actually, as the kde4 is unstable yet, and there is no bug fixes for the kde3 branch?
(17:22:31) SanskritFritz: wasn't the switch to kde4 too fast?
(17:22:40) SanskritFritz: or too early maybe?
(17:23:10) SanskritFritz: im not planning to switch to kde4 in a while, too big and instable
(17:23:33) SanskritFritz: that is what I heard :-/
(17:28:40) jkt|: SanskritFritz: the point is that you can run 3.5 as a desktop environment, but use some kde4 apps
(17:28:44) jkt|: like kphotoalbum :)
(17:28:54) jkt|: that's what I'm doing at the moment
(17:29:53) jkt|: **you know, we have four people working on KPA at their free time, and nobody of us is motivated to work on kde3 anymore**
(17:30:21) jkt|: we all believe that making the kde4 version of kpa is better than maintaining the 3.x branch
(17:30:21) SanskritFritz: I understand
(17:30:33) jkt|: you just need kdelibs from kde4
(17:31:05) jkt|: (and optionally libkdcraw for RAW files and nepomuk for image rating)
(17:31:07) SanskritFritz: I see, that sounds good
(17:31:51) jkt|: the bad news for you is that there's no iptc import in kphotoalbum for kde4 yet :)
(17:32:17) SanskritFritz: although the kde4 apps look very different from the kde3 theme
(17:32:27) SanskritFritz: see? lol
(17:33:24) SanskritFritz: anyway, I can live with those small glitches, I'll tag my collection further with DigiKam for the time being
(17:33:49) SanskritFritz: and I want to say thanks for your help

---

### Post by jis on 2008-10-31
SanskritFritz, it did not seem to work better in 8.10 even if it is KDE4 based AFAIK.

One insteresting alternative is Geeqie, which is based on gqview.
[http://geeqie.sourceforge.net/](http://geeqie.sourceforge.net/)
Unfortunately, its package in ubuntu 8.10 is not mature enough to write keywords to IPTC. BTW. digikam tells you can write only visible ascii characters in IPTC keywords and they have limited length.

There should be some ranking for ubuntu packages that tell what are the major known shortages and advantages of each application in repositories.

I guess fixing the bug in kphotoalbum wouldn't be a big work, if you know what you are doing.

---

### Post by SanskritFritz on 2008-11-01
> **jis said:**
> SanskritFritz, it did not seem to work better in 8.10 even if it is KDE4 based AFAIK.Yup, the dev has told us, there is not even support for IPTC yet. But as the development progresses, we can expect more :-)

> **jis said:**
> One insteresting alternative is Geeqie, which is based on gqview.
[http://geeqie.sourceforge.net/](http://geeqie.sourceforge.net/)
Unfortunately, its package in ubuntu 8.10 is not mature enough to write keywords to IPTC.Nice but not for me, I rather use QT apps.

> **jis said:**
> BTW. digikam tells you can write only visible ascii characters in IPTC keywords and they have limited length.True, but that is no problem for me, I just use some tags, thats all.

> **jis said:**
> I guess fixing the bug in kphotoalbum wouldn't be a big work, if you know what you are doing.There is the catch ;-) Still, I didnt give up, I will try to find it eventually, as I'm not planning to switch to KDE4 soon.

---

### Post by jis on 2008-11-11
> **SanskritFritz said:**
> 

Nice but not for me, I rather use QT apps.

True, but that is no problem for me, I just use some tags, thats all.

There is the catch ;-) Still, I didnt give up, I will try to find it eventually, as I'm not planning to switch to KDE4 soon.

I don't see any advantage in QT apps over GTK.

If you non-ascii characters in tags, it is an issue.

What kind of catch?

---

### Post by SanskritFritz on 2008-11-11
> **jis said:**
> I don't see any advantage in QT apps over GTK.For me it's the aesthetics (uniform look and usability), and the integration with KDE (and other QT apps).

> **jis said:**
>  If you non-ascii characters in tags, it is an issue.It is true. But on the other hand it is just a matter of encoding. I tag the files for my use, and no chinese guys will complain about non readable texts ;-)

> **jis said:**
> What kind of catch?Here:
> **jis said:**
> if you know what you are doing.There is the catch :lolflag:

---

