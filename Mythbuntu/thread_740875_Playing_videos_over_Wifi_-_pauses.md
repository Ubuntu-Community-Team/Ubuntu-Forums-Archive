---
title: "Playing videos over Wifi - pauses"
date: 2008-03-31
forum: Mythbuntu
---

### Post by DingoMD on 2008-03-31
I have just installed Mythbuntu 7.10 on a computer with a Wifi connection. I have a shared folder, on another computer, with all my videos. Mounted the folder on the Mythbuntu box (inside a folder on /var/lib/mythtv/videos) and got everything working. The problem is that while playing the videos, they "pause" every few seconds, just as if I was trying to stream a video over the Internet on a slow connection. The problem is not the bandwidth though, since I tried copying the file to the HDD of the Mythbuntu box, using the Wifi connection, and it took about 5~10 minutes to copy a video with a length of ~40 minutes. Is there any way to have MPlayer (which, I think, is what Mythvideo uses) buffer a few minutes of the video ahead?

BTW, the videos on the HDD or external drive play just fine.

---

### Post by nasha on 2008-03-31
An 802.11g wireless connection does not have enough bandwidth to stream video reliably at any distance greater than right next to the AP.
I suggest a cabled option, for a number of obvious reasons

---

### Post by rhpot1991 on 2008-03-31
Are you perhaps running MythTV 0.21?  I had problems going from 0.20.2 to 0.21 with my wifi, had skipping every few seconds (and audio buffer errors in the frontend logs).  Reducing the bitrate of my recordings helped a lot.  Another thing that seemed to help was sharing the recordings out over a NFS share instead of letting MythTV do the sharing.  I finally worked it out by getting rid of my crap wifi cards and using a openwrt router as my wifi client instead.  So you might want to try a different card, check your signal, try a different channel and so on.

---

### Post by DingoMD on 2008-03-31
But I'm trying to play XviD encoded files. Thats no more than 1~2 Mbits/s. Shouldn't my Wifi be able to handle that? :confused:

---

### Post by nasha on 2008-03-31
Reliability is the issue. This is shown in the problem your experiencing, it jitters every few seconds, which means most of its making it thru, but some packets are getting lost, as happens with wireless communications, more so than cabled solutions

---

### Post by DingoMD on 2008-03-31
Just found out how to solve it. Just had to add "cache = 8192" and "cache-min = 4.0" to ~/-mplayer/config
Works perfectly now :D
Thanks everyone for the replies.

---

