---
title: "MythTV LiveTV not successfully started"
date: 2009-12-07
forum: Multimedia Software
---

### Post by mellery on 2009-12-07
I'm trying to watch live tv using mythtv and a WinTV HVR 1250 Hauppauge PC TV Tuner.  When I select watch tv it says playback starting and then goes back to the main screen.  In my terminal it says TV Error: HandleStateChange(): LiveTV not successfully started.

I was able to control my tv converter box and find all my tv channels with mythtv-setup. So my card seems to be working fine in ubuntu.  

I also have my mythtv recorded folders set to the mythtv group with read and write permissions.

edit: solved, mythtv didn't have the right starting channel

---

### Post by nojstevens on 2010-09-19
Hello,

Could you elaborate on your fix - 'didn't have the right starting channel'? I think I have the same issue.

Thanks

Jon

---

### Post by zepfan on 2010-09-20
> **nojstevens said:**
> Hello,

Could you elaborate on your fix - 'didn't have the right starting channel'? I think I have the same issue.

Thanks

Jon

Go into mythbackend, and look at the tuner setup. It should be where you scanned for channels, under input connections. Click on each tuner you have and set the starting channel to an actual channel.

---

