---
title: "options for adding a second hdd hard drive"
date: 2008-01-12
forum: Mythbuntu
---

### Post by onesojourner on 2008-01-12
I am almost out of space on my first hdd and I would like to add a second 80 gig drive. Can I point my ''my videos'' to 2 different folders? I would also like to be able to link have it display files in a samba share on a differn't machine. is that possible?

---

### Post by newlinux on 2008-01-12
IF you are talking about files you are viewing with mythvideo, you can:

1. Have multiple directories by separating them with a colon in the setup where you specify the directory. 

2. Or you can mount the additional hard drive into a sub-directory of the current mythvideo folder

3. Or you can mount the hard drive and symlink it to a sub-directory of the current mythvideo folder

For your samba share, you can mount it to your frontend that you are viewing mythvideo files and then do option 1,2, or 3.

---

### Post by curtis1552 on 2008-01-13
I haven't done this (yet; give me 2 weeks), but I read that if you use LVM (logical volume management) you can span it across multiple HDDs. Basically you add the HDD to the existing partition.

[Link to a good LVM howto]("http://www.tldp.org/HOWTO/LVM-HOWTO/")

---

### Post by n00b@linux on 2008-01-14
Currently, LVM is the only method that allows you, simply, to add capacity to an existing install. However, setting up LVM requires a little bit of work at the command line (and some prior thought).
 
MythTV 0.21 (yet to be released) will have a new feature called "Storage Groups" that does away with the need for LVM.
 
For a quick fix/kludge, newlinux's suggestions of either:> 2. Or you can mount the additional hard drive into a sub-directory of the current mythvideo folder
 
3. Or you can mount the hard drive and symlink it to a sub-directory of the current mythvideo folderwould seem the best solution to me.  If you want to set up LVM, check out the sticky at the top of the forum.

---

### Post by onesojourner on 2008-01-14
1. Have multiple directories by separating them with a colon in the setup where you specify the directory. 

That sounds like the easiest way to go. I am going to try that. 

Lets say I have a samba share at smb://desktop/videos ,  Would I just type that in? and where would I type it in?

---

### Post by onesojourner on 2008-01-14
ok I just broke my directory to my local videos. 

on the first screen of video settings I deleted my main directory some how trying to ype in a smb share. I tried typing /var/lib/mythtv/video but all my videos are gone when I go into the video editor.

---

### Post by onesojourner on 2008-01-14
{solved] 

just a simple typo. I wrote a simple how-to for people that need help mounting a smb share.

---

### Post by purduephotog on 2008-03-26
> **onesojourner said:**
> {solved] 

just a simple typo. I wrote a simple how-to for people that need help mounting a smb share.

Wherever did you post this?  I'm about to add 1tb and a 750gb drive for movies...

---

