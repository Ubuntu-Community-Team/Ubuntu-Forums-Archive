---
title: "pinnacle remote stopped working after crash"
date: 2010-03-18
forum: Multimedia Software
---

### Post by samuelkarush on 2010-03-18
so i had my pinnacle remote working well with mythtv. Then my desktop crashed, so i rebooted, and the remote didnt work.(remote plugs direct into card)

 irw only recognized the input from my mouse buttons. another reboot, and then irw recognized the input from my keyboard(strange). FWIW im using a logitech wireless keyboard/mouse

 so i had previously taken the steps to make the remote receiver static on event4. somehow this broke, so i fixed it, but im still getting nothing using irw, code2, or irrecord. all 3 of these worked before the crash. mouse and keyboard work fine now 

 ran a livecd 9.10(same im running now) and had same results. 

 remote is sending, i can see the light if i point it into my cell camera. any way to tell if the receiver crapped out? seems kinda fishy it would crap out same time as the crash, but who knows.

 only thing i can see is i have devinput listed as the driver in my hardware.conf file, but i wonder if it is being used. when i run lspci -v i dont see that driver listed anywhere. never checked before it broke, so im not sure if im supposed to see it there.

 what did i break this time?ha

---

