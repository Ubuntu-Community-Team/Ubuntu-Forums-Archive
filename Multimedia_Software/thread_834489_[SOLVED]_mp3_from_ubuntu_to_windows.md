---
title: "[SOLVED] mp3 from ubuntu to windows"
date: 2008-06-19
forum: Multimedia Software
---

### Post by oknos on 2008-06-19
is there anyway to get mp3 files from ubuntu to play in windows????

any help appreciated.

---

### Post by cozmicharlie on 2008-06-19
> **oknos said:**
> is there anyway to get mp3 files from ubuntu to play in windows????

any help appreciated.

Not sure what you mean "from Ubuntu" but any mp3 should play fine on both.  What are you trying to do specifically?

---

### Post by present_arms on 2008-06-19
That depends on whether you installed Ubuntu on a separate partition ot youy used wubi to install within windows and also if you used ext3 on a separate part. if you did the latter the get Ext2IFS_1_11.exe for windows. it's an ext2/3 driver so u can read/write to linux ext2/3 partitions.


i hope this helps

Alie

---

### Post by aysiu on 2008-06-19
Make sure you have Windows Media Player, Quicktime, or VLC installed and then double-click them?

---

### Post by oknos on 2008-06-20
i guess i wasn't very clear on what i ment.
the problem i 'm facing is this:
 
i want to transport some mp3 files from my pc(i 'm using ubuntu) to my friend's (he is using windows) via usb flash. but the files i stored in the usb stick from ubuntu don't show up at all when i try to get them to play  in windows.:confused:

if that is any clearer please try to help.

---

### Post by ad_267 on 2008-06-20
How is the usb drive formatted? Does the drive actually show up when you connect it? Can you see other files and not the mp3s?

---

### Post by oknos on 2008-06-20
usb drive works just fine. i have this problem with any storage media i 'm trying to use.

---

### Post by oknos on 2008-06-20
problem solved and the cause was... my stupidity:oops:

thanks for trying to help out though, appreciated!

---

### Post by cozmicharlie on 2008-06-20
> **oknos said:**
> usb drive works just fine. i have this problem with any storage media i 'm trying to use.

OK lets see if we can summarize what is going on and try a a few things.  This should not be any problem to do.  Any mp3 you add to a usb stick should play on Windows or Ubuntu as long as both can access the disk.  

[LIST=1]
[*]You have an mymusic.mp3 (it does have the .mp3 extension correct?) file on a standard usb stick (formatted as fat32 or ????).  What format is it?  If you don't know right click on the usb disk icon and go to properties.  
[*]The Windows and Ubuntu can both access the usb stick, correct?
[*]Have you tried this with other mymusic.mp3 files?  What about other types of files?  If you add another type of file to the stick from Ubuntu does it show up in Windows?
[*]If you have an mymusic.mp3 on the windows and transfer to Ubuntu, can you access it?
[*]Where did the mp3 file originate from?  Is it something you downloaded from itunes or another service?
[*]If you right click and go to properties what is the file type shown on the mymusic.mp3 file?
[*]What are the permissions on the file - are they owned by user or root?
[/LIST]

---

### Post by cozmicharlie on 2008-06-20
OK - so what was the problem - come on fess up!  I don't ask to embarrass you but if it happened to you, most likely it will happen to someone else and your solution may help them.

---

### Post by multisimple on 2008-06-20
> **cozmicharlie said:**
> OK - so what was the problem - come on fess up!  I don't ask to embarrass you but if it happened to you, most likely it will happen to someone else and your solution may help them.

he's right, please post solution

---

