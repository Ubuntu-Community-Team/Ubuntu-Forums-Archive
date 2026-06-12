---
title: "Cannot install mencoder"
date: 2008-11-22
forum: Multimedia Software
---

### Post by ghostrc79 on 2008-11-22
I have been trying to install devede, tovid and a few other ripping/burning applications and no matter how I do it they come up with it cant install mencoder.

> The following packages have unmet dependencies.
  devede: Depends: mencoder but it is not going to be installed
E: Broken packages

I believe I have enabled all boxes in software sources so I can get access to all repositories.

I have ran get update a million times after changing things

If I use synaptics to get mencoder I get this.
> mencoder:
  Depends: libasound2 (>1.0.17) but 1.0.15-3ubuntu4 is to be installed
  Depends: libmad0 (>=0.15.1b-3) but 0.15.1b-2.1ubuntu1 is to be installed
 Depends: libmp3lame0 (>=3.98) but it is not installable
  Depends: libspeex1 (>=1.2~beta3-1) but 1.1.12-3ubuntu0.8.04.1 is to be installed
 Depends: libx264-59 (>=1:0.svn20080408) but it is not installable


Please can some one help with this, I have been scratching my head for the last two days trying to get it to work, it does not help that I have only just switched to ubuntu from vista so its a steep learning curve at the moment.

Many thanks

Matt

PS replace smilies for the number 8 ??

---

### Post by kostkon on 2008-11-25
> **ghostrc79 said:**
> I have been trying to install devede, tovid and a few other ripping/burning applications and no matter how I do it they come up with it cant install mencoder.


I believe I have enabled all boxes in software sources so I can get access to all repositories.

I have ran get update a million times after changing things

If I use synaptics to get mencoder I get this.


Please can some one help with this, I have been scratching my head for the last two days trying to get it to work, it does not help that I have only just switched to ubuntu from vista so its a steep learning curve at the moment.

Many thanks

Matt

PS replace smilies for the number 8 ??
You have some broken packages. Open *Synaptic* and follow the instructions [here]("https://help.ubuntu.com/community/SynapticHowto#How%20to%20fix%20broken%20packages") on how to repair them.

Then, try again to install the applications you want.

---

### Post by ghostrc79 on 2008-11-25
Brilliant, I will try it later.

Thanks for your help:popcorn:

---

