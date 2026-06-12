---
title: "Video are listed multiple times"
date: 2011-04-28
forum: Mythbuntu
---

### Post by jdk82 on 2011-04-28
Hi all,

I have an odd problem with mythvideo. Some videos show up normally, some show up two or three times. I've searched and found others with this problem, but there were no responses to the threads. I have two frontends, one newish and one that has been up for more than a year. The new frontend has always had this problem, the old one just started exhibiting it when I changed the filenames to strip extraneous info (year, etc) that I put in when ripping them. In a collection of > 200 movies it shows up maybe 1 out of 10 times on the old frontend, 2 or 3 out of 10 times on the new frontend. The backend is running 10.04 with updates to mythtv .24, using storage groups. Both of the frontends are running 10.10 with updates to mythtv .24. Additionally, many (although not all) of my file name changes on the backend aren't reflected on the frontends. Any ideas?

Edit: I just noticed that if I browse the videos section of mythweb on the backend it shows duplicates of the same movies as my old frontend (room mate isn't home so I can't get into his room to verify if they are the same duplicates on his). Is there a way to rebuild the database on the backend?

Edit: Also just noticed that "file browse" mode does not exhibit this behaviour, disabling file browse mode does. All of these videos are sitting in the video root directory (one of the changes I just made) instead of in folders.

---

### Post by phroman on 2011-04-28
I had this problem too.  Videos titles would show up multiple times, a file would be listed with the wrong title and given even another coverart pic, how does that happen.. all kinds of wierdness.  

I never used storage groups before today but doing so seems to have fixed this.  Hope this helps.

---

### Post by jdk82 on 2011-04-29
Thanks for your reply, I also use storage groups (it's kinda buried in my long post) and I've run into the same problem recently. It seems to be related to disabling file browse mode, that's the only variable that appears to effect it.

---

### Post by jdk82 on 2011-04-29
wagnerrp over at mythtvtalk wrote a script that fixes this. It worked perfectly for me, going through an removing all the duplicates both on the frontends and mythweb. Here's a link to the forum thread:
[http://www.mythtvtalk.com/multiple-instances-same-video-mythvideo-14651/](http://www.mythtvtalk.com/multiple-instances-same-video-mythvideo-14651/)

and here is a link to the script on the mythtv wiki:
[http://www.mythtv.org/wiki/Remove_duplicate_videos.py](http://www.mythtv.org/wiki/Remove_duplicate_videos.py)

---

