---
title: "WiFi stopped working after update"
date: 2011-07-06
forum: Networking &amp; Wireless
---

### Post by life in color on 2011-07-06
Hi, it took me a while but I got my wifi working about a month ago, I have an HP Pavilion dv8000 with a broadcom bcm4318, it worked fine until I updated my system and rebooted, now I can only use my ethernet, any help?

---

### Post by u4ric on 2011-07-06
Sorry I can't help but just thought i'd say I have had the same problem.

---

### Post by life in color on 2011-07-07
> 
Sorry I can't help but just thought i'd say I have had the same problem.

Thanks for at least replying!

---

### Post by life in color on 2011-07-07
> 
Sorry I can't help but just thought i'd say I have had the same problem.

When you say you have the same problem, do you mean he exact same problem as in, you had WiFi then opened Update Manager and installed some updates and it now doesn't work, or do you mean something else?

---

### Post by chili555 on 2011-07-07
Sometimes, I like to compress everything into one educated guess. Please open a terminal and do:```
sudo modprobe b43
```Is it working now? If so, please do:```
sudo su
echo b43 >> /etc/modules
exit
ls /etc/modprobe.d | grep b43
```Post the result of the last post, if anything. If that doesn't get the wireless going, post:```
lspci -nn | grep 0280
```And then I'll do it the hard way.

@u4ric--

Unless you know you have a Broadcom 4318, do not try the above and start your own thread.

---

### Post by life in color on 2011-07-07
Ok let me first say that  when I saw that you, Chili555, commented I was already assured it would work cause I follwed your guide in the first place to get my wiFi working back in the day.
> 
Sometimes, I like to compress everything into one educated guess. Please open a terminal and do:
Code:
sudo modprobe b43
Is it working now? If so, please do:
Code:
sudo su
echo b43 >> /etc/modules
exit
ls /etc/modprobe.d | grep b43
Post the result of the last post, if anything. If that doesn't get the wireless going, post:
Code:
lspci -nn | grep 0280
And then I'll do it the hard way.

@u4ric--

Unless you know you have a Broadcom 4318, do not try the above and start your own thread

WORKED!!!!! :) :) :)
I owe you from last time and now I owe you again Chili555!
thank you 5 million!

---

