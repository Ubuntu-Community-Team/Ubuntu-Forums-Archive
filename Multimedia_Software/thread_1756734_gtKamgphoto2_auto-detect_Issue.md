---
title: "gtKam/gphoto2 auto-detect Issue"
date: 2011-05-12
forum: Multimedia Software
---

### Post by mihalybaci on 2011-05-12
I installed gphoto2 and the GUI gtKam for downloading pictures off my camera. When I plug my camera in and choose 'open with gtKam', the program says that the camera is in use. The results of 'ps ux' says that  '/usr/lib/gvfs/gvfsd-gphoto2 --spawner :1.10' is running, after killing that program, or equivalently unmounting the camera, gtKam is free to access the camera and it runs without issue. So my question is, can I disable the auto-detect from gvfsd-gphoto2's so that I don't have to kill it manually every time I plug in my camera?

I've seen other threads, but no solutions so forgive me if this issue has been resolved. 

Thanks in advance for any help.

---

