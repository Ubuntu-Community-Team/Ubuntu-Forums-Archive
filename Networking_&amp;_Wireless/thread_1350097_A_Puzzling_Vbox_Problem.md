---
title: "A Puzzling Vbox Problem"
date: 2009-12-09
forum: Networking &amp; Wireless
---

### Post by Babyd3k on 2009-12-09
Ok, this is a windows xp question as much as a vbox problem and if I could get it solved would have a number of handy uses. 

I want to mount networked ubuntu shares as exact files under windows. For example I want to mount the Music folder of my ubuntu install to the My Music file in my vbox install so I only need on folder set to use my MP3's in Ubuntu but still use iTunes to sync my iPod touch. 

The trick is preserving the file structure for the application that use such things. I need the music folders to be in C:\Documents and Settings\babyd\My Documents\My Music

I've tired using the net use command but it only allows for drive letter mapping. I've also had no luck using symbolic linking or generating a hard link.

Anyone have any ideas? In all the years of XP someone has to have solved this problem.

---

### Post by diablo75 on 2009-12-09
I don't know how you would setup a symbolic link of that sort in Windows.  As you mentioned, you have been able to map a vbox network share in XP which sets up the share with its own drive letter and this is automatically mounted every time you boot there after.  That being the case, you should be able to set whatever software you're using to focus on that network share as it's default folder instead of the My Music folder or whatever you're trying to use and everything should work fine, providing that you've set the proper group permissions on that folder in Ubuntu so Vbox is allowed to read and write to the folder.

---

### Post by Babyd3k on 2009-12-09
Well I already new that.

---

