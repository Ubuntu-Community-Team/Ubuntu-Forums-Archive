---
title: "No Sound although Snd Card detected"
date: 2011-12-29
forum: Multimedia Software
---

### Post by ArktischWalder on 2011-12-29
I have been reading through thread after thread to find a solution to my problem, but so far have come up with nothing.  I just bought a new laptop from Gateway, and have installed Ubuntu on it.  My sound works when I am running Windows 7, and it was working the first two or three times I ran Ubuntu.  I have not messed with any of the system settings at all, let alone regarding sound, but now, sound no longer works in Ubuntu.  Alsamixer detects my sound card, as does lspci -v and aplay -l.  I have checked in alsamixer and made sure nothing was muted.  I have tried purging and reinstalling my sound packages.  I made sure my user was a part of the audio group.  I do not know what else to try.

---

### Post by lidex on 2011-12-31
> **ArktischWalder said:**
> I have been reading through thread after thread to find a solution to my problem, but so far have come up with nothing.  I just bought a new laptop from Gateway, and have installed Ubuntu on it.  My sound works when I am running Windows 7, and it was working the first two or three times I ran Ubuntu.  I have not messed with any of the system settings at all, let alone regarding sound, but now, sound no longer works in Ubuntu.  Alsamixer detects my sound card, as does lspci -v and aplay -l.  I have checked in alsamixer and made sure nothing was muted.  I have tried purging and reinstalling my sound packages.  I made sure my user was a part of the audio group.  I do not know what else to try.
Let's take a look. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by ArktischWalder on 2011-12-31
Here is the output.

[http://www.alsa-project.org/db/?f=5994c4ac8b](http://www.alsa-project.org/db/?f=5994c4ac8b)

---

### Post by MoreOrLess on 2011-12-31
> **ArktischWalder said:**
> Here is the output.

[http://www.alsa-project.org/db/?f=5994c4ac8b](http://www.alsa-project.org/db/?f=5994c4ac8b)
Your link points to a blank page..

---

### Post by ArktischWalder on 2011-12-31
That's strange.  Here it is again.  Sorry about that.

And apparently I'm extremely new to posting links in forums, because when I preview this post, the link works...but when I actually posted it, it stopped working.  SO...I'm attaching the locally saved file.  As a txt it was too big to attach, so I bzipped it.  Sorry for any inconvenience in this.

---

### Post by ArktischWalder on 2011-12-31
Well, I feel silly.  Every time I have a problem and finally break down and take it to a forum, the problem fixes itself.  My sound is now currently working.  I don't know what I did to fix it...and I don't know what was wrong to begin with...which is equally as vexing because I like to understand the problems I run into.  But thanks to those who took the time to start helping me out.

---

### Post by lidex on 2012-01-01
> **ArktischWalder said:**
> Well, I feel silly.  Every time I have a problem and finally break down and take it to a forum, the problem fixes itself.  My sound is now currently working.  I don't know what I did to fix it...and I don't know what was wrong to begin with...which is equally as vexing because I like to understand the problems I run into.  But thanks to those who took the time to start helping me out.

It appears alsa is using the generic parser for your codec. An alsa upgrade may be helpful - this problem could resurface intermittently. But I cannot advise on your system since you are using debian.

---

### Post by ArktischWalder on 2012-01-02
You were right.  The problem is intermittent.  I just restarted my computer, and the sound is no longer working.  And yes, I am using Debian.  I tried booting into Ubuntu and running that script (alsa-info.sh), but it wouldn't run.  It might have been due to the fact that my Internet wasn't working at the time.  Anyway, I am going to try running it from Ubuntu again and see what you think.  In the mean time, I want to try updating my alsa.  Is that something I can use my package manager to do?  I ask because my alsa-base package is at its newest version (at least on Debian).

Also, ubuntu is Debian based...and both Ubuntu and what I'm using use the apt-get cmli package manager.  So is it possible that the fix for Ubuntu would be at least similar to the fix for my Debian distro?

Also, if I include the output from alsa-info.sh from both distros, would you be able to tell if the problem is the same for both?  I included the output from both distros.

Thank you so much for looking into this for me.

---

### Post by MoreOrLess on 2012-01-02
Try using a newer distro, kernel. The alsa upgrade script in lidex's sig should work if you run a custom kernel in Debian that you don't update.
[https://bugs.launchpad.net/ubuntu/+bug/783582](https://bugs.launchpad.net/ubuntu/+bug/783582)

---

