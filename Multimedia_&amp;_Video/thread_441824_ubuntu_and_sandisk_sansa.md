---
title: "ubuntu and sandisk sansa"
date: 2007-05-13
forum: Multimedia &amp; Video
---

### Post by helane on 2007-05-13
Hello,

Have SanDisk Sansa c140. I switched to Ubuntu and I am happy but... I got my Sansa mp3 player working on Ubuntu - any new files i transfer I can play etc. 

The problem: Had some mp3 files on my mp3 player (moved to player from Windows) before and my computer doesn't see them - so half of my player space is unusable because I cannot see = cannot delete...


Please give me some advice.

---

### Post by beefbowel on 2007-11-12
is deleting it possible?  i have the same problem.  i need fresh music in my player.  thank you for your help.  :guitar:

---

### Post by beefbowel on 2007-11-13
i finally got it to work.  i used amarok.  

1  go into usb setting and set to auto detect in the c140
2  connect to computer and run amarok.  or run amarok and connect to computer.  
3  go to configure amarok and if the sansa is not listed under portable media devices then add it.  select 
   mtp and name it sansa.
4  it should list the songs that are on your device.  then delete all of them.  make sure after you are         done to hit disconnect on the amarok window before you physically disconnect the device.  

you might have to fiddle around with it a couple of times.  it is pretty buggy and fragile.  not really sure what is doing what.  it is like practicing voodoo.  good luck with your prob.

---

### Post by peeple on 2008-04-11
Hey, I had the same problem but figured it out.

ALOT easier than the above solution.

I tried to view the hidden files in nautilus but couldnt.
ran across the .<foldername> folders when i ran some cleanup program in rockbox

then I tried ls

```
user@user-desktop:~$ [COLOR="Red"]sudo ls /media/SANSA\ E280/ -a[/COLOR]
.   Files  PHOTO     PLAYLISTS	.rockbox  tmp	       version.sdk  VIDEO
..  MUSIC  PICTURES  RECORD	SYSTEM	  .Trash-1000  VERSION.TXT

```

Then I just typed in /me~tab/SA~tab/.T~tab and it gave me: /media/SANSA E280/.Trash-1000

of course ~tab are physical tabs to autocomplete the dir

I haven't yet checked to see if the files deleted will give me all my space back but its a step.

Good luck! and hooray for rockbox :biggrin:

---

### Post by DavidONE on 2008-07-15
This might help: [http://www.howtoforge.com/sandisk_mp3_player_linux](http://www.howtoforge.com/sandisk_mp3_player_linux)

---

