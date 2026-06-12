---
title: "Mythvideo VIDEO_TS not recognized"
date: 2009-11-01
forum: Mythbuntu
---

### Post by wittewim on 2009-11-01
I've reinstalled my PVR with the brand new Mythbuntu 9.10. Installation went pretty smooth although there are some frustrating issues. I will make a separate thread for each one of them.

My video archive exists of all kinds of file types including DVDs as iso or as dvd-rip (VIDEO_TS folder containing vob files). With all my previous installations mythvideo recognizes the VIDEO_TS type as DVD. It would only show the name of the parent directory, i could play the dvd just from there. Now i can see the entire DVD structure, something i don't really want. How can i hide the structure and let mythvideo recognize the folder as a playable DVD.

I've tried to play with the file extension 'VIDEO_TS' without success. I must be something really simple

---

### Post by joho500 on 2009-11-02
Hi Wim,

It's a known problem with MythTv 0.22 when using the new Storage Groups. You can use 0.22 without the Storage Groups (i.e. the old way). See the transition guide at mythtv.org: [http://www.mythtv.org/wiki/MythVideo_.22_Transition_Guide]("http://www.mythtv.org/wiki/MythVideo_.22_Transition_Guide")

Cheers,
Joost

---

### Post by wittewim on 2009-11-02
As far is i know i am using the old way to structure my files. Everything is in a locally mounted NFS share. All settings are set on the frontend.

Is it possible that Myth thinks i am using the new storage groups? It is hard too tell because it's a single machine frontend & backend

I will dubbelcheck the configuration later on. Keep you posted

---

### Post by tgm4883 on 2009-11-02
Where are your video files stored?

Did you do a clean install of 9.10 AND not restore from a database backup?

---

### Post by wittewim on 2009-11-02
I've removed all the folder settings in the backend and indeed the problem is solved. All DVD's just show the parent folder and they are playable.

Up to the next problem :-)

---

### Post by bheemboy on 2009-11-13
Could you please explain what you did in layman terms. I am having the same issue.

---

### Post by wittewim on 2009-11-14
On mythbackend there is a configuration option for several directories. Just remove all (except recordings and live_tv). You can define your video folder again on the frontend. That way you use the old method and VIDEO_TS folders are recognized as movies.

Give it a try. It's quite easy

---

### Post by williammanda on 2009-11-14
One comment to add here. Just delete the video storage group. IF you delete the others as suggested you will not get the benefit of the artwork for your videos and tv recordings if you have more than one backend.

---

### Post by rhpot1991 on 2009-12-18
This issue came up in IRC today, so I ran some test and updated the following link as it has directions for fixing both ISO and VIDEO_TS playback:
[http://www.baablogic.net/drupal/node/7](http://www.baablogic.net/drupal/node/7)

---

### Post by larsolav on 2009-12-18
> **rhpot1991 said:**
> This issue came up in IRC today, so I ran some test and updated the following link as it has directions for fixing both ISO and VIDEO_TS playback:
[http://www.baablogic.net/drupal/node/7](http://www.baablogic.net/drupal/node/7)

rhpot1991, do the ISOs play with normal sound for you? My sound on the ISOs is all smurfy fast and either falls behind or is ahead of the video... there is a post here about it... [http://ubuntuforums.org/showthread.php?t=1329230](http://ubuntuforums.org/showthread.php?t=1329230)

---

### Post by rhpot1991 on 2009-12-18
> **larsolav said:**
> rhpot1991, do the ISOs play with normal sound for you? My sound on the ISOs is all smurfy fast and either falls behind or is ahead of the video... there is a post here about it... [http://ubuntuforums.org/showthread.php?t=1329230](http://ubuntuforums.org/showthread.php?t=1329230)

I've seen that issue, normally pausing or skipping chapters around fixes it for me.  I don't see it often.

---

