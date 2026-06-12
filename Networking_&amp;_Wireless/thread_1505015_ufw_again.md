---
title: "ufw again"
date: 2010-06-08
forum: Networking &amp; Wireless
---

### Post by dilaudid on 2010-06-08
Sorry to reanimate a dead thread, but I wanted to check my understanding.
```
sudo ufw default deny
``` is designed to stop all incoming and outgoing traffic. If you want to only deny incoming traffic then use:
```
sudo ufw default deny incoming
```
The reason to ban incoming traffic is that it may be an attack. Banning outgoing traffic suggests that your system is already compromised - either someone you don't trust will have control of your system (e.g. you are an internet cafe) or there is a rogue process on your system which you want to stop phoning home. Hopefully these cases are pretty unlikely, so I'd recommend just banning incoming traffic. I'm planning to implement:
```
sudo ufw allow ssh
sudo ufw default deny incoming
```
Which is intended to restrict incoming traffic to ssh. If anyone with more experience can spot holes in my plan - please reply to this post!

---

### Post by Iowan on 2010-06-08
That thread was a little old - linked [here]("http://ubuntuforums.org/showthread.php?t=909110") for reference.

---

