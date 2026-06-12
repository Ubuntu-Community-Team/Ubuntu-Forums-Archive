---
title: "Can't Modify Music Info in Rhythmbox"
date: 2008-01-21
forum: Multimedia &amp; Video
---

### Post by DocHolliday2006 on 2008-01-21
Hi. II keep my MP3s in a folder on my desktop called MP3. I try to access them with Rhytmbox. I apparently don't have permission to change the file info (right click on song, click on properties, and modify stuff like artist, genre, etc) 

I've tried right clicking on my MP3 folder and trying to give myself permission to modify everything in it, but it won't save the changes. I change file access to read and write but it won't stay after I exit the window. 

How do I give myself, as a user, such permission? What's the best way to handle this? Thanks.

---

### Post by zodiacdm on 2008-01-21
let's see. i'm new at this, but open your command, and use the 'cd' command to navigate to your desktop.
cd /home/(your username)/Desktop
remember it is case sensetive. 
now type ls -l (those are L's) to print a list of all the files and folders in your current directory.
somewhere in the list, will be the folder you have your music in. try this command.
sudo chmod 770 (your directory's name)

here's a few useful tips on this subject. that's where i found this out at.

[http://us.download.nvidia.com/XFree86/Linux-x86/169.09/README/appendix-h.html](http://us.download.nvidia.com/XFree86/Linux-x86/169.09/README/appendix-h.html)

hope this helps.

zodiac

---

