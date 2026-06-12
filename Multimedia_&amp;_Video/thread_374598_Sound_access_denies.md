---
title: "Sound access denies"
date: 2007-03-02
forum: Multimedia &amp; Video
---

### Post by sergei on 2007-03-02
Hello,

I am using a multi-user Ubuntu desktop. Just recently, I got multiple sounds to work. Unfortunately, If I log in after using the "Switch User" button from another users account, my sound does not work!

When I open gstreamer-properties, and when I click "test" I get the following error message: 

 gstreamer-properties-Message: Error running pipeline 'ALSA - Advanced Linux Sound Architecture': Could not open resource for writing. [gstalsasink.c(640): gst_alsasink_open (): /pipeline0/alsasink1:
Playback open error on device 'default': Permission denied]

On the other hand, If I use sudo gstreamer-properties, the test works perfectly.

I have not been able to figure out a solution to this problem even with the help of the internet, so any help is appreciated.

Thank you!

---

### Post by deadgobby on 2007-03-03
open up the terminal and type in 
kill esd
 See if you can get sound when logged into the other user account.
Gobby

---

### Post by sergei on 2007-03-03
I just tried what you said, but it still doesn't work. Are there any other possibilities?

---

### Post by sisco311 on 2007-03-03
in terminal:
```
sudo adduser [username] audio
```
where [username] is your username

---

### Post by sergei on 2007-03-03
I've done that too, it doesn't help

---

### Post by sergei on 2007-03-03
Ok, so, I have spent some time doing research.

The problem is that 2 different users can not play sound at the same time (unless the second one is root)

I think the problem may somehow involve permissions being changed when the sound card is accessed. If so, how would I solve this problem?

Thanks!

---

