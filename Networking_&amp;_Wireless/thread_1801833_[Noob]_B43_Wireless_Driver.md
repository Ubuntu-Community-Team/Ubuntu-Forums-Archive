---
title: "[Noob] B43 Wireless Driver"
date: 2011-07-11
forum: Networking &amp; Wireless
---

### Post by IchibanJC on 2011-07-11
I know you are all probably going to think I'm a newb but I really do have to ask this question. The wifi on my laptop that I wanna put Ubuntu on isn't working. It's got the 
"device not ready firmware missing" error. So I did that command in terminal that tells you what driver you need and it said B43. I can't hook up the Ethernet to it for some reason because either the port is broken or it doesn't work. So.. what do I do? hehe. Sawry Im really noob. I was looking into Linux/Ubuntu cuz I wanted to give my old laptop new life. Anyway PLZ help me if u can.

---

### Post by chili555 on 2011-07-11
Hmmm, that's a tough problem you have there, Mr. Noob. I guess you'll have to find the firmware somewhere and download it to your desktop. Right-click it and select 'Extract Here.' A folder will appear called lib. Now open up a terminal and so:```
sudo su
mkdir /lib/firmware/b43
cd Desktop/lib/firmware/b43
cp * /lib/firmware/b43
rmmod -f b43
rmmod -f ssb
modprobe b43
exit
```Now is your wireless working?

---

### Post by IchibanJC on 2011-07-11
Thanks for your reply! I figured it out after a power nap and some power googling. It was less complicated than I thought hehe. Thanks for your help anyway though.

---

### Post by chili555 on 2011-07-11
Do you want to try to troubleshoot the wired ethernet or are you all set?

---

