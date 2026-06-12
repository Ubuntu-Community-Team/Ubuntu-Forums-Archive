---
title: "filenames to text file"
date: 2009-12-25
forum: Multimedia Software
---

### Post by marin123 on 2009-12-25
this is what i want to do.. i have a folder full of music and i want to print the names of the mp3s... is there an app that does this or can i automate this somehow (i want to select file, f2, ctrl+c, and paste in text file)...

i want to do this because i'm a dj and i want to put my music on usb stick and have the names of the songs printed on a piece of paper...

i did this by opening a playlist in gedit and deleting unnecessary text (odd rows), but that takes long time...

---

### Post by Morbius1 on 2009-12-25
In it's simplest form you could open a Terminal and issue something in the form of:

ls /path/to/music/folder > /path/to/destination/playlist.txt

So for example if I wanted to create a text file of the contents of my Documents folder I would issue:

ls /home/morbius1/Documents > /home/morbius/doclist.txt

There are many variations and different ways to do this and I'm sure you're about to get many more given the talent on this forum.

---

### Post by marin123 on 2009-12-25
nice! thanks!

i found something similar to this, but just for winblows, i was missing ls command...
tnx morbius

---

