---
title: "Mythmusic - Scan for New music - Missing Songs"
date: 2008-11-21
forum: Mythbuntu
---

### Post by wizgnome on 2008-11-21
Hi,

I am running mythbuntu 8.10

When I scan for new songs in Mythmusic, I find that a small number of mp3 files have not been included in the library. 

If I run the scan again these songs are then added, but some other songs are missed.

For example In one album, the first scan picks up 6 out of 8 tracks. The next scan picks up only the 2 that were missed the first time.

This happens with only 64 files from a total of 5967 files and is always with the same files that I have the problem.

I have tried renaming and re-encoding the files, but this makes no difference, they are missed or included on alternate scans for new music.

Looking in the mythfrontend log, I see no errors which migth indcate a problem.

Any sugestions on what might be going wrong?

---

### Post by wizgnome on 2008-11-21
I saw that when playing some of the tracks I got an error saying the file could not be found. Looking in the mythfrontend log I noticed that the 

Artist name had lower and upper case characters. But some tracks of the Artist did not have the same capitalisation of the words in the name - eg Gare du Nord or Gare Du Nord.

This resulted in an incorrect file path. It would appear that when scanning for files if all the tracks for an artist are not capitalised the same then the database is not updated correctly.

I updated the files ID3 tags and removed the folder, scaned for new music. Put the folder back and scaned again - this fixed the problem.

---

