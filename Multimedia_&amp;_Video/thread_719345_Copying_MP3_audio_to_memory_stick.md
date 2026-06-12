---
title: "Copying MP3 audio to memory stick"
date: 2008-03-09
forum: Multimedia &amp; Video
---

### Post by ajpearson on 2008-03-09
While copying MP3 files from my external folder to my memory stick I exprience a problem with about 1 in every 15 tracks or so - I get the following error message "invalid parameters while copying media files".

I have tried copying separately and I still get the error. All the MP3 files were created in the same way.

Any help appreciated!

Thanks
Andrew

---

### Post by pbpersson on 2008-03-09
When you say you are copying them.....are you just using Dolphin or Konqueror to drag and drop the files as data files?  For instance, using a USB flash drive?

If so......I don't understand why it would care if they are media files.....they should just be plain data files from the OS point of view.

This only happens with some files but others work fine?  Does it depend upon the size of the file perhaps?

---

### Post by ajpearson on 2008-03-09
I have the MP3 files in my external drive and copy (right click) or drag and drop to my memory stick/pen drive. I am not using any program (e.g. Dolphin) to do this.

I have just tried again - and it has worked with the track it error'd on earlier, but it is not working with others.

Thanks for your help - any further suggestions?

Thanks


Andrew

---

### Post by Giradman on 2008-03-09
**Andrew** - first, I'm assuming that these MP3 files are all valid & have played properly?  If so, you might want to provide some additional information that might help:  1) what is the disk format of the external hard drive, i.e. NTFS or FAT32 (usually a USB stick is FAT32); and 2) you might want to post the exact 'names' of a few files that have copied OK & several that have produced the error - maybe by examining the names, others can provide some suggestions?  

Finally - have you tried to change (and shortened/simplified) the names of the problem files to see if that might make a difference?  Good luck - :)

---

### Post by sekinto on 2008-03-09
Look for things like "." and "/" and "\" in the filenames.
Tell us what file system the drive is using (NTFS, FAT16, FAT32, et cetera).
Also find a file that won't copy and try copying it using the command line and give us the output message.
The command line command is "cp (file) (destination)".

---

### Post by Tarmael on 2008-03-09
Remembering that you can't have quotation marks, commers, question marks, '*', slashes and other symbols because they all have use in the command line and so are not allowed in the names of files so therefore cannot contain them. Why then look for them if you KNOW they are not going to be there?

---

### Post by tgalati4 on 2008-03-09
Try copying one troublesome file using the command line.  Any errors will show up immediately.

For example:

>cp /Music/myfavoritesong.mp3 /media/sonymemorystick

Post your errors.

---

