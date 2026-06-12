---
title: "File Server ?'s"
date: 2006-06-25
forum: Networking &amp; Wireless
---

### Post by JLD on 2006-06-25
Ok, sorry to bother you kind folks.

I have two machines (...well more but for the sake of this problem I have two). One will be a server. I want this server to be a:

1. File server: to swap random crap and store random crap.
2. Router: I already have this one figured out (using Webmin).
3. Fire wall: I haven't really begain to look for this, heck for all I know Webmin may have that option, but if yo could shoot a hand link on a goo firewall that would be great.

So on this server I have two hard drives... A 60gb and a 200gb. I want to have the 200gb to be all shared stuff. and the 60 to be all not shared stuff! the 60 has the OS on it, but when I go into the system>admin>disks I cant format it. Thats may first question, How do I format that thing. Here I'll put it in bold for easy reference: **How Do I Format My 200gb Drive?**

Alright, sencond question! How do I share that Drive so windows and linux can see it? One of the reasons I want this is to dump all the stuff I have on my gaming PC (Music/movies/the like) over so when I reformat, WAbam, its right there on the server. I'm going to be  duel booting as soon as I get this server up and running on my gaming rig since I have fallin in love with ubuntu. So the second question again: **How Do I Share That Drive?**

and lastly, have any of you been able to play CS:S on ubuntu without to much performance loss? I've read about programs like Wine. Have you had any luck ith them?

Thank in advance,
Josh

---

### Post by darkninja on 2006-06-25
Have you tried using system>admin>Gnome Partition Editor to format the disks? That should do it.

Also the easiest way to share the disk over a network would be to mount it wherever and share the mounted folder with system>admin>shared folders, Install Samba when it prompts you and set all the relevent options.

If you wanted to share the disk between Ubuntu and Windows on the same machine one option would be to install a large Windows partition using FAT32 instead of NTFS or install a small Windows partition and create a large ext3 Linux partition and use this Windows driver [http://www.fs-driver.org/](http://www.fs-driver.org/)

I haven't had any experiences with CS:S in Wine so I can't help you much there.

---

### Post by JLD on 2006-06-26
Thank you dark ninja!

I was able to get the hard drive working with Gpart...I have to install it. But now when I try to share it it doesnt work yet. When I did: system>admin>shared folders it never promted for an install of samba, I had it installed before, but I unintalled it to make sure. Anyways I'm still stuck not being able to share tis folder.

---

