---
title: "Compiz refresh rate blank"
date: 2013-10-10
forum: Multimedia Software
---

### Post by ruddi on 2013-10-10
When i try to change the refresh rate in compiz it just goes blank when i hit the back button, close compiz or restart and it is always just blank. Had similar problems with Ubuntu 13.04
any idea on how I can permanently set the refresh rate? :)

System:
Ubuntu 13.10 (upgraded to 13.10 to see if the refresh rate would be fixed..)
i7 3770K
Geforce 760 with driver 331.13 

And yes I have googled it with no luck :(

Thanks in advance :)

---

### Post by ruddi on 2013-10-12
Any help would be greatly appreciated :)

---

### Post by hobosexualities on 2013-10-30
Not that this is helpful, but I'm having the exact same issue. The refresh rate is blank and anything entered disappears and doesn't take effect.
Ubuntu 13.10
i5 2500
Nvidia 560 ti with driver 331.13 (the issue also appears with driver 325).

I previously used a startup script to force compiz to 60 to fix some screen tearing issues (as it previously used to try to reset itself to 50 every reboot). So, I'm now experiencing screen tearing again.

I've yet to come across a fix for it. I've tried reinstalling compiz to no avail.

If I come across any workaround I'll be certain to forward it your way.

Cheers,

edit:
There is a bug page on launchpad with others with this bug since 13.10, but as of yet no fix that I can see.
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1194009](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/1194009)

---

### Post by mc4man on 2013-10-30
Somewhat a weird issue - 
at least here while it always shows blank in compiz when opening it is actually already at the default, (60/59.95) for my display. (just not shown
I can see this in ccsm by clicking on the button to set to default, nothing happens. If I change the value then clicking on the button resets back to the default of 60 & is displayed at that point.
xrandr always reports the correct rate for me anyway when using open source drivers, & when using the prop drivers it's also correct in the settings panel. (nvidia on one laptop

---

