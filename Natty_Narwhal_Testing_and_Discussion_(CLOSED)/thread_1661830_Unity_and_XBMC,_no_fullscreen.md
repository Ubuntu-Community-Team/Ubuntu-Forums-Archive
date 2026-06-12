---
title: "Unity and XBMC, no fullscreen?"
date: 2011-01-07
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Tompalaz on 2011-01-07
Hi, sorry if this question already been asked.

So far I like what they have done with the 11.04. It's really fast. 
I have a problem with XBMC though. When I open up XBMC it goes to fullscreen, but the unity bar still shows to the left.

Is there a solution to this or is it just a cool feature of the alpha stage?

---

### Post by mc4man on 2011-01-07
Atm the autohide option (intelli-hide) is not enabled by default.
To enable either install compizconfig-settings-manager and enable it in the unity plugin setting
or from terminal
```
gconftool --type Boolean --set /apps/compiz-1/plugins/unityshell/screen0/options/launcher_autohide true
```

(at some point there may also be a 'true-hide' option which I find preferable on large screens

---

### Post by Tompalaz on 2011-01-07
Thanks a bunch!

---

### Post by castrojo on 2011-01-07
Please file a bug in unity anyway, gotta make sure XBMC works in 11.04.

---

### Post by woodbj on 2011-01-07
I get a similar problem while using a full-screen application (eg Firefox) on an second monitor. The top bar is always visible but not click-able on the second monitor but full-screen works as intended on first monitor.

---

### Post by Amaranth on 2011-01-08
Known issue. Don't know if there is a bug filed specifically but this even happens with the screensaver so we are definitely aware of it. :)

---

