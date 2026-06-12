---
title: "How to mount a folder of my pc on other pc?"
date: 2006-06-03
forum: Networking &amp; Wireless
---

### Post by hit0442 on 2006-06-03
That's it. I think I've already seen it. I want to mount a folder of my Linux in the linux of my brother. If it's possible, please.

Yes, we are connected in a lan.

:)

---

### Post by rbalfour on 2006-06-03
Here is your answer.
 [http://www.ubuntuforums.org/showthread.php?t=103860&page=3](http://www.ubuntuforums.org/showthread.php?t=103860&page=3)

---

### Post by hit0442 on 2006-06-03
I have a bad english but I'll try to follow this guide. Thank you.

Just a question, what should I do here?

2) Add fuse to /etc/modules
sudo nano /etc/modules

---

### Post by rbalfour on 2006-06-03
The command is

> sshfs

Use 
> man sshfs 

for more info.

---

### Post by hit0442 on 2006-06-03
Don't I have to install this FUSE first?

---

### Post by hit0442 on 2006-06-03
It's working pretty nice. Thank you.

---

