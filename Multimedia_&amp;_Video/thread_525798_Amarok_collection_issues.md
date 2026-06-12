---
title: "Amarok collection issues"
date: 2007-08-14
forum: Multimedia &amp; Video
---

### Post by Stochastic on 2007-08-14
Hi, I recently installed ubuntustudio and copied my /home files over to the new install.  Nearly everything worked perfectly for the transition but I've noticed a couple bugs here and there.  One of the main ones is with the Amarok collection

I've got Amarok setup with SQLite to take only from my one folder of mp3/ogg files.  Currently Amarok claims that the collection is 6277 tracks large but gnome's file browser sees a total of 5336 files within that folder and its subfolders (4562 in the main folder and the rest in subfolders).  That means that every 6th song or so Amarok is imagining and runs into a "Local file does not exist" error and stops when it's on random play.

Any ideas on how to get rid of the imaginary files (they may be old files that have since been deleted from the folder but the database file is not updated).  I have rescaned and updated the collection, and reloaded the playlist a number of times.  What else can I try?  I don't want to loose the play count or song score info.  Thanks.

---

### Post by aysiu on 2007-08-14
I would rename the ~/.kde/share/apps/amarok folder, relaunch AmaroK, and then try to find what file has all the ratings and play counts and move that over... unless, of course, that's the same file that has the list of imaginary songs...

---

