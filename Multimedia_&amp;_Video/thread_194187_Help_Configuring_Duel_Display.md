---
title: "Help Configuring Duel Display"
date: 2006-06-11
forum: Multimedia &amp; Video
---

### Post by rabid9797 on 2006-06-11
i recently(an hour ago) intalled unbuntu, this is my first time working with linux and have a very basic idea of what im doing here. i have checked my drivers and unbuntu is running my graphics card(Radeon 9600 XT) and the secondary(virtual) card for my second monitor. unfortunatley, i don't know how to setup unbuntu to run my second monitor as an extended monitor instead of just a duplicate of the first.

can anyone help me out?:-k

---

### Post by scxtt on 2006-06-11
well, good news is the ATI drivers support a duAl monitor setup - the bad news is you may not have much luck installing the drivers - it seems to be a crapshoot for some people ...

looking at my ATI control panel i see the following for "Desktop Setup":
[indent]1. Disable Secondary Monitor
2. Clone Mode
3. Extend Desktop Horizontal
4. Extend Desktop Vertical[/indent]so assuming you haven't messed w/ installing the ATI drivers at all, i will suggest my method to install the 8.24.8 drivers for your card (i don't think yours is old enough that they won't support it) ... and from what i've been reading, as of late, if you want to install 8.25.18 on Xorg7 you'll want to use ATI's installer (found on their site as well) instead ...

i'll see if i can find the link i posted about it earlier ... EDIT: [found it]("http://www.ubuntuforums.org/showthread.php?p=1115995#post1115995")

---

### Post by rabid9797 on 2006-06-11
how do i get to the ATI control panel? i really have no idea what im doing here and don't know if the vid card might already be working properly.

---

### Post by scxtt on 2006-06-12
you'll have to have installed it, take a look @ the link in my signature if you've not installed any drivers for your card ...

for me. what i mentioned above is the result of running:

[indent]$:> /usr/bin/fireglcontrolpanel[/indent]

---

### Post by genghis on 2006-06-12
Hey rabid9797,

RudolfMDLT and I are having similar problems with our video cards.  I also have a Radeon 9600 XT.  You are more than welcome to come work with us in this thread:

[http://www.ubuntuforums.org/showthread.php?t=195123](http://www.ubuntuforums.org/showthread.php?t=195123)

We have tried multiple solution with very little success.  Also in that thread I have been compiling a list of other threads which seem pertinent to the problem.

---

