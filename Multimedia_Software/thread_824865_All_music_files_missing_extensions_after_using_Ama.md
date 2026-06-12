---
title: "All music files missing extensions after using Amarok to organize"
date: 2008-06-10
forum: Multimedia Software
---

### Post by sgfaulkner on 2008-06-10
I decided to use Amarok's music organization function to organize my library.  For some odd reason I thought to make a custom file format to rename everything, but I forgot to append the file type to the end.  Now I have about 120 GB of music in FLAC and MP3 format that have no file extensions.  None of the music players I have tried (Exaile, Rythmbox, Amarok) or ID3 tagging programs recognize any of them.  For some reason Nautilus still does because they are all displayed with a music icon and play in totem when I double click them.  Any recommendations of how to fix this without renaming them all by hand!?

---

### Post by pelago on 2008-08-08
I have a similar problem (a load of music files, some mp3, some wma, with no extension). Again, Nautilus recognises them as mp3 or WMA (which is actually labels as ASF video), but most music players won't recognise them without the extension.

Is there a program, probably command-line, to rename files to the 'correct' extension, based on the same magic that Nautilus is using to detect the file type?

---

### Post by pelago on 2008-08-08
I've been looking at bulk renamers. pyRenamer is useful if you want to rename all files in recursive sub-directories to, e.g., *.mp3. krename, however, was more useful for me with my mix of files, as I could sort by file-type in Nautilus and just drag the mp3s to krename for renaming, which I couldn't do in pyRenamer. It takes several passes to do all folders and all file types manually, though.

It would still be great if there was a program that would rename based on the file 'magic'.

---

