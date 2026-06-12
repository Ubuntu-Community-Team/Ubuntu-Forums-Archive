---
title: "How to burn .iso files to DVD properly"
date: 2013-01-28
forum: Multimedia Software
---

### Post by Poe4 on 2013-01-28
As a warning; I am a complete and utter newbie to all things Linux/Ubuntu, etc.

I just want to do something, that while I was using Windows, was incredibly simple stupid. Evidently, as I have found with all things Ubuntu, nothing is simple. 

My problem?

I can't burn a DVD and have it play properly.

I CAN convert any file type to an .iso (devede). 
I CAN even get my various burning programs (k3b, brasero, etc) to burn the .iso files onto a DVD. 

So where's the problem? When I attempt to play the DVD everything works just swimmingly...for 45 minutes. It then stops, stutters, and fails. 

Every. Single. DVD. Fails.

This same process, on this same computer, using Windows, gave me absolutely PERFECT dvds with no playback issues what so ever. So, HEY! maybe the solution is Wine! Right?! no. No it is not. None of the programs I know to work on Windows for this work on Wine (some don't even bothering opening)...even the ones Wine's website claims to work, do not work.

I've tried burning at slower speeds.
I've tried different programs.
I've tried combing through countless forum topics and wikis, etc. (as I have done, every day, for two months in an attempt just to make Ubuntu usable for the most basic of tasks)

I am at a loss. I was so grateful that Ubuntu helped me get my piece of crap computer to work again after my Windows became corrupted and I had no other recourse. 

Now, I have a functioning computer that does not FUNCTION and it is driving me nuts.

I am about to light the computer on fire, and just wash my hands of all things linux forever. As, after 15 years of super using Windows like a BOSS and aiding others in fixing their computer issues... two months on Ubuntu has made me question my intelligence, my sanity, and whether or not I am possibly in a special computer lovers version of Hell. 

This shouldn't be this hard, guys.

---

### Post by prabhanjan on 2013-01-28
install k3b
its available for free on ubuntu software center

or even u can install nero

For 32 bit 11.04/11.10/12.04/12.10
> 

        wget -O nero-32bit.deb [http://goo.gl/VVbyn](http://goo.gl/VVbyn)
        sudo dpkg -i nero-32bit.deb
        sudo rm nero-32bit.deb



for 64 bit
> 

        wget -O nero-64bit.deb [http://goo.gl/gu369](http://goo.gl/gu369)
        sudo dpkg -i nero-64bit.deb
        sudo rm nero-64bit.deb



---

### Post by Poe4 on 2013-01-28
> **prabhanjan said:**
> install k3b
its available for free on ubuntu software center

or even u can install nero

For 32 bit 11.04/11.10/12.04/12.10


for 64 bit

I am using K3b. I also tried Brasero. Neither work.

---

### Post by offgridguy on 2013-01-28
Hello Poe4, i hope you don't give up on linux yet, i know it can be frustrating.
Probably not much help but my way of working around these issues is just use
windows for the apps. that are giving me problems.  But then i still have windows,
maybe you don't.

Burning DVD's being one of the things that i still use windows for, after experiences similar to yours.   In summation i just use whatever works.:)

---

### Post by VanillaMozilla on 2013-01-29
There is one simple thing to check.  Check the .iso directly to see if it plays.  If it plays correctly, you can rule out a hardware problem.

And by the way, how large is the .iso?

---

