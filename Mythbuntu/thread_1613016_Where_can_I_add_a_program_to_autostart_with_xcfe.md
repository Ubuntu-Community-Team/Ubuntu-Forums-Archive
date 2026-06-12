---
title: "Where can I add a program to autostart with xcfe"
date: 2010-11-03
forum: Mythbuntu
---

### Post by tzoom84 on 2010-11-03
This probably has been answered before but here it goes ...

I'd like to start a program (xbmc) once xcfe starts. Where is the best place to set that program to load?

I tried going to Applications->Settings->Sessions&Startup->Application Autostart" and adding /usr/local/bin/xbmc to the list. But when I do this, the program crashes upon first session start (it's fine if I log in a second for some reason).

So I am looking for alternative ways I can add it to the boot sequence ... post xcfe.

Thanks!

---

### Post by klc5555 on 2010-11-04
> **tzoom84 said:**
> This probably has been answered before but here it goes ...

I'd like to start a program (xbmc) once xcfe starts. Where is the best place to set that program to load?

I tried going to Applications->Settings->Sessions&Startup->Application Autostart" and adding /usr/local/bin/xbmc to the list. But when I do this, the program crashes upon first session start (it's fine if I log in a second for some reason).

So I am looking for alternative ways I can add it to the boot sequence ... post xcfe.

Thanks!

Sometimes programs that don't want to autoload quite correctly at xfce4 startup will do so if autostarted from an autolaunched xterm. 

That is to say, in the autostart menu you put something along the lines of:  xterm -e /usr/local/bin/xbmc

I don't know if it will work in this case, but might be worth a try.

---

### Post by tzoom84 on 2010-11-04
Hmm, no luck. Xterm started it fine but as soon as I press any key, it auto logs me out of that session. Funny thing is when I log back in manually, there's no problem as
the software loads with no error. Curious why it kicks me the first time every
boot.

I'll play more after work.

---

### Post by tzoom84 on 2010-11-05
Another update:

Still no luck. I've tried switching to Kubuntu and Xubuntu but they both had the same issue.

Get this though ... if I DISABLE automatic login (force myself to log in first), I DON'T have the problem. So somehow, the login screen is mixing up with xbmc starting.

Any ideas?

---

### Post by nickrout on 2010-11-07
Try a different approach?

Set up a mythtv menu entry to start xbmc.

---

### Post by tzoom84 on 2010-11-08
Yeah that's what I ended up doing this weekend after a fresh install. I prefered to have xbmc on start because I use it more. but 1 button press to go from mythfrontwnd to xbmc is no biggie

---

