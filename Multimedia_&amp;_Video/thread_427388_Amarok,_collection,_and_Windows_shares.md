---
title: "Amarok, collection, and Windows shares"
date: 2007-04-29
forum: Multimedia &amp; Video
---

### Post by Celadra on 2007-04-29
Hello all,

New to the forums and fairly new to Linux as well.
Most times I can find all that I need in the forums but I have a problem that I cannot find resolution to.

I'm trying to build a collection in Amarok by adding music from my Windows shares. I have 18k mp3s in 2 folders on a Windows machine that I can see, access, and play from my Feisty box. 
However, I cannot get Amarok to build a collection from them.

I've tried both the default SQLlite and the MySQL methods and I get the same result. I point Amarok to the folders and it goes through the motions of building the collection. After a while it pops up a list with "Collection Scanner could not process these files". It's not all the files, just some. Not sure how many because the list goes off the bottom of the screen and I cannot scroll it.
Anyway, then I close the list and Amarok returns to the main screen with no activity and no files added to the collection.

I'm not sure if I have the configuration wrong, if there are too many files, or if I'm just going about it all wrong.

Any suggestions are greatly appreciated.

---

### Post by Dave67 on 2007-05-08
Try this 


Create a folder in your home directory call it my music or something  like that and than copy from your 
windows share to that folder.  than point Amarok to the music folder in your home directory.  I am thinking you do not have the rights to add to the database like you are trying to do. if it is MP3 files Amarok will need to install Mp3 support for it the play MP3. Amarok should ask you if you want to install MP3 support.

---

