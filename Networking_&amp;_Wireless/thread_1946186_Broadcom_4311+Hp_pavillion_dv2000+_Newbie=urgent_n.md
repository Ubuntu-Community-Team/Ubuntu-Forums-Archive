---
title: "Broadcom 4311+Hp pavillion dv2000+ Newbie=urgent need of solution 2 problem"
date: 2012-03-24
forum: Networking &amp; Wireless
---

### Post by saintnikolausx on 2012-03-24
Hi!

I am aware about the sticky-thread above, but cant find the answer to this, quite urgent problem. the fact that i need an urgent solution is the reason why i start a new thread, which i hope is kosher... 

To begin with, i am completely new to linux. Almost free of any knowledge concerning this system...

I installed xubuntu (latest version) and everything worked smooth Except the wireless connection. I have realized it&#347; a common and well known issue, so i have tested all the solutions in the thread above. I have now come to the point where i can get the card to work by installing the windows .inf driver through the ndis program. the problem is that, in order to get the wireless working, i have to reinstall the drivers everytime i reboot, and after that operation it works flawless. How can i do to solve this problem with having to reinstall everytime?

Thx in advance! Niklas

---

### Post by wildmanne39 on 2012-03-24
Hi, this should do it but if that is your wireless card you do not need ndiswrapper.
```
sudo su 
echo ndiswrapper >> /etc/modules 
exit
```
Thanks

---

### Post by saintnikolausx on 2012-03-24
> **wildmanne39 said:**
> Hi, this should do it but if that is your wireless card you do not need ndiswrapper.
```
sudo su 
echo ndiswrapper >> /etc/modules 
exit
```Thanks

SweeeT! works like a charm!
 TY!

---

### Post by wildmanne39 on 2012-03-24
Hi, that is great glad I could help, can you send me a private message and give me a link to the directions you used to install ndiswrapper, and use thread tools at the top of the page to mark as solved.
Thanks

---

