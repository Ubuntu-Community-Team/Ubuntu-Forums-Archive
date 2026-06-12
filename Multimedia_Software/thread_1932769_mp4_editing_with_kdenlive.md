---
title: "mp4 editing with kdenlive"
date: 2012-02-28
forum: Multimedia Software
---

### Post by jamesbon on 2012-02-28
I installed kdenlive and wanted to edit mp4 file. Basically want to add images and subtitles to this mp4 file.But upon opening them in kdenlive it says that mp4 are not kdenlive type files.So I can not edit it.Is this the case i.e. kdenlive does not support mp4 audio clip editing 

or I need to try some thing else?

---

### Post by sgtGarcia on 2012-03-24
Don't know if You still need help.

For KDEnLive You need to install
```
libavcodec-extra-53
```
It can be ```
libavcodec-extra-52
``` if You got Ubuntu older than 11.10


And then in KDEnLive go to Settings->Run Config Wizzard
Go through wizzard & then You should be able to use those formats ( maybe You will need to restart KDEnLive ).

---

