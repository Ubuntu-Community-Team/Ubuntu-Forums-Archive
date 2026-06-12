---
title: "Music Library Organizer"
date: 2006-11-18
forum: Multimedia &amp; Video
---

### Post by GStubbs43 on 2006-11-18
Hi all, I've been doing some searching, but I haven't really found anything.
I want a program that can take a lot of music (ogg and mp3) from a folder and use the id3 tags to create sub folders such as Genre>Artist>Album>Song
I guess I don't really know how to expain it, but, if you can help me, please do so. :D  Thanks!

P.S. I would prefer an app for GNOME.

---

### Post by snidemd on 2006-11-18
I think EasyTag is what you're looking for, its in the repositories I think, and I know it supports mp3 files, and I don't see why it wouldn't support ogg  either.

---

### Post by GStubbs43 on 2006-11-18
Yeah, I've tried Easytag, it deos support ogg, but I couldn't find a way to create folders.

---

### Post by snidemd on 2006-11-18
Have it load your music folder where your library is.  
Open the scanner window.
In the text field, enter how you want the directories formatted.  For example, if you want the path to the music to be the same and sorted by artist with the title as the filename, you would put %a/%t

If you open the scanner window, click the second icon from the right: Show/Hide Legend.  That'll show you all the variables to use in renaming your files.  Play around with it, if you click a music file in EasyTag while the scanner window is open, it will show the proposed format based on what you've typed in the text field.

Hope that helps, I've only used it to rename a bunch of mp3's, but I know it can do directories too.

---

### Post by GStubbs43 on 2006-11-18
> **snidemd said:**
> Have it load your music folder where your library is.  
Open the scanner window.
In the text field, enter how you want the directories formatted.  For example, if you want the path to the music to be the same and sorted by artist with the title as the filename, you would put %a/%t

If you open the scanner window, click the second icon from the right: Show/Hide Legend.  That'll show you all the variables to use in renaming your files.  Play around with it, if you click a music file in EasyTag while the scanner window is open, it will show the proposed format based on what you've typed in the text field.

Hope that helps, I've only used it to rename a bunch of mp3's, but I know it can do directories too.

Thanks! I'm almost there, it does work, but I could only get it to work with one file, I tried selecting all of the files, but nothing changed after I clicked save.

EDIT: I got it working! Thanks again snidemd!

---

