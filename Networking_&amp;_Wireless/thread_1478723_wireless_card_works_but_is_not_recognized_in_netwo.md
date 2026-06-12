---
title: "wireless card works but is not recognized in network manager applet"
date: 2010-05-10
forum: Networking &amp; Wireless
---

### Post by ~dr,j on 2010-05-10
hey everyone~
ok so far so good on my transition to lucid from karmic. few quarks and this is one of them.

i have a broadcom wireless card in my hp tx2510us laptop. i can get on my network and on line fine BUT half the time the network manager applet doesn't show in my notification area and when it does, it says i am not connected (even though i am)

if i use a screenlet to monitor say transfer rates i can see the transfer rates but if i use one to monitor my wireless signal (in karmic it was eth1) it says i don't have wireless (again even if i am online)

anyone have any ideas? this isn't like a must fix....but i like to know my signal strength so i can keep tabs on the range of my wireless network etc.

now onto the other section to post my other quark question lol
oh yeah im using the 64 bit edition of lucid
thanks in advanced everyone!
~j

p.s. i did look some already in the forum for this problem but didn't see this specific problem. most people just couldn't get their card to work...mine works fine, just says it doesnt lol

---

### Post by P4man on 2010-05-10
Sounds like this bug:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/539300](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/539300)

You may want to subscribe to it and try some of the suggest worarounds in there.

---

### Post by ~dr,j on 2010-05-11
p4man~
hi there, that thread in launchpad is basicaly it....thanks [and i must admit i spaced looking in launchpad]
thanks....there's no fix there so if anyone here has a fix that'd be awesome....and if it works ill post it there too [and give u credit :P]
~j

---

### Post by ~dr,j on 2010-05-18
p4man (and anyone else reading)~
well a reply in launchpad has given the solution to the network manager problem.
if you install 'WICD' [its in the repos, stands for 'wireless interface connection dameon'] it should show the info properly. [i.e. when your connected it will actually say your connected. and also i want to point out, my little sisters laptop has an atheros wireless chip and the network manager applet works fine for her....so i think it's due to my broadcom chip...)

p4man, thanks for showing me that thread :-)
~j

---

