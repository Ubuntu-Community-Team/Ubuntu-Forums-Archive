---
title: "Mythvideo."
date: 2008-01-16
forum: Mythbuntu
---

### Post by Scrier on 2008-01-16
Hi, 

I have some issues with finding files in the mythlibrary. I have a samba mounted folder from the backend and the files are there and I can start them from my user but the mythlibrary don't find any files. Do I have to mount them with the mythtv user, or have I missed some setting?

//Andreas

---

### Post by aaltieri on 2008-01-16
Greetings!

If you can see them as your normal user, you should be able to see them in mythvideo.

One thing I had to do though is go into the video settings and set up several file types.  MKV, AVI, and a couple other common file types were not there.  Once I set these up, they were found by mythvideo no worries.

Otherwise, if you can log in as your normal user, open a terminal window and see the directory mounted where you told mythvideo to find it, access rights shouldn't be an issue.  

Peace

--anthony

---

### Post by Meph1st0 on 2008-01-16
When I add files to my mythvideo folder I have to go to Video Manager in Settings and then set the video as browseable.  The easiest and most effective way (because it downloads the movie cover art too) is to select a video, hit menu and then search IMDB.

If you don't see your videos in video manager then there's something else going wrong.  You might want to try going into Settings/Media Settgins/Videos Settings/General screen 2 and enable:

Video Browser browses files
Video Gallery browses files
Video List browses files

That will force mythfrontend to read the files in your videos folder without regard to whether or not the browseable setting is set.  The only annoyance with this is it won't read any of the video metadata but at least you'll be able to watch your videos.

Oh and one more thing.  Make sure that you've got the correct folder entered in the "Directory that holds videos" setting under Settings/Media Settgins/Videos Settings/General screen 1.

---

### Post by Scrier on 2008-01-17
Well, the skimming of documentation strikes again. I had a semikolon separated list instead of a kolon separated list :( Thanks for all the answers though

---

