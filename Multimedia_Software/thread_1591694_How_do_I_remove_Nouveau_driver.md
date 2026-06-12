---
title: "How do I remove Nouveau driver?"
date: 2010-10-09
forum: Multimedia Software
---

### Post by rfbeck on 2010-10-09
In trying to install my NVIDIA driver, I get a message that the Nouveau driver is preventing it from installing. I have it blacklisted. 
Is there another way to remove it?
Thanks folks.
______
Robert

---

### Post by cchhrriiss121212 on 2010-10-09
I just went into synaptic and removed anything with nvidia on it.

---

### Post by rfbeck on 2010-10-09
I tried that, but the nouveau drivers seemed to reinstall themselves. The NVIDIA driver also added something to block the nouveau drivers. But that did not do the trick either. Can someone come up something? I really want to install my NVIDIA drivers.

---

### Post by rfbeck on 2010-10-12
Well, by trial and error, I got my NVIDIA drivers installed. Whose bright idea was it to put those Nouveau drivers in by default. It just screws up people who happen to like proprietary drivers.
________
pissed at Ubuntu

---

### Post by auh2o on 2010-11-24
Forget it; problem solved.

---

### Post by ephman on 2010-12-13
saying that you solved your problem and not explaining how is sort of unproductive to the community.

---

### Post by efflandt on 2010-12-13
What driver version do (did) you need?  Nvidia 260.19.26 Ubuntu packages are available for Lucid and Maverick if you know where to get them.  [http://www.ubuntuupdates.org/ppas/27](http://www.ubuntuupdates.org/ppas/27)

Once you do[FONT=monospace]:
[/FONT]```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
```you can actually install them using Synaptic. Then no fussing with nouveau and they update automatically with kernel updates.

If you install them yourself from nvidia website, they may not update for kernel updates, and you may need to reinstall.

---

