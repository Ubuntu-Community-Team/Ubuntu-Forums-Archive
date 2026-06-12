---
title: "Stream video from linux to windows?"
date: 2007-05-29
forum: Multimedia &amp; Video
---

### Post by allspiritseve on 2007-05-29
Hi,

I would like to be able to stream video from my linux machine to my friend's windows machine. All I am trying to accomplish is to watch the same video at the same time. Does anyone have any idea how to do this?

Thanks,

Cory

---

### Post by Yoooder on 2007-05-29
> **allspiritseve said:**
> Hi,

I would like to be able to stream video from my linux machine to my friend's windows machine. All I am trying to accomplish is to watch the same video at the same time. Does anyone have any idea how to do this?

Thanks,

Cory

If you do some reading into the VLC media player (which is cross-platform) you'll find that it's able to do what you want.  Basically you'll play a file on Linux which will behave as a combination player/server and you should be able to connect to the stream through Windows (I think you'll need to use the win32 version of VLC though... but I'm not certain).

---

### Post by cox377 on 2007-05-29
can you not just map the drive using samba and he connects to it?

Is this over LAN OR WAN?

CoXen

---

### Post by allspiritseve on 2007-05-29
No, she's not on the same network I am. But I don't just want to share the file, I want to watch it at the same time. 

Cory

---

### Post by cox377 on 2007-05-29
I think it might have to be the VLC option then

---

### Post by Yoooder on 2007-05-31
I was just reading about "Democracy"-- an open-source media player built on top of VLC.

I'm not sure if it supports streaming from one person to another, but it appears to have many nice features.  And since it's built on VLC, and VLC supports streaming, there's a good chance that it will work :)

[http://www.getdemocracy.com/](http://www.getdemocracy.com/)

---

