---
title: "Mediatomb transcoding on headless server"
date: 2009-09-16
forum: Multimedia Software
---

### Post by Udayakiran on 2009-09-16
Is there any way to implement transcoding in Mediatomb on a headless ubuntu server? I have tried to install vlc, but it tries to install xfce also. So, is there any alternative?

---

### Post by Udayakiran on 2009-09-16
Sorry to *bump* this up, i'm getting a bit desperate.

Have you ever heard of Transcode? Seems it is a set of command line tools for transcoding.

---

### Post by Udayakiran on 2009-09-19
Final *bump*. Anyone?

---

### Post by tristan5 on 2010-10-02
I've got the same problem. ;-)
Unfortunately I use a PS3 to view my media which reside on a Ubuntu headless machine. Using the PS3 to watch video files is really painful, I don't know why SONY allows such a restricted group of video codecs. :-(

If you are using mediatomb to transcode video files I think there are some options. Using vlc is one of them but it seems that you have to install the whole vlc package, which depends on a graphical environment (Gnome, xfce ...). So installing vlc on a headless machine seems to not make any sense.

Probably there are more encoders available that do not require that kind of burden on our machines. I heard something about mencoder and ffmpeg encoder but I do not know anything right know about this stuff so I cannot tell. :-|

---

### Post by fraser_john on 2011-03-10
Have you read [http://www.vanalboom.org/node/14](http://www.vanalboom.org/node/14)?

I am currently using Twonky but there are some things that my Panasonic plasma TV won't recognize. The above details how to transcode everything on the fly within mediatomb, so I will be looking at it over the w/e.

---

### Post by Blues- on 2011-03-10
Yes .. I use mediatomb and transcoding on my headless server.
But I do not use VLC .. I use ffmpeg

---

### Post by fraser_john on 2011-04-05
I ended up using the PS3 Media Server and found a config file for the Panasonic plasma tv that works really well, very pleased indeed.

---

