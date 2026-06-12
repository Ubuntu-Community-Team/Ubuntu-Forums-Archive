---
title: "Can't Get LIRC to Work"
date: 2007-03-21
forum: Multimedia &amp; Video
---

### Post by deejross on 2007-03-21
Hello,

I'm trying to make a PVR with MythTV and Ubuntu. I got MythTV up and running using the guide from [http://parker1.co.uk/mythtv_ubuntu.php]("http://parker1.co.uk/mythtv_ubuntu.php") Now, I can't get my remote to work. I have a Fusion Remote MCE and I've followed many tutorials on what to put into the lircd.conf file. I installed lirc from apt-get. Running lircd doesn't produce any error that I can see, but when I run 'irw', it puts me right back at the command prompt. When I run it a second time, it returns with "connect: Connection refused".

I have tried running it with ```
lircd --driver=dvico --device=/dev/hiddev0
``` But no luck.

Any help would be much appreciated, thanks.

---

### Post by bloodniece on 2007-03-22
Somewhere along my same quest to get LiRC to work, I think remember I had to blacklist the  ir-common module.

---

