---
title: "Atheros AR5007EG not working..."
date: 2009-07-10
forum: Networking &amp; Wireless
---

### Post by asiankid on 2009-07-10
as you can probably tell, i am a complete Linux n00b. I've wanted to completely switch, but i found i still am going to need windows for school, but on to my problem

i have an Atheros AR500EG on my acer aspire 5515 and there is a driver loaded in my Linux partition, but when i go to the network preferences or whatever it cant connect to any wifi networks.

i know i have wifi b/c there is a router in my house.

can anyone help?

thanx in advance,
AsianKid

ps sry if this has been answered b4, i wanna hurry and get my hardware working

---

### Post by superprash2003 on 2009-07-10
try this , hope this helps [http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html](http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html)

---

### Post by asiankid on 2009-07-10
First of all, thanx for such a quick reply 

 Secondly,I'm not sure if this has to do with anything, but when I typed in the lshw -C network command, it said it was unclaimed

if you could tell me what that means, and if I claim it, will it work?

I'll google it to see if I could claim it

again thank you for the reply

AsianKid

edit:
here is as far as i can get:

asian@ubuntu:~$ sudo apt-get install linux-backports-modules-intrepid
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-backports-modules-intrepid
asian@ubuntu:~$

edit 2:
nevermind,
i hooked up my laptop to my wired connection, updated to 9.04 i believe and it fixed it

thank you anyway,
AsianKid

---

