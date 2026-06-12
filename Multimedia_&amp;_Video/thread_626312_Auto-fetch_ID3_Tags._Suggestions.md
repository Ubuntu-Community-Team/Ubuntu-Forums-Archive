---
title: "Auto-fetch ID3 Tags. Suggestions?"
date: 2007-11-28
forum: Multimedia &amp; Video
---

### Post by flexgrip on 2007-11-28
Here's the story,

I have a ton of music in a directory. I myself organized most of the music into folders (genre > artist > album > etc). When I say a ton of music I mean 26,000 mp3's that are not tagged right.

I basically need software that will start at the base of the folder and fetch ALL the ID3 tags. I don't want to add albums separately. I just want to click go and have it add ID3 tags to anything it can find on amazon, come back 8 hours later and have it be done.

I can rename them with easytag or some of the other apps I have played around with, ONCE they are properly tagged.

Here are what I have tried to use and cannot get to work.

Picard (will autotag but cant seem to get it to do a whole directory)
EasyTag (same with easytag
Cowbell
Some others too...

Nothing does the entire folder on its own. They wall want me to babysit them.

Thanks a lot for any light you can shed on this guys. 

P.S. I deleted my windows partition a month ago!!!

---

### Post by DasCrushinator on 2007-12-25
Does such a thing not exist?

---

### Post by csisgro on 2007-12-26
tagtool works great for this. sudo apt-get install tagtool or install through synaptic.

---

### Post by DasCrushinator on 2007-12-26
> **csisgro said:**
> tagtool works great for this. sudo apt-get install tagtool or install through synaptic.

I have this already installed and as far as I can tell, it doesn't go out and fetch tags starting at a root directory based on folder names.

---

### Post by ron999 on 2007-12-26
Hi

I think that you are asking too much. :roll:

When you use a program such as EasyTag you check each album (in a folder) against the database, one album at a time.
Then tidy up the tags and make corrections and add extra comments. 
Then save.
Then get the next album folder and do it again.
Till you've gone through all the albums.
And if you've got some tracks that aren't in an album then you have to type in the tags yourself.
8)

---

### Post by DasCrushinator on 2007-12-27
> **ron999 said:**
> Hi

I think that you are asking too much. :roll:

When you use a program such as EasyTag you check each album (in a folder) against the database, one album at a time.
Then tidy up the tags and make corrections and add extra comments. 
Then save.
Then get the next album folder and do it again.
Till you've gone through all the albums.
And if you've got some tracks that aren't in an album then you have to type in the tags yourself.
8)

Doesn't hurt to ask :roll::roll::roll:
Especially when you have over 500GB of music :roll::roll::roll:

---

### Post by andresFang on 2008-07-09
Well, I'm all linux but sometimes I realize that in windows we can find some ideal programs that make life easier, I suggest you Winamp, it has auto-tag and it's automatic, I rather tagtool because it's in linux and i just need v1, but in your case it could be useful XD mmm... I cannot remember but there is an editor that can edit your tags according to your directory but i cannot remember which but you can search because you now know that it exists hehe, bye. sorry about my english, is not my native language.

---

### Post by nycste on 2008-07-09
hiya, im in a similiar situation, currently testing many audio players and trying to sort my music collection +100gb

trying to figurout how i want them labeled, how to label them, etc etc

and in linux well spaces in file names are a NONO they all have spaces cuz well i got all songs while in windows and i never commandlined anything

just sharing, ill be checking this thread often and look foward to replies

---

### Post by zombiepig on 2008-07-09
Picard will definitely do this, and do a fantastic job of it. (I use it all the time). You should just be able to go "Add Folder", choose the top level music folder, and picard will import everything from it. Then, click on "unmatched files", and hit the "cluster" button. This will make picard group tracks into albums (makes online lookup quicker, since it doesn't need to query for for every separate track on an album). Then, finally, highlight all the tracks and hit the "lookup" button. Picard will grab all the details for the tracks - then you just highlight them and hit save, and the metadata will be written to the files.

Picard is great for doing this, since it uses the musicbrainz database, which means you not only get track/album name/artist details, but a bunch of extra things like composer, record labels, release dates, performers, technicians, etc... (depending on that data being present at [http://musicbrainz.org/](http://musicbrainz.org/)

But yeah, use picard :)

---

