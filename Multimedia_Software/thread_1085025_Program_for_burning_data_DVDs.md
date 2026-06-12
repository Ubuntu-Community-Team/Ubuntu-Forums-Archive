---
title: "Program for burning data DVDs?"
date: 2009-03-02
forum: Multimedia Software
---

### Post by Vesa Paatero on 2009-03-02
Dear All,

Sorry if this is a bit off-topic for Multimedia & Video, but:

Which program would you recommend for burning data DVD+RW or DVD-RW discs? I have tried K3B as well as the built-in DVD writer in Ubuntu 7.10 but they have the following problems/shortcomings:

  - K3B has problems in the initial emptying/formatting the disc, and causes annouyingly many discs to become unreadable by normal means. I have been using Maxell's DVD+RW discs.

  - The built-in writer in Nautilus cannot make multi-session DVDs, which wastes space as my writing sessions could be something like 1 gigabyte.

Thank you for any help you can give.

Regards,
Vesa

---

### Post by sgosnell on 2009-03-02
Brasero works for me.

---

### Post by A. J. Rimmer on 2009-03-02
I agree with the Brasero recommendation.  I'm not on my Ubuntu machine right now, but as I recall it comes standard with the Hardy distro and is available for Gutsy from the repositories.

---

### Post by ajgreeny on 2009-03-02
> K3B has problems in the initial emptying/formatting the disc, and causes annouyingly many discs to become unreadable by normal means. I have been using Maxell's DVD+RW discs.I'm surprised about this as I have always found k3b to be the best disk burning application on any platform.  I run ubuntu with gnome not kde , but still choose to use k3b, even thiough it looks wrong on gnome, as I find it so much better than brasero.  I have never yet got brasero to work at copying a home produced CD or DVD, so no copy protection problem, obviously, whereas k3b does it without blinking and runs without a problem.

---

### Post by taurus on 2009-03-02
> **ajgreeny said:**
> I'm surprised about this as I have always found k3b to be the best disk burning application on any platform.  I run ubuntu with gnome not kde , but still choose to use k3b, even thiough it looks wrong on gnome, as I find it so much better than brasero.  I have never yet got brasero to work at copying a home produced CD or DVD, so no copy protection problem, obviously, whereas k3b does it without blinking and runs without a problem.

+1 for running k3b in Gnome.  I have done a lot of burning using DVD+RW and everything comes out just the way it should.

---

### Post by wsonar on 2009-03-02
> **sgosnell said:**
> Brasero works for me.

This

---

### Post by yther on 2009-03-02
I use k3b for all of my burning, unless I'm stuck on a Windows machine, but... oddly, I can't remember if I've ever tried to burn a multi-session DVD.  If I had, I doubt it would have been a DVD±RW, either.  What I do remember about multi-session discs, however, is that they are strange fruit, and some computers and devices won't recognize them properly.

That was just my experience... maybe I had bad luck.

I definitely got some coasters out of **k3b** because the multi-session was set to "Auto" when I shouldn't have been using it, so maybe you could check the settings there (especially the all-important "Misc." tab) if you haven't already.

---

### Post by Vesa Paatero on 2009-03-06
Alright, thanks for your input, guys!   I installed Brasero and will try it at the next suitable opportunity.

Mm, I guess DVD+-RW discs are not as common as DVD-Rs, and so operations on them may not be so well-polished in writer programs as those on DVD-R's.

-Vesa

---

### Post by punx45 on 2009-03-06
you can blank the disc pretty quickly with the command line utility wodim (replaced cdrecrod)
```
wodim blank=fast dev=/whatever the dvd is
```
there are other blank types too check man wodim for lots of info.

---

### Post by binbash on 2009-03-07
I am using nerolinux or wodim

---

