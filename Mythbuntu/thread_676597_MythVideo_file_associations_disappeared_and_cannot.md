---
title: "MythVideo file associations disappeared and cannot be reentered"
date: 2008-01-23
forum: Mythbuntu
---

### Post by Skychaser on 2008-01-23
I've searched around about this, but so far I believe I'm the first one to experience this issue. I'm assuming the probable cause was when I restarted my machine after a freeze up by VLC. I have network shares mounted to the video directory that MythVideo uses and can see all the files when viewed with Thunar. I couldn't figure it out why I couldn't see them in MythTV, so I checked the file type settings. To my surprise, they were all gone. I was like "wtf, mate?" and tried to replace the ones I needed (avi, mpg, etc), but they will not save. I can create only one new file type and as soon as I leave the settings page it disappears again. I've restarted, uninstalled and reinstalled MythVideo, and still no change. Any help, thoughts, etc would be excellent. Thanks!


I suppose while I'm posting I might as well add this as well. My ATI Remote Wonder II is not working properly with MythTV. It's the only thing hardware-wise that isn't working right.

---

### Post by Skychaser on 2008-01-24
Solved! Apparently I messed up a the "videotypes" table in MythTV's mysql database. I did a little searching and used mysql's "repair table" command to fix it.

---

