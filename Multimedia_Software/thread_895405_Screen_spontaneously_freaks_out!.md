---
title: "Screen spontaneously freaks out!"
date: 2008-08-20
forum: Multimedia Software
---

### Post by Angus77 on 2008-08-20
This has only happened to me a couple times in the last couple days.

All of a sudden my screen will freak out like in the attachment.

Sometimes the system will freeze up, sometimes it won't.

I haven't had this problem in over a year using Ubuntu.

Dell Inspiron 531s, AthlonX2 3800, Radeon x1300, 2GB RAM

---

### Post by vprasaj on 2008-08-20
Something similar happened on my old radeon 9800 almost a year ago. I pluged my card into second computer and it works. (My artefacts were 10 times worst then yours.)

My begin to freak after I changed CPU and the clocks were different. This was the only change on that box.

I tried everything from changing drivers to repluging the card. But no luck.

The same problem appeared in M$ XP.

After out of idea I just pluged the card in to another computer. Now everything is OK.

If you have a chance, test your graphic card on another machine.

I hope that this helps you a bit to solve your problem.

---

### Post by Angus77 on 2008-08-21
Well, I don't have another machine to plug the card into (it would be nice!)

For now, I've disabled the fglrx driver, and it seems to be working fine (with no special effects).

I was surprised I could do this, because on Feisty and Hardy I couldn't get 1680x1050 resolution to work without the driver.  Now it works fine.

I don't play games or do anything really graphics-intensive, so as long as I can get my screen resolution and watch videos---bye-bye, proprietary  driver!

And I'll definitely be buying something other than ATI in the future.

---

### Post by vprasaj on 2008-09-02
Well, ATI drivers are  improving.

My fiend just saw this post and he suggested to check your voltages.

---

### Post by Angus77 on 2008-11-05
How do you "check your voltages"?

I'm asking because I've just run into the same thing on Intrepid with the 2:8.543-0ubuntu4 version of fglrx.  It was 7.x on Gutsy, so I assumed it would be different.  It was.  The screen went to garbage within minutes!  On Gutsy, I had to run the system for a while before everything went kaput.

Luckily, I'm able to run fine without the driver.  I can even use Compiz!  Which doesn't actually interest me, but it sure would be nice if I could use this piece of hardware that I wasted my hard-earned dollars on...

---

### Post by CPtAJ on 2008-11-05
I don't know, that doesn't look like a hardware problem to me. First of all, if it were a hardware problem then I doubt you'd be able to screenshot the effect. Furthermore, the behaviour of the artifacts seems limited to certain elements on-screen, another hint of a hardware-software configuration problem.

Just my 2c

---

### Post by Angus77 on 2008-11-09
Well, sometimes it only affects certain things on the screen, but it always ends up affect the entire screen.  

On Gutsy it would get to the point where I couldn't even use the mouse to logout---meaning I could still see everything even though the screen was garbled, but the cursor wouldn't move.  

I haven't run into that on Intrepid yet, but then I didn't stick with fglrx as long, either.

---

