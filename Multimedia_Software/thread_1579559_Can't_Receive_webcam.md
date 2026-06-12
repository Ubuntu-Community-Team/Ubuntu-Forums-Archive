---
title: "Can't Receive webcam"
date: 2010-09-22
forum: Multimedia Software
---

### Post by Wag on 2010-09-22
I can send web cam on skype/amsn/gyache/ and cheese works fine... but I cannot receive web cam on any of those clients.. if I try the clients crashes.. any ideas?

---

### Post by dirty_harry on 2010-09-22
wecam ubuntu howto:
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

which one are you using?
[https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras)

I have a Logitech Quickcam and on Jaunty & Lucid I need to
```
bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```but nevertheless skype shouldn't crash...

---

### Post by dirty_harry on 2010-09-22
:confused:


Sorry but I misunderstood the first post. I thought that the problem is the local webcam... what is a different matter. Any luck now?

But what has this to do with any sort of interpersonal relationships performed in real life'?' I really don't get it.


[COLOR=#000000][FONT=Arial][FONT=Tahoma]
[/FONT][/FONT][/COLOR]

---

### Post by Wag on 2010-09-22
I can send cam but not receive... not sure why..

Rubesam ... don't troll here please if you can't help then its better to say nothing

---

### Post by dirty_harry on 2010-09-23
I tried to find out more about your problem, not that easy --- google-fu:

[https://jira.skype.com/browse/SCL-428](https://jira.skype.com/browse/SCL-428)
two years old, on ubuntu 8.04 and 8.10... unsolved

can you start skype in the terminal, because I don't know where skype logs his errors (?messages)

---

### Post by Wag on 2010-09-23
Its not just with Skype but with GyachE and amsn as well... cheese works fine.. 

I don't think its a firewall or router, because the ports are open to allow cam in, and the program(s) crash right after the initial feed.

---

### Post by dirty_harry on 2010-09-28
How's it? Anything new or is it still crashing when you try to establish a video-conf with someone?


Have you tried to install the gstreamer-plugins?
->> [http://ubuntuforums.org/showpost.php?p=9695088&postcount=42](http://ubuntuforums.org/showpost.php?p=9695088&postcount=42)

---

