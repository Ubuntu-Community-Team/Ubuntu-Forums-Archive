---
title: "Jaunty Sony Vaio Webcam - Webcam worked, but now it doesn't work any more"
date: 2009-04-22
forum: Multimedia Software
---

### Post by duxi on 2009-04-22
Hi guys,

Hope you can help me with me webcam in jaunty.

As I installed jaunty yesterday, everything worked fine. Even the webcam was supported immediatly. 
But today I opened cheese again and suddenly it says that there's no webcam.

When I checked v4l-conf, it says:

```
duxi@duxi-laptop:~$ v4l-conf 
v4l-conf: using X11 display :0.0
dga: version 2.0
WARNING: No DGA direct video mode for this display.
mode: 1280x800, depth=24, bpp=32, bpl=5120, base=unknown
can't open /dev/video0: No such file or directory

```

Does anybody know what the problem is? Any libraries which has to be installed? 

Thanks in advance

Best regards

duxi

---

### Post by ooobooontooo on 2009-06-01
Hi, I have the same problem. I have a Sony Vaio. Is there a fix for this or should I go and try to find the ricoh driver and install it?

---

### Post by brunjes on 2009-06-08
No answer here unfortunately.

I also have the same problem with my Sony Vaio SZ770N. The webcam worked for a short time with the RC version of 9.04 but shortly after 9.04 went official, some update from the Internet caused it to stop working.

Any one have a clue as to how to get this working again?

Thanks,

Roy

---

### Post by ooobooontooo on 2009-06-09
Please post the results of:
```
lsusb
```

Look for the one that says ricoh...assuming the driver you need is ricoh...If it's 05ca:183b like mine. Then you can go to [http://bitbucket.org/ahixon/r5u87x/]("http://bitbucket.org/ahixon/r5u87x/") to get the camera working. If it has a different id...you can still try...can't guarantee it though. Post if you need extra help.

---

### Post by duxi on 2009-11-09
worked great for me!

just installed this package following the instructions (from README)

Worked great!

best thanks

Webcam working like here = [http://duxthefux.blogspot.com/2009/11/webcam-ricoh-r5u870-einrichten.html](http://duxthefux.blogspot.com/2009/11/webcam-ricoh-r5u870-einrichten.html)

---

