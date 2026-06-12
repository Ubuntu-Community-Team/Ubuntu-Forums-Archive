---
title: "Mythmusic displays full path not song name"
date: 2009-04-29
forum: Mythbuntu
---

### Post by Drostin77 on 2009-04-29
I have installed Mythtv and mythmusic and everything is working as it ought to except for mythmusic's song names.  

Mythmusic displays the song name as the full path to the file.  I want song name to be populating from ID3 tag, and do not have it set to 'ignore ID3 tags'.  Artist & Album appear to be being populated correctly by tag, but the name (title) of songs is simply displaying as the full path of the song file, making it unreadable.  Anyone had to tackle this before or have any ideas?

p.s. Sorry for the silly question, I've managed to setup lirc etc. without a hitch, but this seemingly trivial problem is really stumping me.

---

### Post by jbman on 2009-04-30
I have this problem when the file does not have a proper tag in the file. Check the file with a mp3 file tagger to be sure.

---

### Post by Drostin77 on 2009-04-30
Thanks for the answer!  What I do know is Amarok, Songbird, and Itunes all correctly read the tags.  However, is there a more generalized mp3 file tagger that I ought to use?  I don't know of a tool specifically for this purpose but if there is one I would be happy to try it.

---

### Post by jbman on 2009-04-30
Easytag, load that up and give it a look.

---

### Post by Drostin77 on 2009-04-30
Easytag showed all tags ok.  And then i noticed that one, just one of my albums was showing titles correctly (I hadn't happened upon this one before).  All of my albums were divided into "genres" of sorts, and were in subfolders within mythmusics folder that it scanned.  The one album that worked was actually miscategorized and not in any of the genre folders.  **Taking all of the artists our of their genre folders so that the artist folders were in mythmusic's folder directly fixed the problem**... Not sure if thats a bug or user error, but either way its fixed!  And thanks for the help, somehow messing with Easytag was the way i noticed, so in a way you fixed it!

---

