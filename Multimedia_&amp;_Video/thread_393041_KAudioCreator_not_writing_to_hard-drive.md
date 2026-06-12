---
title: "KAudioCreator not writing to hard-drive"
date: 2007-03-25
forum: Multimedia &amp; Video
---

### Post by Hark3n on 2007-03-25
Small problem here.

Recently installed Kubuntu 6.10.  Today, for the first time, I thought I would give Kaudiocreator a whirl.

Insert CD, get asked what to do, download DB, choose tracks and press go.

Everything looked fine, until the first track's progress reached 100% and a pop-up appeared that said the following: "Cannot place file, unable to make directories.".

I first thought it was permission problems, so I changed the permission on the folder that it writes to.  Didn't work.

Then I tried running kaudiocreator as root.  Still no luck.

Tried searching the forums, but couldn't find anything.

Even did a search on google, but only got some obscure post on dev-mailing-lists.

If anyone knows how to fix this, please help.

Thanks,
E

---

### Post by oliwally on 2007-08-14
I've got the same problem. 

Anyone got a solution?

---

### Post by Bollinja on 2007-08-14
I just had the same problem when I first ripped with mp3/ LAME encoding. I could rip as wav files fine though, to a folder /home/<username>/wav. I noticed that there was a file in /home/<username> called 'mp3' which was a wrongly named mp3 track, so I deleted that and created a new folder /home/<username>/mp3 and it is now ripping with no problem.

---

### Post by oliwally on 2007-08-15
Bollinja, you're brilliant.

I also had the mysterious mp3 file. I deleted it, created a folder called mp3, and in the KAudioCreator settings made that folder the default......and Bingo - beautiful ripping.

Thank you for helping out.

---

### Post by antiserious on 2007-09-24
Sorry to dig up an old thread, but I'm having the same issue. I'm running UbuntuStudio 7.04 and no matter where I try to save a file using KAudioCreator, I get the 'cannot place file, unable to make directories' error. It saves the wav file, using a random gibberish name, to whatever folder I point it at, but will not create or save the mp3. I tried changing permissions on the mp3 folder, creating a new one, and creating a folder within that folder, all to no avail. Any help would be appreciated. I have no such issues with any other KDE apps, and grip works just fine, so it's not a major problem, but still it should work.
 
Thanks.

---

### Post by antiserious on 2007-10-01
I see.
 
Well, thanks for the input.

---

