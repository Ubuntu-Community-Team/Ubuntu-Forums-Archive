---
title: "Easytag Question Concerning Renaming of Directories"
date: 2007-01-21
forum: Multimedia &amp; Video
---

### Post by wounded on 2007-01-21
I've spent the last day tagging and renaming my music on my computer which seems to be about 8000 songs. I've really loved Easytag and its ability to fill int ags based on file names and rename files and so forth. The only thing that frustrates me at this point is that it does not seem possible to rename multiple folders at once. 

For instance I have it setup so that the structure looks like ~/music/[band]/[album] 

Even if I couldn't mass rename every album folder at once (Seeing as how they are all subdirectories of diferent folders fo the individual bands) I would atleast like to be able to rename all of the folders of one artist at a time if possible. 

However, poking through the easytag menues and dialogs and googling leads me to believe that this connat be done or I am very stupid and the only person who has ever needed help doing this. haha. Possible?

---

### Post by Fisslefink on 2008-05-19
Took me a while to figure this out too.  In the "rename file and directoires' scanner, add the folder path beginning with a slash ('/') before the masks for the file name. Customize the band/album paths by adding the tags as needed.

For example, you could put in the scanner box:
~/music/%a/%b/%n - %a - %t
...which would give you something like:
~/music/Arctic Monkeys/Favourite Worst Nightmare/01 - Arctic Monkeys - Brianstorm.mp3


  Also, make sure the folder that contains the folders you want to rename (in your case, "music") is writeable by the current user.

---

