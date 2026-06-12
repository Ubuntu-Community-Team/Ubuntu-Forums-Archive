---
title: "foreign characters in music tags"
date: 2009-10-29
forum: Multimedia Software
---

### Post by riseringseeker on 2009-10-29
I am having some problems with mp3 tags...

I got a significant selection of songs off an iPod, but only by using it as a mass media device.  The way iPod names and puts songs in a directory is a mystery to me, but using pacpl in recursive mode was able to get them converted from m4a to mp3 and put the converted files all in their own directory in one pass.  (cool!)

Now I am trying to figure out a way to sort them by artist/album while renaming them using the tag info to replace the file names the iPod gave them (like AADE.mp3, ABWE.mp3, etc.).

The problem I am running into is that there are foreign characters in some/many of the tag fields.  I can't use the two little scripts I wrote to create the appropriate directories and rename the files due to these characters.  (An example would be M&#555;tley Cr&#470;e - M&#555;tley Cr&#470;e is *not* a legal directory name, at least not on my system).  

The scripts I wrote (pretty much my first effort at scripting) creates directories and subdirectories based on artist and title, then renames the iPodish names with the title and moves the file into the appropriate directory.  If there are no foreign characters it seems to work OK, but that still leaves me with a number of files where it does not work.

I have played a little with easytag, cowbell, and some others I have seen recommended on this and other forums.  Easytag may be the way to go, but I just can't figure out how to make it edit the tags to replace say an "Ø" with an "O", or an "è" with an "e", or eliminate a "/".

If someone has a script to replace the characters in the tags, I would love it if you would share!

Easytag seems quite powerful, but I can't figure out what it's doing, or how to make it do pretty much anything.  If you are an Easytag guru, I would love to hear from you with baby step instructions on how to do this (or anything else with easytag for that matter).  

I am not married to the idea of easytag, so if something else (preferably from the repositories) is easier to use/figure out, let me hear from you as well.

---

### Post by cipicip on 2009-10-29
See if this thread helps: [http://ubuntuforums.org/archive/index.php/t-16312.html](http://ubuntuforums.org/archive/index.php/t-16312.html)

---

### Post by riseringseeker on 2009-10-29
> **cipicip said:**
> See if this thread helps: [http://ubuntuforums.org/archive/index.php/t-16312.html](http://ubuntuforums.org/archive/index.php/t-16312.html)

Thanks for the quick reply.

That thread seems to be mainly to get songs to display properly on an iPod.  I don't even have an iPod (my wife does, but not I).  I don't have any need (yet) to make them display properly on that device.  

My question was how, if it's even possible, to edit the mp3 music tags to eliminate or replace "illegal" characters contained therein.  (Batch change, I could do changes by hand but would still be at it next year!)  IOW, change the tag "M&#555;tley Cr&#470;e" to "Motley Crue" or "Some Artist / Other Artist" to "Some Artist & Other Artist".  

I wish to do this to the tags themselves, not an external database as I understand Amaroke has for example.

---

### Post by riseringseeker on 2009-10-30
Well, given the paucity of replies it either cannot be done, or everyone is so involved in installing 9.10 that no one is available that has an answer.

sigh

---

### Post by riseringseeker on 2009-11-05
bump

---

