---
title: "Rhythmbox ID3 tags not found by gtkpod"
date: 2008-02-05
forum: Multimedia &amp; Video
---

### Post by kris_a on 2008-02-05
Hello,

I have just been through my entire music collection in Rhythmbox making sure everything was tagged correctly, then when I reloaded the mp3's into gtkpod all of the files I have changed the tags on are now apparently untagged...

They still show the correct tags when reloaded in Rhythmbox or when I view the file properties in Nautilus, but even easytag says the files are now not tagged, very confusing!

I have done a bit of testing, as soon as I change part of a tag in Rhythmbox easytag stops showing any of the tag info, updating tags in easytag works fine and the changes show up in Rhythmbox..

Anyway, anybody know how I can resolve this situation without re-tagging my whole collection again?  I guess it is something to do with ID3 tag version, but haven't had much luck finding a solution.

Thanks in advance,
Kris.

EDIT: Seems that Quod Libet reads the tags OK, ID3 data must be written by Rhythmbox

---

### Post by tgalati4 on 2008-02-05
There are 3 or 4 flavors of ID3 tags.  Sometimes they are stored in front of the file, sometimes at the end of the file, and sometimes in their own database, without touching the file.  Try using easytag.  In a terminal:

sudo apt-get install easytag

I don't have my notes with me, but each music application uses a different ID3 library and different version so such problems do arise.  Do a search on ID3 tags so you will understand the differences.  The trick is to find the music player application that uses the same ID3 library as gtkpod.  Offhand I don't remember what programs they are, but others may post their experience.

---

### Post by kris_a on 2008-02-05
Thanks for the reply, I have already been trying Easytag, all the MP3's whose tags I edited in Rhythmbox show up as being untagged, but for some reason Quod Libet can read them...

I've also been trying eyeD3 that reads all the tag versions, it crashes when I try to read the ones tagged by Rhythmbox.

This is a bit annoying, it took ages to tag them all correctly :(

Maybe I will just re-tag them in Easytag using the CDDB lookup when I have a few spare hours and take it as a lesson learnt the hard way.

If anybody knows a prgram that can recover these tags (they are still in there somewhere) then please let me know!

Kris.

---

### Post by kris_a on 2008-02-05
OK, found a work around...

Added the mp3's 1 folder at a time to gtkpod, when files appear with no tagging I did the following:

 - Go to the correct folder in Ex Falso (find it in the repos)
 - Select the file whose tag doesn't appear in gtkpod, the tags will show in Ex Falso
 - Click in the Write column for each tag (i.e. title, artist etc)
 - Click save

Now if you right click the song in gtkpod and select 'Update Tracks from File' and the tag should appear correctly.

It seems that Rhythmbox doesn't write the tags correctly...

Kris

---

### Post by onthefence on 2008-02-06
if i can piggyback on this thread, I am having trouble in easytag browsing one of my partitions. can the program read ntfs files systems? 
thanks

---

### Post by onthefence on 2008-02-06
Also, is there a way to batch change a tag, I found out how to apply changes as a batch, but I couldn't figure out how to apply the same tag across many files without doing it individually
For some reason, when I imported this audiobook in iTunes, it grabbed diferent information for the different discs so that when I look at it on my mp3 player, it have the book spread out over different genres, artists, and even albums.

---

### Post by kris_a on 2008-02-06
Hello,

From all my playing around with tags I think I can answer your question...

In easytag select all the files you want to apply the same tag to, enter the tag and then click the small button on the right hand side of the tag entry field, I think that should then apply it to all the files you have selected.

Otherwise, use 'ex falso', I have found it more user friendly than easytag.

Hope that helps,
Kris.

---

### Post by onthefence on 2008-02-07
I will try, thanks for the response!

---

