---
title: "remove text from title in mp3 tag in e.g. easytag?"
date: 2010-04-20
forum: Multimedia Software
---

### Post by pickarooney on 2010-04-20
I'm trying to remove the .mp3 from the track tag (id3v2) in my mp3 collection but am not sure how to go about it.

Can anyone talk me through converting all tracks with e.g.
TITLE= the beatles - eleanor rigby.mp3
to
TITLE= the beatles - eleanor rigby

either with easytag or a script or something else. 

I started writing a script but got lost in the sed commands :(

---

### Post by Objekt on 2010-04-20
Tag for interest.  I'd like to know the answer here too.

I have used EasyTag to rescue lots of my music files from the tyranny of iTunes, but there was plenty of manual work involved.  EasyTag does not seem to have any way to designate a group of files for batch renaming, or renaming according to a set of rules.

A perl script could work, but you would have to learn all the gory details of how to parse MP3 tags, deal with exceptions, etc.  Probably not worth the effort for a few dozen or hundred files.

---

### Post by pickarooney on 2010-04-21
Yeah, I know I *could* do this myself but I calculate the work involved not being worth the result :)

---

### Post by Objekt on 2010-04-21
I know - at that point, you might as well start your own software project.

So far I haven't found anything better than EasyTag, for straightening out misspelled filenames and garbage ID3 tags (thanks a bunch, iTunes!!).

That said, some of the features of EasyTag aren't completely obvious at first, and its documentation not exhaustive.  I'll try to remember to play around with it a bit this evening.  Maybe I can come up with a less-painful way to do what you're trying to do.

---

### Post by pickarooney on 2010-04-21
I wrote this in the meantime...

```

for filename in *.mp3
do
  song=`echo "$filename"|sed 's/\.mp3//'`
  id3v2 --song  "$song" "$filename"
done

```

---

### Post by TunaCanTommy on 2010-05-16
Look at GPRename . . . it's in the repos. It does a fine job on batch renaming of file names.  Makes quick work of it.

Edit:  Belay that, just reread and noted you're trying to edit ID3v2 tags . . . !

---

