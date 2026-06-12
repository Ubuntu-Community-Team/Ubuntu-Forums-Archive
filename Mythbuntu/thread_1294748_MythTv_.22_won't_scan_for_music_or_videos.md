---
title: "MythTv .22 won't scan for music or videos"
date: 2009-10-18
forum: Mythbuntu
---

### Post by GuiGuy on 2009-10-18
Using Karmic Beta MythBuntu.

Has something changed with scanning for music & videos to load the database?

Utilities/ Setup > Video Manager  returns "No Files Found"

In my case nothing's returned when I ran a scan on valid read/write enabled paths and files.

TIA

---

### Post by tgm4883 on 2009-10-18
> **GuiGuy said:**
> Using Karmic Beta MythBuntu.

Has something changed with scanning for music & videos to load the database?

Utilities/ Setup > Video Manager  returns "No Files Found"

In my case nothing's returned when I ran a scan on valid read/write enabled paths and files.

TIA

Scanning should be the same. Did you check your video paths? default should be /var/lib/mythtv/videos and /var/lib/mythtv/music

---

### Post by GuiGuy on 2009-10-18
> **tgm4883 said:**
> Scanning should be the same. Did you check your video paths? default should be /var/lib/mythtv/videos and /var/lib/mythtv/music

Yes. All paths are correct and permissions are adequate. As a long time MythTV user I am really stumped on this. Might have to post to the mythtv users list :confused:

PS: I don't see anything in the logs to help me either

---

### Post by map7 on 2009-10-18
I noticed that when I went into Video Manager I had to now hit 'm' and then select update collection for it to scan.

---

### Post by GuiGuy on 2009-10-18
> **map7 said:**
> I noticed that when I went into Video Manager I had to now hit 'm' and then select update collection for it to scan.

doh!! Well that's a "gotcha", right?

Many thanks.

NB: While that's fixed the video scan, music won't. Scan that its. Also, Vidoe Scan seems to hang if it's looking across the network.

---

### Post by tgm4883 on 2009-10-19
> **GuiGuy said:**
> doh!! Well that's a "gotcha", right?

Many thanks.

NB: While that's fixed the video scan, music won't. Scan that its. Also, Vidoe Scan seems to hang if it's looking across the network.

Why would video scans be looking across the network? Unless it's ISO's, you should be using Storage groups for that.

---

### Post by fenian on 2009-10-21
> **tgm4883 said:**
> Why would video scans be looking across the network? Unless it's ISO's, you should be using Storage groups for that.

My guess is that the OP is on a frontend trying to scan libraries on a seperate backend and that the frontend is using a different mysql database.
To fix this on the frontend open a terminal and enter...

sudo dpkg-reconfigure mythtv-common

When promted for the adress use the ip address of the backend (192.168.x.xxx)  not 127.0.0 (localhost).

database and user keep the same (mythconverg & mythtv)

password should be that of the backend (If you don't know it you can find it on the backend in the file /etc/mythtv/mysql.txt)

This will ensure that the frontend will use the mysql database on the backend and use the directories set up in storage groups.

---

### Post by GuiGuy on 2009-10-22
> **fenian said:**
> My guess is that the OP is on a frontend trying to scan libraries on a seperate backend and that the frontend is using a different mysql database.
To fix this on the frontend open a terminal and enter...

sudo dpkg-reconfigure mythtv-common

Thanks for the reply. I understand all you wrote and did as much before hand. The issue remains that I can only enter one path name in the list of path names for the music libraries. I'll live with it for now and will see what the final release of myth does. 

Cheers

---

### Post by fenian on 2009-10-22
> **GuiGuy said:**
> Thanks for the reply. I understand all you wrote and did as much before hand. The issue remains that I can only enter one path name in the list of path names for the music libraries. I'll live with it for now and will see what the final release of myth does. 

Cheers


Can you create symlinks within the directory you specified to the other directories you want to access?

---

### Post by GuiGuy on 2009-10-22
> **fenian said:**
> Can you create symlinks within the directory you specified to the other directories you want to access?

I didn't think of that! Thanks again. That should do it. 

Cheers

---

