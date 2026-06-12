---
title: "Mythtv - Frontend video playback failure"
date: 2007-03-17
forum: Multimedia &amp; Video
---

### Post by sstakes1 on 2007-03-17
Hi all,
I have successfully(?) installed mythtv frontend on my laptop. It is configured to connect to my mythbackend server. When the frontend is brought up, everything seems fine. It shows recorded items available on the backend. It also plays the video preview in the select recording screen correctly. However, when I select a particular item, the screen goes blank as if its about to begin playback and then the select recordings screen comes again and the preview plays OK.

I'm trying to diagnose this problem. Nothing untoward seems to be happening. I tried to look at mythfrontend -v playback and compare the output in both this frontend and the frontend directly attached to the backend and do not find any major differences.  The output on the laptop seems to indicate successful retrieval of the media. Monitoring the wireless connection also shows a lot of inbound packets.

There is no log at /var/log/mythtv/mythfrontend.log.

Does anyone know of a solution. Please help me.

---

### Post by sstakes1 on 2007-03-19
Okay, I solved the problem.

Here's the details in case anyone runs into it in the future. The documentation for installing the frontend only are not very clear. I had a backend on the laptop as well and it was pointing to the master backend. That made the video preview work somehow, but not the actual playback. All I had to do was to in the mythfrontend on the laptop was to point it directly to the database on the backend. This would mean that you would have to enable networking on the mysql database on the backend server and authorize the mythtv account on the front end to access it. 

HTH

---

### Post by majoridiot on 2007-03-19
> **sstakes1 said:**
> This would mean that you would have to enable networking on the mysql database on the backend server and authorize the mythtv account on the front end to access it.

this is the standard way to install a mythtv frontend.  the simplest way to do this (if you installed
from ubuntu packaging) is to copy /etc/mythtv/mysql.txt from your backend machine to the
~/.mythtv/ folder on the frontend.

optionally, you can modify ~/.mythtv/mysql.txt on the frontend by hand, getting the information
from the backend with an ssh connection to it and:

```
# more /etc/mythtv/mysql.txt
```

glad you got it figured out!

---

