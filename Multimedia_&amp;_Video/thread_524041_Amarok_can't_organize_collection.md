---
title: "Amarok can't organize collection"
date: 2007-08-12
forum: Multimedia &amp; Video
---

### Post by qiemem on 2007-08-12
Whenever I try to organize my music files with Amarok (right click->manage files->organize files), it says "Sorry, ## files could not be organized".  This is true of all my music files.  Of course, my first thought was permissions, so I ran:
```
chmod -R +rwx
```
on my music directory, but to no avail.

Any ideas?

---

### Post by mrsticks on 2007-09-17
I have the same exact problem.  My music is located on another partition, but I think I have the permissions correct:

```
drwxrwxrwx  3 root plugdev  131072 2007-09-05 16:19 songs
```

My user is a member of the plugdev group, all the files within the songs directory have these permissions...  As much as I dont like 777, I thought it would fix the issue.  My user can go in through the file browser and create new folders and move stuff around, and amarok runs as my user, so what gives?

Any ideas?

Thanks 

-peter

---

### Post by jveezy on 2007-12-03
I just found this thread through a google search while looking for the same problem.

Turns out I've managed to fix it and it's pretty simple.

For some reason chmod on the folder will only change the folder itself. All the music in the folder is still under read permissions only. 


Just navigate to your music folder using the file browser.

Then hit Ctrl+A to select all the files in the folder.

Right click ---> Properties

Permissions Tab

Change permissions to your desired values. I changed everything to read and write because nobody else touches my computer so I don't really care what happens.

Now Amarok can update your tags. Enjoy. It's so much easier than having to use an external program to organize everything.

---

### Post by bobradu on 2008-03-30
Unfortunately, I still have this same problem.  My music is under a folder on my main Ubuntu partition (/public/Music) and the owner is my username (hbob) along with the group (hbob, to which user hbob belongs).  All files share this exact owner scheme as well.  In addition, All files (and the folder) have rwxrwxrwx permissions (just trying to get it to work).  All files are mp3's and no file can be organized.

Amarok is version 1.4.7 ( using KDE 3.5.8 ).  I am using AMD64.

---

