---
title: "Lucid - ATI x850 on resume from S3 DVI - flickering display - no mouse cursor"
date: 2010-05-17
forum: Multimedia Software
---

### Post by zaghadka on 2010-05-17
I suspend to RAM. This works great in 10.04, but the resume has been a bit of a problem. I'm using the DVI output on my Radeon X850, open drivers. When I resume from S3, the screen will flicker, lines and funny colored dots (like a hot pixel) will appear.

Sometimes resetting with a CTRL-ALT-BKSP will jar it out of the problem. Setting option "SWCursor" to "true" might help. I'm not sure.

I'd like to get S3 suspend to work, but right now, I can't bring my X850 out of S3 stable.

I'd appreciate any help. It seems to be an Xorg problem.

All of this worked fine in Jaunty and Karmic.

---

### Post by akvik on 2010-06-14
Hi,

I have a Thinkpad T60 using ATI X1300 mobile, and my external display flickers constantly using Lucid. All worked well with Karmic. 

Found a workaround for the disappearing mouse during suspend. If I use the FN + Suspend keys on my laptop, the mouse is gone on resume. Workaround ALT+CTRL+3 and then ALT+CTRL+7.

However, if I suspend it with the menu on the gnome panel, it resumes OK.

---

### Post by Haitao on 2010-06-14
Hi!

I have the same problem with my ATI X1400 and confirm Karmic was fine (and before) as well as a new issue where now even on the laptop LCD screen itself I get some kind of flickering or greyish tone (like a grid applied to the whole screen). It looks like the screen is set at a wrong frequency maybe. I don't know enough to be able to troubleshoot.

Thanks.
Fred

---

### Post by akvik on 2010-08-23
Solved for me!

Tried the solution offered at:
[http://www.niccolofavari.com/ubuntu-10.04-lucid-issues-with-external-monitor-and-ati-radeon-card](http://www.niccolofavari.com/ubuntu-10.04-lucid-issues-with-external-monitor-and-ati-radeon-card)

> 
Solution

I just did the following (on a bare install of Ubuntu 10.04)
Fire up the terminal and type
```

gksudo gedit /etc/modprobe.d/radeon-kms.conf

```
a blank file will open up. Type in the following.
```

options radeon modeset=0

```
Save, exit and reboot.


---

