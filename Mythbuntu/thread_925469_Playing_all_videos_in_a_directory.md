---
title: "Playing all videos in a directory"
date: 2008-09-20
forum: Mythbuntu
---

### Post by rflook on 2008-09-20
Is it possible to get mythtv to play all videos in one directory. At the moment i am having to drop out of the frontend and use something like mplayer or kaffeine. Ideally id like to just be able to chose a directory in myth and play it in some way - but an alternative would be for me to create a playlist somehow and play that. Any suggestions greatly appreciated

---

### Post by managementboy on 2008-09-23
> **rflook said:**
> Is it possible to get mythtv to play all videos in one directory. At the moment i am having to drop out of the frontend and use something like mplayer or kaffeine. Ideally id like to just be able to chose a directory in myth and play it in some way - but an alternative would be for me to create a playlist somehow and play that. Any suggestions greatly appreciated

I don't think mythvideo has this feature. Main MythTV has a playlist for recordings (press M and/or INFO).

---

### Post by newlinux on 2008-09-23
I believe in video manager you can setup what file plays upon exiting a file. You could sort of setup a playlist this way.

---

### Post by raptorjr on 2008-09-23
A feature i would like to see is the ability to "play" a folder. That way you could have a entire season in a folder and the folder plays every episode. And also remember where it left off so you could continue to watch later.

---

### Post by novellahub on 2008-09-23
> **raptorjr said:**
> A feature i would like to see is the ability to "play" a folder. That way you could have a entire season in a folder and the folder plays every episode. And also remember where it left off so you could continue to watch later.

There is the ability to continue playback where you left off if you change your videos to play using the internal player. 

Otherwise you can download mplayer-resumer.pl from here:

[http://mythic.tv/contributed_code.php](http://mythic.tv/contributed_code.php)

Make sure you follow the directions on the page.

---

### Post by newlinux on 2008-09-23
> **raptorjr said:**
> A feature i would like to see is the ability to "play" a folder. That way you could have a entire season in a folder and the folder plays every episode. And also remember where it left off so you could continue to watch later.

There is a setting to remember your position in the video tree in myth so you can start from the video you left off on in a folder. It only works if you use the list view (at least for me) of mythvideo.

Other than that, you have to setup the "File to alwyas play next" video explicitely. I agree it Would be nice to have this option automatically. It could be done probably with a  script that updates the database field (child id in video_metadata?) that sets the file to play next.

---

