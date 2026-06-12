---
title: "Help needed in compresing video so it can be sent by email.15.7 mb"
date: 2012-04-06
forum: Multimedia Software
---

### Post by Peterfc on 2012-04-06
I need to send an email with a video attachment that is 15.7mb in size. I live in Portugal and i have a very slow internet connection 1.75mbs and i keep getting a time out from my email provider. 

Can anybody help i need to somehow compress this file so i can send it by mail.

Thanks for taking the time to read my post.

---

### Post by sudodus on 2012-04-06
> **Peterfc said:**
> I need to send an email with a video attachment that is 15.7mb in size. I live in Portugal and i have a very slow internet connection 1.75mbs and i keep getting a time out from my email provider. 

Can anybody help i need to somehow compress this file so i can send it by mail.

Thanks for taking the time to read my post.
I would do that with ***ffmpeg***, but you could also do it with for example ***OpenShot*** if you prefer a GUI tool.

If your video clip is in a 'crude' state directly from a camera, it might be possible to compress without loss of quality by using a more efficient codec, for example x264. But if it is already encoded with an efficient codec, you must reduce the quality somehow in order to make the file smaller (frame size and/or bit rate)

So let us know more about your video clip!

---

