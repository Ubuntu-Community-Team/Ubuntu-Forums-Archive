---
title: "Storage Groups problem"
date: 2010-03-21
forum: Multimedia Software
---

### Post by wembleyboy on 2010-03-21
I have installed mythbuntu and all is going well !!!

A couple of questions. 

1) What is a storage group and what advantage do they have ?

2) When I select "watch videos" it takes me to the next window which is called storage group. There is a question mark and is called storage...

I have attached picture. 

I appreciate any help. ;)

---

### Post by tburkhol on 2011-04-06
Storage groups are a way for the mythtv backend to organize a number of file stores (including local directories) and deliver the contents to a frontend.  If your frontend and backend are on different machines, they claim this can simplify setup.  In ubuntu, setting up the backend to export /var/lib/mythtv isn't hard, and setting up to auto-mount /var/lib/mythtv on the frontend is straightforward.

I recommend you avoid storage groups.  First, they force you to use mythtv's internal video player, which I find not as good as mplayer or vlc in interface or CPU efficiency.  Second, if you use separate front and back-ends, playing a storage-group video may consume 5-10x more bandwidth than the same video played over NFS.  For me, this means videos that videos which play smoothly in mplayer over NFS through my wireless (g) network, stutter enough to be unwatchable through mythtv.

---

