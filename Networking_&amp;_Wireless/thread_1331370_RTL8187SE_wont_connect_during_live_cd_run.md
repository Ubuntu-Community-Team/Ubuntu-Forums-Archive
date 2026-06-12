---
title: "RTL8187SE wont connect during live cd run"
date: 2009-11-19
forum: Networking &amp; Wireless
---

### Post by TheYaisu on 2009-11-19
HI, i am a complete beginner here haha so bear with me :)
I have been wondering about linux for a while so i thought id give it a go, had a look on some forums and saw that people who actively saught to learn, got alot more help than people who wanted to be spoon fed. I acted on this an decided to try ubuntu and see if i can get it working with use of help files and other resources. I fear this was a mistake and i should of asked one of you guys lol.
Intitially i installed vmware and backtrack3, but i quickly realized that wasnt the way to sample a linux distro. i then downloaded the latest version of ubuntu and made a live cd. the live cd boots up well fine. but when i try to connect i am just left with the spinning icon and nothing happens. i select my unsecure NETGEAR, hit connect..... and just the spinny thing. i am using RTL8187SE wireless card, i have looked on compatible card lists and my card seems to be supported.
Would this be happening because i need a driver? or maybe because i downloaded ubuntu wrong? Any help would be greatly appreciated,
Yaisu
p.s i was planning to dualboot vista/ubuntu if wireless card works

---

### Post by TheYaisu on 2009-11-19
Me again, 
            I have checked the forums and i cannot find any posts relating to my problem, can some1 help? would be ever greatful lol.
Yaisu

---

### Post by puppywhacker on 2009-11-19
Hi,

I've recently seen a similar post (live-cd and a rtl8187se) can't recall the outcome.

I'm guessing that the module is not automatically loaded. You can check that with lshw and if I remember correctly the driver is not rtl8187 (which is a different chip!) I think that rtl8180 is compatible instead.

lshw -C network
lsmod | grep 81
modprobe rtl8180

---

