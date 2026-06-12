---
title: "Process Max Out CPU What Is It?"
date: 2009-02-10
forum: Mythbuntu
---

### Post by rschapman on 2009-02-10
I have a process that is maxing out my cpu when I'm using my HDHomerun. I have an NVIDIA chipset and made sure to turn Events on in the xorg config. If anyone has any idea what I can do I'd appreciate it. Thanks. 

[HTOP Screenshot]("http://www.trinity.edu/rchapman/jing/mythtv_htop.png")

---

### Post by movieman on 2009-02-11
That's your X-server, I believe.

---

### Post by rschapman on 2009-02-11
That's what I assumed. Does anyone know what it's doing exactly? I have a 3Ghz Intel Core 2 with 4GB of Ram. I just think it's odd it's hitting my system that hard. All it's doing is writing to the disk it's not transcoding anything.

---

### Post by Lido on 2009-02-12
I'm having the same/similar problem and haven't found the solution yet. There's a thread about tearing that I started at mythtvtalk.com in the hardware section where some people have given me some help.

---

### Post by Da_Teach on 2009-02-12
Try disabling xvideo v-sync, see if that lowers cpu usage. If it does then its the same issue I'm having. Note that disabling v-sync isnt really a cure as it leads to massive tearing.

---

