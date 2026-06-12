---
title: "Upgrading from 10.04 to 10.10 Beta Problem"
date: 2010-09-16
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Seligne on 2010-09-16
I am relatively new to Ubuntu. I have been running 10.04 LTS quite successfully on my laptop. As it is not my "production" machine, I decided to upgrade to the 10.10 Beta so that I could give the feedback of a novice user. 

That turned out to be a mistake.

My laptop now boots up with a very DOS-like interface. It asks for my user ID and password, and then hangs on a line reading "jim@jim-laptop:~$". It is evidently waiting for a command from me. 

I have searched the documentation high & low but cannot find any advice on what command to enter. I have a hunch the fix is very simple.

Can someone help me out? Thanx.

---

### Post by Claus7 on 2010-09-16
Hello,

first choose recovery mode and then choose to start with low graphics mode.

Then you should install the drivers of your graphics card.

First though I would suggest you to remove anything that has to do with xorg.conf file in case HAL does do the job.

So go to:
cd /etc/X11
and see if you have any file xorg.conf

If affirmative take a backup of this file and remove it.

Restart normally and see what you get. If its the same, then you have to start again via the recovery mode and install the drivers of your graphics card.

Hope enough info at the mo.

Regards!

EDIT: Hello and welcome to the forums!

---

