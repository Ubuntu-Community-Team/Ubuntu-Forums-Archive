---
title: "Firefox mplayer shows sound only in wmv videos"
date: 2007-02-09
forum: Multimedia &amp; Video
---

### Post by bongadadu on 2007-02-09
Hey,

In new to ubuntu and linux in general.
Ive gotten a lot of stuff to work to my liking and am enjoying the experience, however i am experiencing some problems with firefox and playing wmv embedded video

I have totem and mplayer correctly installed the the corresponding plugins for firefox, now when i play  a wmv file i can see the mplayer buffering the video , once the buffering is complete it only plays the sound, does not show the video at all. (see attached pic)

What could be the problem

thanks in advance for your help

---

### Post by EdThaSlayer on 2007-02-09
I'm not sure which Ubuntu version you have but I recommend you reinstall from gstreamer to xine.
That is what fixed my problems of not being able to view Windows Media Video files.
> 
sudo aptitude install totem-xine


---

