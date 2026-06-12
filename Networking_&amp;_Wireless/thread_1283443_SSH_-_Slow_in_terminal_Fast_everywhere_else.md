---
title: "SSH - Slow in terminal? Fast everywhere else?"
date: 2009-10-05
forum: Networking &amp; Wireless
---

### Post by TheBuzzSaw on 2009-10-05
I've noticed that when I use a program to do SSH (Putty, FileZilla, gFTP, etc.), the response is snappy/quick. Whenever I use the SSH command in terminal, it takes like 20 seconds before it finally asks for my password. Fortunately, the response time is nil from that point on, but that initial connection is so slow. Why is this? Is there a way I could speed that up? I prefer using SSH in the terminal for many things.

---

### Post by renkinjutsu on 2009-10-05
try using ```
-C
``` with ssh.. with that, all information going in and out are compressed and would probably speed things up (if the bottleneck is the network)

---

### Post by TheBuzzSaw on 2009-10-05
No effect. Like I said, it is only the initial wait for the password prompt. It is fast afterward.

---

