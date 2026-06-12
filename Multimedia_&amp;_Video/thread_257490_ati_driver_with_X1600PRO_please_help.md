---
title: "ati driver with X1600PRO please help"
date: 2006-09-14
forum: Multimedia &amp; Video
---

### Post by dave1507 on 2006-09-14
Hi, after trying several how-tos and guides I still couldn't get my 
Radeon X1600PRO 512mb AGP card to work with fglrx. I have now reinstalled Ubuntu and did the following:

sudo apt-get update
sudo apt-get install fglrx thingy
sudo aticonfig --initial

I rebooted and my desktop was like this (and still is):
[IMG]http://i5.photobucket.com/albums/y174/david150788/Screenshot.png[/IMG]
[IMG]http://i5.photobucket.com/albums/y174/david150788/Screenshot-1.png[/IMG]

when I do glxgears the system locks completely.

I am new to linux but am starting to learn how things work however I don't know how to fix this. I do know how to revert to he original driver but I don't want to because there is no 3d. I would appreciate it if anyone could give me step by step instructions of what to do, what information to post here etc as I would really like 3d acceleration. This is the only thing stopping me from using linux on a much more regular basis.

My system specs are:

2.8GHZ P4
1GB PC2700 RAM
512mb Radeon X1600PRO AGP (Sapphire)
Creative Audigy 4


Any help would be much appreciated :)

---

### Post by james99 on 2006-09-14
Check the sticky in this forum on how to [Fglrx 8.21.18 Driver install]. Go to whatevers message and click on the link. Worked for my x1600, unfortunatly firefox no longer runs. Not a biggie cause Ive also got opera. The big thing is the card is now working at last.
hope this helps

---

