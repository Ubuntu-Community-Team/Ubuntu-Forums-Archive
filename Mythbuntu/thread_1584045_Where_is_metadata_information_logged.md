---
title: "Where is metadata information logged?"
date: 2010-09-28
forum: Mythbuntu
---

### Post by Turbocopter on 2010-09-28
I am new to linux and just installed mythbuntu. I had some initial help and got everything configured and running smoothly, but I have some mistakes in metadata info that got imported in and need to delete that information so that I can get the correct information. Where is that information logged and how can I edit or delete it? Any help would be greatly appreciated!!

---

### Post by sanderd17 on 2010-09-28
Do you mean metadata of mp3 files? try kid3:

```


sudo aptitude install kid3

```

---

### Post by Turbocopter on 2010-09-28
It is all the jacket cover information in my video files.  I have 3 that were chosen wrong becuase I could not see dates listed and chose the original 50's and 60 version of those films and I have (3) phantom files that are not videos at all that are displayed with a question mark in my video folder that I cannot see or delete at the file management level.

---

### Post by LowSky on 2010-09-28
remove the non-film files directly from nautilus if you can. You should be able to. if not open nautilus using the command

gksu nautilus

then for the ones with the wrong art, just press i > go t metadata option and choose the newer film artwork... if it isn't listed, go over to imdb.com search for the film and then use the films number form the url as the code for mythtv's metadata, and it should fill the correct artwork

```
http://www.imdb.com/title/tt**0043286**/
```

---

### Post by Turbocopter on 2010-09-29
Thanks for the info.  The "I" menu was exactly what I was hoping for.  It makes sense that they have a graphical interface for manipulating the metadata information, I just had not found it or read it anywhere.  That worked great!!
 
The phantom files are still a mystery to me because they don't show up in the file system anywhere I have found yet.  I even found a version of "show hidden files" like in windows, but they still do not show up.  I can hit delete from the graphical video folder and it lets me hit that, but then has a message saying that "delete was unsuccessful".  It is a mystery to me.  For the time being, I found a kooky pic online and added blank cover to the top of the pic and installed that as cover art for those phantom files so they are at least not just a big question mark.  I would untimately love to figure out how to get rid of them completely though.

---

### Post by larsolav on 2010-09-29
in the place you view the videos in myth have you tried "m" -> "scan for changes" (or something like that)? MAybe that would get rid of the phantom files in your viewer?

---

### Post by Turbocopter on 2010-09-29
> **larsolav said:**
> in the place you view the videos in myth have you tried "m" -> "scan for changes" (or something like that)? MAybe that would get rid of the phantom files in your viewer?
 
 
I have tried that and no luck there either.  Maybe a little more background is in order....I did my ititial test install of Mythbuntu for a proof of concept on a single 80gig drive and it installed fine and we worked out the component kinks.  I did a couple of test rips of DVD's in the "perfect" format so we could check the player with something burned.  Then I burned (1) ISO because that is the format I ultimately wanted the files to be in.  Then, I intalled a (2) terabyte drive, created the front end folder system on that drive (i.e. video, music, coverart, etc.), deleted the (2) that were ripped as "perfect" leaving just the (1) ISO.  After deleting the two "perfect" files, I copied the remainder of the contents of the original video folder and moved it to the other video folder on the 2tb drive.  What I thought would just be the (1) ISO I had left moved to the other folder on the other drive, was actually the remains after the delete of the other 2 files and the (1) ISO.  That is my theory anyway.  So I think I brought some sort of framework that did not get deleted in the primary delete of those files that are now showing up as phantom files that are not listed in the directory at all since they are deleted, but do show up in the graphical interface for the video file in the front end.   WHeeeeew.
 
Seems to me that if I made another folder on the 2tb drive for videos, moved them one by one into that folder (NOT a "select all"  and move them all at once), that I would have a clean folder without the ghost files, but that would be a long and tedious task at this point since I have like 150 vidoes ripped now.  I would prefer an option at the command line level that would find the rogue code and let me delete it in Terminal.
 
Anyone who can help.....Please help me!  Who likes a challenge?

---

