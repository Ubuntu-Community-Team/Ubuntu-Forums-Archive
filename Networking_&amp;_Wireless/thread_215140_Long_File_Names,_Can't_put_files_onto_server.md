---
title: "Long File Names, Can't put files onto server"
date: 2006-07-13
forum: Networking &amp; Wireless
---

### Post by Big_MARK on 2006-07-13
I am using DD for a file server here in my art dept. The problem I am having is file name and characters in the file names. Seems like some file names are to long for DD to allow them to be put onto the server.

I'm using Mac OS X.4.7 and want to store all my fonts (some are Kanji and seem to cause this error) as well as a PDF libray of wich some file names get lengthy and might have characters like "#", "&", "%", etc....


Is there something software wise that I can do, add to DD to allow me to put files with the offending characters and long file names on it?

](*,) ](*,) ](*,)

---

### Post by T700 on 2006-07-13
The limit is 256 characters, exclusive of file path.  See [this link]("http://www.tuxfiles.org/linuxhelp/weirdchars.html") for details on special characters and how to handle them.

Paul

---

### Post by Big_MARK on 2006-07-13
Thanks for the info, however your link explains about comand line functionality, I'm dragging and dropping files to the Server from the Mac.

How do I handle that issue, must be a character name issue (the "/" most likely, See attached Error window). Short of hunting down al the erroneous file names is there a way I can overrid the Linux box or add to it's file handling capabilities so I can drag and drop without getting errors like this?

I have 4000+ font files that I am moving so sifting through them to change the names is really out of the question.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=12690&d=1152818782[/IMG]

---

### Post by Big_MARK on 2006-07-14
BTT


Anybody have an idea how to work around this issue?

Or are certain caractes just unusable in file names?

Seems like this might just be a downside with the way Linux handles files.

---

### Post by Big_MARK on 2006-07-14
Interestingly enough I solved the problem. 

I was trying to copy the files TO the Linux server FROM the Apple Computer (from the Apple GUI) and got the error.

When I copied the files FROM the Apple computer TO the Linux (from the Linux GUI) server I had no errors. Weird.

Now I will see if I can use the fonts...that is another story though...


Thanks for the help. :KS

---

