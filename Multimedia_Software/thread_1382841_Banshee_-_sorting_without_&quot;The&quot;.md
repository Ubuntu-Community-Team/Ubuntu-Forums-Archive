---
title: "Banshee - sorting without &quot;The&quot;?"
date: 2010-01-16
forum: Multimedia Software
---

### Post by aquascrotum on 2010-01-16
Simple query - is it possible to get Banshee to ignore "The" when sorting tracks by band name?

---

### Post by boombox1387 on 2010-01-21
Yes, but it might be a painful process.

First of all, what version of Banshee are you using?  I forget which version added support for the "Sort Artist" tag, but I know it's at least in 1.5.1 which shipped with Ubuntu Karmic.

What you need to do to get Banshee to ignore the 'the' is right click on  track in your Banshee library that has an artists starting with 'the', open up 'Edit Track Information', click on the third tab (titled 'Sorting'), and add information to the "Sort Artist" field.  For example, for 'The Decemberists', the sort artist is 'Decemberists, The'.  Visually it still shows up as The Decemberists in the library, but Banshee sorts it under 'D' instead of 'T'.

Adding this information can take a long time if you have a lot of music, and so far there is no automated way to do it.  Hope this helps a little, though.

---

### Post by aquascrotum on 2010-01-22
Thanks for this info - nice to know theres a way to do it but it sounds like just too much of a pain in the *** at this stage.

Hopefully its automated as an option in future Banshee releases.

---

### Post by sdc444 on 2011-05-01
Good news on the process is that if you have multiple songs from the same "the" artist, editing one song's sorting mechanism edits it for all songs by the same artist (Doing the process for Help! does it for Yesterday and Eleanor Rigby and ...)

---

