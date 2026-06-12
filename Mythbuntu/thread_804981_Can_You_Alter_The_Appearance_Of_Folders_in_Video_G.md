---
title: "Can You Alter The Appearance Of Folders in Video Gallery"
date: 2008-05-23
forum: Mythbuntu
---

### Post by ab1301 on 2008-05-23
I have a bunch of movies with extra content in separate files, as well as tv show dvds with many episodes in separate files.  In order to make browsing the video gallery easier, I put each movie with its extras, and all the episodes of a particular tv show, in separate folders in the main video folder.  (e.g. one folder for Arrested Development, and one folder for Superbad, its deleted scenes and blooper reel.)

The problem with this is that folders in the gallery are displayed differently than files.  The worst part of this is that the folders have no posters attached to them.  Its very annoying having a nice gallery with posters for every movie, then having to see blank folder icons for the tv shows, and the movies with extra features.  In addition, all the folders are listed before any of the files, so that the gallery is no longer in proper alphabetical order.

Is there any way that I can attach metadata and posters to the folders so that they look just like files in the gallery?  Also, is there a way to make the folders in the gallery "mix" with the files, so that everything is in alphabetical order?

---

### Post by frego on 2008-05-23
Back when I was on Mythtv 0.19, I had a bunch of videos that I wanted to have all one picture. ie. multiple episodes of the same TV show.  What I did was copy the cover art to:
/myth/video/.covers

And I gave each picture a unique name. Then, I executed sql statements such as:
UPDATE videometadata set coverfile="/myth/video/.covers/Andy_Griffith.jpg" where title like "%Griffith%";

UPDATE videometadata set coverfile="/myth/video/.covers/SCTV.jpg" where filename like "%SCTV%";

I believe there's a way of doing the same one at a time from within the video manager, but it got tedious when you have lots of shows, so I just forced them into the database.  I would highly recommend backing up your database before you do any of the above operations.  You might find a front end such as webmin useful for executing the sql statements.  Also, I'm not sure if the tables are the same for your version of myth, so beware!  Anytime you force a change in the database, you might hose it!!

As far as the ordering of the listing... I've worked around this by putting everything in a folder, such that all the movies are in a folder called "Movies", while TV episodes are broken down alphabetically so I don't have to do a bunch of scrolling.  ie.  "A-C", "D-F", etc.  so I will have a subdirectories under that, in the form: /A-C/Arrested_Development/AD-1

---

### Post by toorima on 2008-05-23
If you put an image inside the folder and name it folder.jpg it will show on the folder.

To get info like movies get from imdb there is a script that will do that for you and also take a screenshot from the file and use instead of the blank.
[http://idisk.mac.com/r.mcnamara-Public?view=web](http://idisk.mac.com/r.mcnamara-Public?view=web) (link won't work with firefox3)

---

### Post by difosfor on 2008-05-24
Exactly the same problem here, thanks for the suggestions. I wish I could just configure MythVideo not to sort directories separately  from files and show the first image found in a (sub)directory as the image for that directory. Perhaps we could make a feature request?

---

### Post by frego on 2008-05-25
That would be a great feature request!

---

