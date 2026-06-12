---
title: "Problems playing Divx over network share"
date: 2006-11-18
forum: Multimedia &amp; Video
---

### Post by Sarcaza on 2006-11-18
I have a linux server (with Dapper) sharing (with smb) some mpeg4 (divx & xvid) video files.  On my windows machine I can play them across the network without problems.  I have Edgy on my laptop, and although I can connect to the servers no problem (Places->Connect to Server->Windows share -> ipaddress) and can copy files without issue, when I try to play a movie in totem or MPlayer, the movie will not play.
In totem, the title of the movie is displayed in the title-bar, and "Buffering 100% 0:00/0:00" is displayed in the status bar.  The screen stays blank however.
If I copy the movie by dragging and dropping from the share-folder to the desktop, the movie plays without any problems.
I have been able to replicate this problem on a fresh-install of Edgy on a destop system (athlon XP 3000, 1gig ram).  The same system plays the movie fine when it is copied to the local harddrive, and also plays it fine across the network in Windows.

One other bit of information:
if I look at running programs, I see
"totem smb://192.168.0.2/movies/film.avi"
with Totem using about 30% of the CPU.  Also the network appears to be quite active.  After about 30 minutes, Totem still hadn't displayed any frames from the movie however.

Do Totem and MPlayer not support smb connections well?  

Anyone else have this problem or a solution?

thanks,

Sam

---

### Post by Mercurial1969 on 2006-11-18
I have a similar issue when trying to play video from a windows smb share on another PC on my network through my Ubunu machine.

Is it possible to play from a windows smb share through Ubuntu (and the player of your choice)?

---

### Post by sortia on 2006-11-18
I also have the same problem, it seems to be a known bug!

[http://bugzilla.gnome.org/show_bug.cgi?id=359133](http://bugzilla.gnome.org/show_bug.cgi?id=359133)

---

### Post by Sarcaza on 2006-11-18
So I was messing around with this a bit more last night, and found out that Kaffeine (the KDE player) works fine, it's just MPlayer, and Totem that are screwed up.  So I guess Kaffeine is (once again) my drug of choice :rolleyes: 

Sam

---

