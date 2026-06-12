---
title: "Advice regarding ID Tags plaease"
date: 2007-05-04
forum: Multimedia &amp; Video
---

### Post by Roger_Melly on 2007-05-04
I am the happy recipient of a Sandisk e280 MP3 player.  I can drag and drop MP3 files to it.  Sadly it only identifies a particular type of ID tags.  The tracks are there and play as songs but are not catagorised on the machine by artist or album.

I am currently extracting MP3's with sound juicer and generally stick to Rhythmbox.  I have many types of ID tag utilities and can work the less complicated ones.

Q1 How do I tell what ID tag format my files are in?  This will allow me to compare those that can be seen and those that can't.

Q2 How can I change a block of tags (say a whole album) whilst deleting any older tag format?

Q3, can you recommend and perhaps point to a guide to the most efficient tagger.  I have easytag and another complicated one but haven't a clue how to go about using them!

Cheers

---

### Post by adamadamant on 2007-05-04
Hi, I have a Sansa m240 and had exactly the problem. I use easyTag which is prety good for bulk renaming, and you can even search the net for album details. I found that when you load up the types of files that the sandisk dosen't like in easyTag (you just navigate to the dierectory by the left panel) they appear without tags here too. Although it's a bit of a pain I had to fill the tags for everything (though you can use the CDDB search and scan files options to make it quicker). I don't know if there is an easier way.

---

### Post by aysiu on 2007-05-04
TagTool has a pretty easy-to-use interface.

---

### Post by Roger_Melly on 2007-05-04
Thanks guys,

I have found a Sansa beginners guide here in the forums and I'm going to have a go with Easytag.

Everything would be so much easier if we had a decent CD extractor that uses ID3v2 Tags!

---

### Post by ntetreau on 2007-05-07
Hi Roger_Melly,
Soudjuicer does add the ID3v2 tag to the files I rip.  Perhaps yours is not setup optimally?  Once you have installed these packages:

sudo apt-get install gstreamer0.10-bad-multiverse gstreamer0.10-ugly-multiverse lame 

you should be able to choose the MP3 profile in Soundjuicer and Rhythmbox preferences.  When I rip using this MP3 profile, my files are all tagged automatically.  Hope it helps

Nic

---

### Post by Roger_Melly on 2007-05-07
ntetreau,
I think it has something to do with the ID3 version Soundjuicer uses 3.2.4 and other stuff uses 3.2.3 (or something like that!)

---

### Post by ntetreau on 2007-05-09
I am under Feisty which uses 3.8.4 if that's what you mean.  Do you mean that other program, using the verson 3.8.3 would not be able to read the tags?  That's doubtful.

---

### Post by Roger_Melly on 2007-05-12
I have read somewhere that SJ uses ID3v2.4 or something similar as opposed to ID3v2?

---

