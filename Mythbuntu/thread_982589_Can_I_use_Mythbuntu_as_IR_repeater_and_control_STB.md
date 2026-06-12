---
title: "Can I use Mythbuntu as IR repeater and control STB?"
date: 2008-11-14
forum: Mythbuntu
---

### Post by bmwman on 2008-11-14
Can I use Mythbuntu as IR repeater and control STB? Basically i want to mount my TV on the wall in the bedroom and put the cable box right behind the wall in the closet. I have USB IR receiver and IR blaster that came with one of my tuners. I want to be able to change the channel on the STB while in the room and possible if I don't go through MythTV but just Ubuntu. I did little research and seems like i need to get this [http://www.amazon.com/Cables-Go-Remote-Control-Repeater/dp/B001BLTDZA/ref=pd_bbs_4?ie=UTF8&s=electronics&qid=1226716927&sr=8-4]("http://www.amazon.com/Cables-Go-Remote-Control-Repeater/dp/B001BLTDZA/ref=pd_bbs_4?ie=UTF8&s=electronics&qid=1226716927&sr=8-4")

Is this possible and how to do it or is there any other solution??
Thanks

---

### Post by Rompalle on 2008-11-14
Yes you can use your Transmitter to blast the channels. You would run the blaster wire to the front of your STB. You need to configure LIRC to do this. And yes you can change channels from the command line with IRSEND.

take a look at the Mythtv wiki under mce remote control.

---

