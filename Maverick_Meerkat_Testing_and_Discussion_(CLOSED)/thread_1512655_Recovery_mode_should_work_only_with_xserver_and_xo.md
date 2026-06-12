---
title: "Recovery mode should work only with xserver and xorg"
date: 2010-06-18
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-06-18
When i was using fglrx both in maverick and in lucid recovery mode was not working all all i got was a bright blue line at the top of the screen.
Now with xserver it's working not without errors and black parts but it works so i thought maybe it would be a good idea that no matter what 
recovery mode should use xserver and xorg just like windows safe mode so what do you think of this idea?

---

### Post by cariboo on 2010-06-18
Recovey mode works before the xserver starts, if you have broken graphics, having the xserver start for recovery mode isn't going to work very well

---

### Post by aviramof on 2010-06-18
I don't understand it do you say that if i have a problem with fglrx for instance i can't use recovery mode to try and fix it?

That doesn't sound too good for me.

And i had problems with fglrx in the past that forced me to reinstall ubuntu because he would not boot up properly.

So i'm hopping that you would try to think of a solution to this problem that i mentioned here.

---

### Post by ranch hand on 2010-06-18
You will find that all the folks on the forums here are users, not developers.

The users here on the forums are donating their time and effort to help people.  Making demands in such a cranky manner as you use is not going to get you anywhere.

This thread, for instance, shows that you have not done any research before making a suggestion on changing the entire OS.  Then, when someone points this out, you become abusive.

There is no reason for anyone here to think of a fix for your problem which you have not defined in any coherent manner.

---

### Post by aviramof on 2010-06-18
What coherent manner? it doesn't work plain and simple all i get is a blue line at the top of the screen and that it it doesn't go from there but it only happen if i use fglrx.

---

### Post by ranch hand on 2010-06-18
So use the OSS driver.

---

### Post by cariboo on 2010-06-18
From the title of your question, it looks like you are suggesting that recovery mode should start with a graphical interface, not the command line.

---

### Post by Reiger on 2010-06-18
(1) Coherent manner refers to the many issues of spelling/grammar that litter your post. I imagine it trips up people who do not have the same perception of English as you have (garbled phrases may not be as easy to read for other people), and it may even annoy some in particular since your posts tend to be brief to the point of being curt.
(2) Recovery mode is, essentially, booting to a root shell (maintenance shell). The rest is merely commands executed in such an environment. This is necessary because just about every single thing that can recover a (truly) broken system requires root privileges anyway, and quite a few cannot run in an X environment.
(3) Fglrx features a setup script/X-configuration script. Ordinarily, you would run that as root, before you bring up any X servers if you attempt to recover a broken fglrx installation.

---

### Post by aviramof on 2010-06-18
> **ranch hand said:**
> So use the OSS driver.

What is that driver?

And let me explain my self again,there were times in the past that i had problems with fglrx driver so ubuntu didn't boot properly to gnome and when 
i tried to fix it with recovery mode i was unable to enter the blue screen or command line or anything all i got was a blue line at the top of the screen and that it.

And just because of problems with fglrx i was forced to reinstall ubuntu.

So what i'm saying is that the recovery mode should behave like xp/7 safe mode in 256 colors with a basic default driver so no matter what i would still be able to enter it even if
gnome don't want to boot properly becuase of fglrx problems.

I hope that i'm more clear now.

---

### Post by mc4man on 2010-06-18
> So what i'm saying is that the recovery mode should behave like xp/7 safe mode in 256 colors with a basic default driver so no matter what i would still be able to enter it even if
gnome don't want to boot properly becuase of fglrx problems.


That is basically what recovery menu -> failsafe x is.
If you can't  enter the recovery menu then that may be from some 'self inflicted' cause(s) or something that  occasionally could happen...

---

### Post by ranch hand on 2010-06-18
> **mc4man said:**
> That is basically what recovery menu -> failsafe x is.
If you can't  enter the recovery menu then that may be from some 'self inflicted' cause(s) or something that  occasionally could happen...
You were using the OSS driver before you installed the one from ATI.  It must have worked or you would not have been able to install the one that doesn't.

Try logging into an "xterm session" and running "apt-get remove fglrx".

---

### Post by aviramof on 2010-06-18
At the moment i don't use fglrx because there isn't one for xserver 1.8 not official any way but if i install fglrx and that include in lucid and not just maverick when i try to enter recovery mode i get something like this:
[http://www.animatedgif.net/barslines/bar_eleg_e0.gif](http://www.animatedgif.net/barslines/bar_eleg_e0.gif)

at the top of screen but with no animation of course and that is why i said it should not depend on the current driver but on some default driver no matter what.

---

### Post by jocko on 2010-06-19
So you suggest that recovery mode, which is supposed to be a mode you can boot into even when xorg is completely broken, should boot into xorg? Do you not see the problem with that?
I have no idea how you would think xorg could start (even in vga mode) if you can't even get the recovery menu to display...

And I have to agree with the other posters' comments that it is hard to understand what you mean in your posts. Your posts are often quite incoherent and requires a bit of imagination to interpret. Please try to explain your problem/question as completely as you can, break up your posts into sentences and use somewhat proper punctuation.
Do you understand the difference in meaning between the two sentences below?
"King Charles walked and talked half an  hour after his head was cut off."
"King Charles walked and  talked; half an hour after, his head was cut off."

I understand that english is not your native language, but that's true for a lot of people here (including me)...

---

### Post by cariboo on 2010-06-19
I think there has been quite enough aviramof bashing, this thread is closed.

---

