---
title: "Can't increase resolution past 800x600"
date: 2008-08-08
forum: Multimedia Software
---

### Post by step_hane on 2008-08-08
I read a rather long post about this in ubuntu forums, but none of it works for me.

I'm running 8.04 on a compaq Presario 6016US with an Envision H190L.

The monitor won't autodetect (although I can probe for horiz and vert refresh rates).

When I try to dpkg-reconfigure, I never get asked about settings no matter what flags I use.

When I manually edit the xorg.conf file and add details about resolution (that I know my monitor can handle), I just get a blank screen that I can't bypass.

Also, when I accept using the video drivers from nvidia that ubuntu suggests I use, I get weird freezes and reboots and still no resolution increase. I've tried to install legacy drivers to see if that would help, but that didn't work either (don't remember what happened).

Any help would be appreciated!

---

### Post by xc3RnbFO8P on 2008-08-08
Try
atl+f2
gksudo displayconfig-gtk 
try to find your monitor,
if you cant find it,
Choose Generic
and resolution that your monitor supports

---

### Post by KoolPenguin on 2008-08-08
Ubuntu should be able to set it up in most cases, but you could try running from a terminal "gksu displayconfig-gtk" (without the quotes) and select your monitor and graphics card.  I had to do this with my laptop and a couple of other computers and it worked.

Edit: I see someone beat me to it...give it a try.

---

### Post by nbayiha on 2008-08-08
Try this thread .

[http://ubuntuforums.org/showthread.php?t=880787](http://ubuntuforums.org/showthread.php?t=880787)

---

### Post by step_hane on 2008-08-08
Thank you. I was in that area below, but I thought I needed to hit add or edit instead of just oking out of that screen. That's terrific!


I'll post back about the nvidia driver issue.

How do you "Thank" someone?

---

### Post by step_hane on 2008-08-08
Figured out the thanking and so far the nvidia driver is working awesome! I had to use envyng-gtk. The usual installation wasn't working for me.

Have a nice weekend everyone.

---

