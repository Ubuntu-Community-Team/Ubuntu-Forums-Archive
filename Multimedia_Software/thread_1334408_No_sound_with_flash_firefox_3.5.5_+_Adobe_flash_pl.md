---
title: "No sound with flash firefox 3.5.5 + Adobe flash player + ubuntu"
date: 2009-11-22
forum: Multimedia Software
---

### Post by UNME on 2009-11-22
Hi Guys,

I am not able to play youtube videos and google videos with sound.
Graphic Quality is good but there is no sound!!

tried many tweaks here but all seems to be with older versions none working on U 9.10 Karmic Kuala.

Help need.
thanks 
Unme...

---

### Post by surveyorsteve on 2009-11-26
Hi, I have the same problem but it also plays too fast. This is only on one user on the PC though, videos play OK with sound with other users on the same PC.

Any ideas?

---

### Post by masux594 on 2009-11-26
This command worked for me..
```
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1 && sudo mkdir -p /tmp/.esd/ && sudo touch /tmp/.esd/socket 
```
.. and for you?

Sysc, A

---

