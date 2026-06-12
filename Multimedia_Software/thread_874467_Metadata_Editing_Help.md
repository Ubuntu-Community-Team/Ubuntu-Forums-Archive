---
title: "Metadata Editing Help"
date: 2008-07-30
forum: Multimedia Software
---

### Post by markclewis1 on 2008-07-30
Need some help.

Context:  Organizing my music library by genre tag in genres that make sense to me so that I can load my I-pod by genre when in the mood.  Library is made up of a mix of mp3 and m4a files from various sources.

Player:  Prefer Amarok, have used Rhythmbox and Banshee

Editing:  I have tried editing through all 3 players, in Windows through I-Tunes, etc.  Neither Amarok nor Rhythmbox will change the genre on some of the files, some they will (m4a obviously won't but I expected that).  Tried Ex-Falso, and it changes all very well.  Great editor.

The Problem: The tags aren't always changed!  They will show up in Ex-Falso as the one I changed them to, but then when the files are loaded into Rhythmbox, they are still the same.  In Amarok, they may be same or different.  Amazingly, I can go out to Windows and check them through I-Tunes and they will be changed appropriately as I had changed them in Ex-Falso.  What is going on with the consistency???

Example: Black Flag - Damaged, the original tag came through as 'Rock'.  I changed it to 'Hardcore'.  Load into Rhythmbox, and it shows up as 'Rock', load into Amarok and it loads as 'Punk' (and cannot be edited by either program).  Jump to Windows, and it shows up in I-Tunes as 'Hardcore'.  Go back to Ex-Falso, and it is still listed as 'Hardcore'.

Please help me understand what is going on and if someone knows of a better solution than Ex-Falso for editing that will actually recognize the changes made to the metadata, that would be great!!

Thanks,

M

---

### Post by satellite360 on 2009-01-21
You can reset your collection in Amarok, then when it rescans your collection it should pick up the new tags. See this quick guide:
[http://amarok.kde.org/wiki/Resetting_collection_HowTo](http://amarok.kde.org/wiki/Resetting_collection_HowTo)

Basically you just need to quit Amarok, rename /home/YOUR-USER-NAME/.kde/share/config/amarokrc then when you restart Amarok the first-time wizard runs.

I use Banshee to edit tags, EasyTAG is also pretty good - both allow editing of m4a files.

---

