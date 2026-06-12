---
title: "Volume control missing from launch panel"
date: 2010-04-30
forum: Multimedia Software
---

### Post by zeroandone on 2010-04-30
I installed Lynx 10.04 from scratch and found the audio volume control is missing from the launch panel. 

Anyone else has this issue?

---

### Post by epitaph123 on 2010-04-30
Check if Gnome Volume Control applet is included in the System -> Preferences -> Startup Applications. It is called "Volume Control" If not add it:

Name: Volume Control
Command: gnome-volume-control-applet

that will be for the next reboot, for right now press alt+f2 and type code:

gnome-volume-control-applet

Then push enter, this should make it appear right away.

---

### Post by zeroandone on 2010-04-30
> **epitaph123 said:**
> Check if Gnome Volume Control applet is included in the System -> Preferences -> Startup Applications. It is called "Volume Control" If not add it:

Name: Volume Control
Command: gnome-volume-control-applet

that will be for the next reboot, for right now press alt+f2 and type code:

gnome-volume-control-applet

Then push enter, this should make it appear right away.

Thanks, I will give it a try.

---

### Post by Windle Poonbuntu on 2010-04-30
Thanks dude, thats just what I was looking for!

Chris...

---

### Post by specimen65 on 2010-05-01
I installed 10.04 tonight and after a few reboots noticed the panel applet missing - thanks for this.

---

### Post by mrgoldy on 2010-05-01
noticed the same thing this morning.
thanks for the fix.

---

### Post by john_spiral on 2010-05-03
same issue here, thanks for the fix.

---

### Post by Crempel on 2010-05-03
Same here, thanks for your help. Is this a known gnome issue? In my case the control only disappeared a few days after the initial install and maybe 40 boot ups.

---

### Post by zeroandone on 2010-05-03
At one point, I remember that I got a gnome-volume-control crashed notification, since then the volume control has been missing.

Thanks for the fix.

---

### Post by biometricstu on 2010-08-19
> **epitaph123 said:**
> Check if Gnome Volume Control applet is included in the System -> Preferences -> Startup Applications. It is called "Volume Control" If not add it:

Name: Volume Control
Command: gnome-volume-control-applet

that will be for the next reboot, for right now press alt+f2 and type code:

gnome-volume-control-applet

Then push enter, this should make it appear right away.

Thanks, this was driving me mad. Stu

---

### Post by Zeenomorph on 2010-08-26
Same problem here.  Fix worked.

---

### Post by dulce on 2010-08-27
me too--at last! thanks:)

---

### Post by dulce on 2010-08-28
nope. i can install it but the next time i boot up its gone again.

---

### Post by dulce on 2010-08-31
still disappearing again. help?:(

---

### Post by ockron on 2010-10-17
Thanx for the fantastic advice :)

It works 100% for me ...

I upgraded from 10.04 to 10.10 and lost my volume control, after following the advice I have it back, although it's the old version and not the new one :(

Thanx again!!

---

### Post by Deref on 2011-05-08
Thanks - that fixed it for me too.

Quite remarkable that Canonical could screw up something so basic.

---

### Post by chicgeek on 2011-05-08
Somewhat related - how can I remove the volume icon?  I have no need for it with my keyboard shortcuts.  Clutter.

---

