---
title: "Cant get a working bt878 or Logiteh camera to work with mythtv"
date: 2008-12-17
forum: Mythbuntu
---

### Post by ggpr on 2008-12-17
Cant get a working bt878 or Logitech camera to work with mythtv
Both devices work with v4l with other programs on linux (VLC and Xawtv) but I can not get them to work with mythtv.

The logs keep showing errors about setting a channel or pginfo (guessing program guide info)

as both of these devices do not have a tuner, there is no need for a program guide.

You may be wondering why I am using these devices, its because I am trying out mythtv to see if I should be saving up the big bux for a better machine with hopefully the hvr-2250 (theres supposed tobe drivers for this coming soon).  

Error Log:
I am changing the source information. nograbing source or none for source on video input.
[http://mythbuntu.pastebin.com/f7a4f604c]("http://mythbuntu.pastebin.com/f7a4f604c")


Side Questions:
1)If I got a frame grabber card, would the encoders on an hvr-2250 hardware encode its stream or does mythtv/hardware not support hardware encoding other sources?
2)Is there a way to split up a video from a capture card to different programs? ie. zoneminder(security) + mythtv for live viewing

---

### Post by ggpr on 2008-12-17
Update:

I still can't get the camera to work with mythtv, but I eventually got the bt878 to work only with the back end.
Now I appear to be having problems with getentry(-1) which I think is the program guide.

Updated Log:
[http://mythbuntu.pastebin.com/f1e2e556e](http://mythbuntu.pastebin.com/f1e2e556e)

---

### Post by ggpr on 2008-12-18
Funny thing is, it can record.  I'm not sure why it can not play live tv.

---

### Post by ggpr on 2008-12-18
What does this error mean, it is the one I am getting now.
MythSocket(990b808:27): readStringList: Error, timeout (quick).

---

### Post by jaysmit9 on 2009-03-18
How did you get it to work with the backend?

---

