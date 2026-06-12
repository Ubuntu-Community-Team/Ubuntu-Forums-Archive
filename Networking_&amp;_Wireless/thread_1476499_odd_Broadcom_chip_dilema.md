---
title: "odd Broadcom chip dilema"
date: 2010-05-07
forum: Networking &amp; Wireless
---

### Post by fysicsandpholds on 2010-05-07
So i am currently dual booting Snow Leopard and Ubuntu 10.04 on my mac. Lately the ubuntu has really been growing on me but I can't get internet access because I have one of those pesky Broadcom xx43 chips that come with apples cards.
Unfourtunantly I am a total noob so basic things like installing packages are a mystery to me
when I first started ubuntu i just ran virtualbox and the packages installed perfectly
now it can't find the packages it tells me to install like when i type
g++ 
it will tell me to install g++ package which it then says does not exist
I think this is related to my internet problem
I need a way to get the broadcom drivers working on ubuntu
But I have to do it all without internet natively on Ubuntu (i can transfer files easily from my mac partition which does have internet)
I have seen this done with Edgy and Dapper, but i cant find a tutorial for Lucid
maybe I am missing something very obvious like they already built in support for it

---

### Post by pinoyskull on 2010-05-08
same here, I have a Dell Inspiron 1464 and it comes with a Broadband Wireless card, i followed the howto of craptree [1] and it fixes the problem, although I get a disconnect issue every now and then which I am trying to figure out

[1] [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/502433/comments/31](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/502433/comments/31)

---

### Post by fysicsandpholds on 2010-05-08
thanks but that was a little over my head
I eventually fixed the problem. Ubuntu has support for the driver like I expected but due to licensing issues they can't include it in their packaged drivers. What I had to do was connect it to a physical ethernet cable, at which point Ubuntu automatically recognized my card and the necesary drivers I needed.
lol but as soon as I fixed it I realized my sound wasnt working
I have an Intell ICH8 sound card if you happen to know of a quick fix, but I am sure I will figure it out eventually if you dont

---

