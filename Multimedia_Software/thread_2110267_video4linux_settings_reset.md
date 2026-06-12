---
title: "video4linux settings reset"
date: 2013-01-29
forum: Multimedia Software
---

### Post by Thee on 2013-01-29
Hi

I setup my webcam settings in video4linux control panel, but after suspend/restart/shutdown all the settings reset to default.

How can I make the settings permanent?

Thanks

---

### Post by tgalati4 on 2013-01-29
When working with video, generally you have to add yourself to the "video" group.  Also, there is v4l and v4l2--two different video frameworks.  I presume there are configuration files in your home directory:

```
ls -la
```

I'm not on a machine currently with a video camera so I can't give the exact location of where these files might be.  Also check in /etc.

---

### Post by Thee on 2013-01-31
I didnt have a Video group so I created one and added myself to it. Not sure if thats what I was suppose to do. Anyway, I cant find configuration files anywhere.
Any advice?

---

