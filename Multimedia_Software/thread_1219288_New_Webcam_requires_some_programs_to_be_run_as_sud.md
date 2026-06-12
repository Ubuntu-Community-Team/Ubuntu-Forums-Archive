---
title: "New Webcam requires some programs to be run as sudo!"
date: 2009-07-21
forum: Multimedia Software
---

### Post by Rytron on 2009-07-21
Hi.
I just got a web cam. I notice that I need to run sudo wxcam to get wxcam to work with it. Also cheese needs to be run in sudo *[COLOR="DarkSlateGray"]sometimes[/COLOR]*. How can I use the Webcam as non sudo user?

---

### Post by igorzwx on 2009-07-21
This should be immediately reported to the security forum.

---

### Post by Dragonbite on 2009-07-21
Look at the permissions of /dev/video0. I think that is where it is. If so, you may be able to try ```
chmod 777 /dev/video0
``` to make it not root-only accessible.

I'm guessing here.

When I run something like Kino the first time, I get the message about /dev/raw1394 not be accessible. I have to run the chmod command to /dev/raw1394 and then I can access it with no problems.  I'm just guessing that your webcam is operating in a similar fashion.

---

### Post by Rytron on 2009-07-22
```
chmod 777 /dev/video0
``` seems to have done the trick.

I also used chmod 777 for audio1 which appeared in /dev when the webcam was connected. I now can get audio.

---

### Post by Dragonbite on 2009-07-22
> **Rytron said:**
> ```
chmod 777 /dev/video0
``` seems to have done the trick.

I also used chmod 777 for audio1 which appeared in /dev when the webcam was connected. I now can get audio.

Great! Glad it worked!

---

### Post by Rytron on 2009-07-22
I can now use **cheese** to record video with sound. ~ Perfect. :D
Although **wxcam** records only video with NO sound. Does anyone know how to get wxcam to record video and sound?
Thanks.

---

### Post by Rytron on 2009-09-21
Has anyone got wxcam to record sound with video?

:confused:

Surely someone knows?

---

### Post by no2498 on 2010-02-02
i do on 804

---

### Post by Rytron on 2010-02-03
> **no2498 said:**
> i do on 804

Please elaborate. :o

---

