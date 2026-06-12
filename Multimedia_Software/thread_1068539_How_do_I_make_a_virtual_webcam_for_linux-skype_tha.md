---
title: "How do I make a virtual webcam for linux-skype that will point to images?"
date: 2009-02-13
forum: Multimedia Software
---

### Post by squeakyneb on 2009-02-13
I want to share some pics with a friend via Skype. I know there are other ways to share pics and talk over the net, don't ask.

I was thinking a virtual webcam. I start a video chat, and tell skype to use my "webcam" that doesn't exist. The virtual webcam will get it's data from whatever picture (maybe a movie file?) I point it to. So I point it to "lol.jpg" and my friends Skype receives it as being my webcam.

I was thinking of achieving this by creating a virtual device that looks like a webcam ("/dev/cam0"?). I then write a program that will constantly write the data from a specified image to the virtual device.

Any advice? I have no idea how to do any of this, although I can write to a device (with Python, it's like r/w to  file, right?). The picture file may also need to be transcoded or it might look like random rubbish.

Thanks,
Benny

---

### Post by ilioscio on 2009-02-13
I think what you are looking for is called a "video loopback" device you may get lucky with [this]("http://allonlinux.free.fr/Projets/AVLD/"), but it doesn't look very easy...

---

### Post by squeakyneb on 2009-02-13
OMG Thank you! Such a quick response, too. It is an Open Source Program, so I am also going to study it, see if I can make a virtual cam.

Thanks again,
Benny

---

### Post by ilioscio on 2009-02-14
Cool, good luck getting it working.

---

