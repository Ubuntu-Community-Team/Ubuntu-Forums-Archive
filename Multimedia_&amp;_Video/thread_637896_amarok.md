---
title: "amarok"
date: 2007-12-11
forum: Multimedia &amp; Video
---

### Post by r4wr on 2007-12-11
hello hello, i just installed amarok last night. And i am running dual boot xp/ubuntu all my music in on my win partition. SO when i go to put the music in to the player it says that it is copying it over. I dont really want have all my music on my hard drive twice. And when i add music through the player i dont know how to find the mounted drive that the music is on. im still new to the ubuntu:confused: type file system.[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

### Post by Biggus on 2007-12-11
Hey dude, I had to manually do soemthing or other when I set up my Ubuntu 6.10, but I understand that the latest version comes with built in read support for NTFS partitions.

You may have to mount your partition (on my machine I think it's 'sda1' it's called, or maybe 'sda2') to a mount point. (Again, I don't really know, I just did what a few peeps on these forums told me, and I got an icon on my desktop).

---

### Post by r4wr on 2007-12-11
yea boyo that about where i am at. my ntfs partition is already mounted so idk. just when i got to put them in they it says, it copying files over. and i dont want it to. thanks though

---

### Post by Wolfie Lee on 2007-12-11
Try this, not sure if this will fix it, it solved  a somewhat similar problem of amarok building my database from a slave ide HD (but it was on a linux install, not windows...ntsf may cause you some problems, even with this)

open terminal (applications /accssories)

sudo su

enter your login password

amarok


Opens amarok with Super User (not sure on that...SU), basically owner permisions. It goes BEYOND just opening it in terminal

hope it helps.......? (I'm a NOOB, too)

---

### Post by lil_B on 2007-12-11
When you add music folders in Amarok it shows your root file system in a tree type browser.

/
-/bin
-/boot 
-/cdrom 
... and so on

Your windows drive should be mounted in 

/media/"drivename"

drivename being the disk/partition number of your windows partition.

---

### Post by bluknight on 2007-12-11
1. Make sure that the music files are readable by you (user)

root>chown -R <user> /<music files> or chmod -R 644 /<music files>

2. Launch amarok by mouse or if you like by commandline

3. Go to setup amarok and collections. Click the directory of <music files> above

4. Click on amarok left panel the collections (or open files to playlist) and select files to play

sometimes (often) you have to download more plugins to play certain music files :guitar:
or display certain fonts of non-english music titles

HTH

---

