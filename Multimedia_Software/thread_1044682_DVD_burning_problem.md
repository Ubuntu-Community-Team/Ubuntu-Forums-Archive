---
title: "DVD burning problem"
date: 2009-01-19
forum: Multimedia Software
---

### Post by ||Z0di4C|| on 2009-01-19
Okay i downloaded a movie off of a torrent and now im left with a folder that has IFO files and VBO files how do i burn this to a disk i just want the movie to play like it was the actual movie

please help

---

### Post by stefangr1 on 2009-01-19
The DVD file structure is arranged in this way. For a video dvd you should have a VIDEO_TS folder that contains .BUP .IVO and .VOB files. If you choose the video dvd option in your burning software you can select all these files, put them in the VIDEO_TS folder, and burn.

---

### Post by ||Z0di4C|| on 2009-01-19
Okay well the videoTS folder is already there and inside of it was IFO files and VOB files so from there i just click burn and i should have what i need Cause i believe it said it was going to be like 7 gigs in which case do they make that big of DVD R discs???

---

### Post by kleptik on 2009-01-19
On the root of the DVD you should have:
AUDIO_TS
VIDEO_TS (In here is where the ifo and vobs will be)

If your dvd is over 4.7 gigs it's ripped from a duallayer dvd, in which case you need to compress the movie. I suggest dvd shrink.

---

### Post by kleptik on 2009-01-19
heh, opps, (Obvious Windows guy mistake) dvd shrink is a Windows App. Just fyi.

---

### Post by ||Z0di4C|| on 2009-01-19
dont worry im using window for this operation currently but how can you select dvd shrink

---

### Post by ||Z0di4C|| on 2009-01-19
also it has backups to each ifo and vob file does that make sense???

---

### Post by kleptik on 2009-01-19
> **||Z0di4C|| said:**
> dont worry im using window for this operation currently but how can you select dvd shrink

Try here: [http://www.dvdshrink.org/](http://www.dvdshrink.org/)

---

### Post by kleptik on 2009-01-19
> **||Z0di4C|| said:**
> also it has backups to each ifo and vob file does that make sense???

Not sure I understand but DvdShrink will recreate everything anyway. Just open your existing video_ts folder with DVD shrink and go from there.

---

### Post by ||Z0di4C|| on 2009-01-19
well i went there and unfortunately they do not support vista lol not that im surprised but now do you have an alternative idead because for sure one of the movies i have is a blueray movie and if i do shrink it will it still play like a normal dVD

---

### Post by kleptik on 2009-01-19
> **||Z0di4C|| said:**
> well i went there and unfortunately they do not support vista lol not that im surprised but now do you have an alternative idead because for sure one of the movies i have is a blueray movie and if i do shrink it will it still play like a normal dVD

Hmm. I doubt you have a valid blueray movie as that would require cracking the css which i'm not sure is in much practice lately. :) Hmm.. You can try [http://www.vcdhelp.com](http://www.vcdhelp.com) for other compression utilitiez but I HIGHLY recommend dvdshrink.

---

### Post by ||Z0di4C|| on 2009-01-19
okay so i did have one movie that was just 4.38 gigs so wat i did was i opened the video_TS folder and hit burn that all and now like it is showing all the files being burnt onto it does this mean that it is going to just be a data disc or if i pop it into a dvd player it will play the movie 

P.S. sorry im a pain but i just want to make sure i get everything right by the way also thanks

---

### Post by kleptik on 2009-01-19
> **||Z0di4C|| said:**
> okay so i did have one movie that was just 4.38 gigs so wat i did was i opened the video_TS folder and hit burn that all and now like it is showing all the files being burnt onto it does this mean that it is going to just be a data disc or if i pop it into a dvd player it will play the movie 

P.S. sorry im a pain but i just want to make sure i get everything right by the way also thanks

As stated earlier, your burned DVD should look like:

DVDDriveLetter/VIDEO_TS <-- Should contain ifo and vob files.
                   
DVDDriveLetter/AUDIO_TS <-- Empty Folder (Required for some DVD players)

Yes, the data burn format will be "Data".

:D

---

### Post by stefangr1 on 2009-01-20
Actually, dvdshrink is also the best option in Ubuntu: it runs perfectly in wine. It compresses dvd's so that they will fit on a 4.7GB disk, and then can produce an iso you can burn or a new dvd structure.

As how you should burn them: this depends on the software you're using. I use k3b, and they have a "video dvd" option, that verifies if it's indeed a movie. But you can also burn it as data.

---

### Post by ||Z0di4C|| on 2009-01-20
okay thanks i will keep that in mind now a completely different question basically i have an mp4 file and i want to put it onto a dvd and play in any player so i need a converter for that i think correct? well then does anyone have any suggestions

---

