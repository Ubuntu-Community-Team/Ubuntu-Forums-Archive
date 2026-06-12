---
title: "Flash not playing need reinstallation"
date: 2008-02-13
forum: Multimedia &amp; Video
---

### Post by Gouz on 2008-02-13
Greetings everyone

I have a problem I have installed Flash several time and each time it is playing perfectly as long as I keep the browser on everything.
Once I close it and I open a new one the video is not loading, not even showing that there is a flash video and non error msg is shown


I am using 7.10 (gutsy) and I had no problem with flash before..even after the update to FF 2 until I formated couple of days ago.

do you have any idea?

---

### Post by ubuntu-freak on 2008-02-13
That's really odd. Do you have any other multimedia issues? Check out paragraph 7 of the troubleshooting section in my [how-to](http://ubuntuforums.org/showthread.php?t=661833).
 
Hope that helps. 
 
Nathan

---

### Post by Gouz on 2008-02-14
Thanks for the link really nice work but it didn't helped I had all ready done most of those stuff

But what helped me (I think at least yet I haven't seen any problem) is this

```
  sudo apt-get install alsa-oss
 
```

```
  FIREFOX_DSP="" 
FIREFOX_DSP="aoss"

```

---

### Post by ubuntu-freak on 2008-02-14
Thanks for reminding me about that stupid issue. Forgot to put it in my how-to, but have now.
 
Nathan

---

