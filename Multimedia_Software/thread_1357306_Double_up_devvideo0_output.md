---
title: "Double up /dev/video0 output?"
date: 2009-12-17
forum: Multimedia Software
---

### Post by revanb on 2009-12-17
I have a TV card installed and I use it to monitor a security camera. Everything works wonderfully.

I also run "webcam" or "motion" on it. Those are program that take snapshots periodically or based on detected movement and saves it with a timestamp. This also works wonderfully.

The question is that I can't watch the security camera using TVtime while using the mentioned software because only one at a time can use the /dev/video0 device.

Now, I'm sure it must be possible to somehow clone the output and give each program a copy. It's the same output after all.

Does anyone know how to do this?

---

### Post by revanb on 2009-12-17
Any ideas anyone?

I thought there may be something that will read /dev/video0 and create /dev/video1 and /dev/video2 which are simply clones of the output. Then I could use tvtime on one and another program on the other at the same time?

---

### Post by VertexPusher on 2009-12-17
From the "motion" package description:
> Also, motion has its own minimalistic web server. Thus, you can access the webcam output from motion via a browser.

---

### Post by revanb on 2010-01-05
Thank you, I have also found the video loopback device provided by motion. This allows you to feed the video into XawTV or similar after motion has used it.

---

