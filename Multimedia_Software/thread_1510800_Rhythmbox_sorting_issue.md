---
title: "Rhythmbox sorting issue"
date: 2010-06-16
forum: Multimedia Software
---

### Post by MrSlaggers on 2010-06-16
After upgrading to Lucid I noticed that the sorting in Rhythmbox got messed up. I have it set to sort in alphabetical order based off the album name, however for some reason two albums are at the top that shouldn't be there. Here is a picture of what I am experiencing:

[IMG]http://h.imagehost.org/0054/kfEFpw7G.png[/IMG]

---

### Post by Dngrsone on 2010-06-22
There may be an invisible character at the beginning of the artist name, maybe a space?

---

### Post by MrSlaggers on 2010-06-24
> **Dngrsone said:**
> There may be an invisible character at the beginning of the artist name, maybe a space?

That's what I thought at first, however even when I retype it the results are the same.

---

### Post by SoFl W on 2010-06-24
There is a sort order, if you go to the song, right click, properties, the second tab should be "sorting"
This is in Rhythmbox 0.12.8, I don't remember this in my previous version although I remember something about sort order when I ripped the CD.

---

### Post by MrSlaggers on 2010-06-26
> **SoFl W said:**
> There is a sort order, if you go to the song, right click, properties, the second tab should be "sorting"
This is in Rhythmbox 0.12.8, I don't remember this in my previous version although I remember something about sort order when I ripped the CD.

Yes that seems to be the issue. I just checked and noticed that only those two albums have a number set as the order. 

I attempted to remove the number however for some reason it wouldn't let me, so I set the album order on all songs to be zero, but now it looks like it's just random sorting somewhat based off both the artist and the album. Is there a way I can simply remove the sort order since setting it to zero did not work?

---

### Post by MrSlaggers on 2010-06-30
I noticed that what it is currently doing is sorting it based off the number in the file name, for example '01 - Come Together.mp3', and then by the album name. Can someone help me make it work the way it normally should, with sorting by the album name first and then the file name?

---

### Post by MrSlaggers on 2010-07-04
Bump

---

### Post by MrSlaggers on 2010-09-01
I am still having this problem. I am unable to remove the sorting set under the song properties: 

[IMG]http://imgur.com/PvGdi.png[/IMG]

When I change it to nothing, it stays like that for about two seconds and I even see the song position change, but then it reverts back to what it was previously set as and the song goes back to where it was.

---

### Post by MrSlaggers on 2010-09-07
I was finally able to fix this issue. If anyone else comes across this problem, select all the songs in the library using Rhythymbox and set the sort fields to a space. After it is done changing all the song sort settings, closing and opening the program should make it so everything gets sorted correctly. If that is not the case, remove all the songs from your library and add them again.

---

### Post by Tornikee on 2012-04-11
I wonder what's the principle of the 'sort order' tab? If I put a number on a track, will it sort the track relative to other tracks of the album/artist/genre, or relative to all tracks in library?

---

