---
title: "Can I compress videos?"
date: 2008-04-28
forum: Multimedia Software
---

### Post by Indy452 on 2008-04-28
I guess I'm unable to upload two of my short videos because they are too large for photobucket 100MB limit and mine are both 103.5MB. They are about one minute in length.

I shot them from my Canon powershot camera and uploaded to my videos in Ubuntu 7.10.

I was wondering if they can be compressed or altered in some way so they could be smaller size in MB so Photobucket could upload them to my account?

Neal

---

### Post by chewearn on 2008-04-29
100MB is very large for a one minute video.  You should be able to compress it to less than 10MB using xvid compression.

What is the video format produced by the camera?  You should be able to use avidemux as the GUI front-end for xvid compression.

---

### Post by Indy452 on 2008-04-29
I thought 105 Mb was wayyy to large for such a short video but it is a still camera with a short video function. I figured that was the reason for producing so many mb for a short video.

It uses .avi format I guess it is.

Does Ubuntu have xvid compression or is it something that can be found on synaptic?

Thanks.

---

### Post by chewearn on 2008-04-29
If you have not done so already, install the necessary codec
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Note: I'm not sure if xvid comes preinstalled, but the above page will show you how to install many stuff related to multimedia, etc.

Next, install avidemux
```
sudo apt-get install avidemux
```

Avidemux is an application to manage video encoding.  The usage/GUI is almost self explanatory, but not quite straight forward.  It could take a while (and some trial and error) for you to learn, if this is the first time you tried video encoding.

---

