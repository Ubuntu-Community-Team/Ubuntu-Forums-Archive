---
title: "Nvidia geforce GT 120M"
date: 2009-12-16
forum: Multimedia Software
---

### Post by pmaciver on 2009-12-16
Hi,

I have just purchased an Asus N81V, which comes with an Nvidia geforce GT 120M graphics card.

Everything works fine except that when I installed the nvidia graphic driver I get no video output for things such as my skype video calling, the cheese photo taking application, and totem. 

I can hear the sound, and even in cheese when I take a picture I can see the output once it becomes a jpg or whatever format, but while it is trying to output the video to show what picture is to be taken, I see nothing. And the only way I have been able to use VLC to watch videos up until now is to set the video output to something other that the default, opengl seems to work.

I am just not sure how I can do this so that all sort of video output uses this output method.

I am using ubuntu 9.10 and the nvidia driver 185 version from the repo.

Any help would be welcome. 

Thanks

---

### Post by Yellow Pasque on 2009-12-16
```
sudo apt-get install -y gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-bad
gstreamer-properties
```

Test the different outputs under the 'Video' tab.

---

### Post by pmaciver on 2009-12-16
Well that would only solve the video watching problem under VLC.
I want a universal fix.

But just happens that many hours playing with it and googling has brought me the answer.

In fact the answer is in this post here 

[http://ubuntuforums.org/showthread.php?t=1061650](http://ubuntuforums.org/showthread.php?t=1061650)

I basically had to manually set my refresh rate in compiz, and then check "Undirect Fullscreen Windows".

And that seems to have got it working using the default av output.

Anyway else having this problem I suggest that you try this first as it would have saved me a whole load of time if I had knows.

---

