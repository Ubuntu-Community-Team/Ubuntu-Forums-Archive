---
title: "ps3 remote mythtv"
date: 2009-05-03
forum: Multimedia Software
---

### Post by lift28 on 2009-05-03
ps3 remote bluetooth mythtv
here is a link to get it going with a python script. 
[http://www.mythtv.org/wiki/Ps3_remote](http://www.mythtv.org/wiki/Ps3_remote)
works for 8.10 and 9.10 
its tweak for mythtv and mplayer

i was unable to get the driver referenced in this thread working.
[http://ubuntuforums.org/showthread.php?t=874284&highlight=ps3+remote](http://ubuntuforums.org/showthread.php?t=874284&highlight=ps3+remote)

if anyone has been able to make the driver work on a 9.04 clean install please post how 
thanks

---

### Post by balderson on 2009-05-05
I'm also having trouble with this. Please help!!

---

### Post by billy_big_time on 2009-05-17
I had success following a guide on the xbmc forums:
[http://xbmc.org/forum/showthread.php?t=50717](http://xbmc.org/forum/showthread.php?t=50717)
with the additional steps suggested lower down the thread of adding uinput to /etc/modules and creating a new /etc/udev/rules.d/40-permissions.rules file.

---

### Post by lift28 on 2009-05-30
> **billy_big_time said:**
> I had success following a guide on the xbmc forums:
[http://xbmc.org/forum/showthread.php?t=50717](http://xbmc.org/forum/showthread.php?t=50717)
with the additional steps suggested lower down the thread of adding uinput to /etc/modules and creating a new /etc/udev/rules.d/40-permissions.rules file.

thanks for your reply
what success did you have?
blueman will allow pairing and re-pairing on reboot, battery change and allows the following to work natively with uinput: numbers,arrows,enter(center pad) and return.
which leaves all the other buttons unused 
i was unable to make the bd driver to work or get lirc to work.
xev shows only have of the buttons working with uinput
wish they all work then a remap would do the trick:(

---

### Post by lift28 on 2009-05-30
> **lift28 said:**
> thanks for your reply
what success did you have?
blueman will allow pairing and re-pairing on reboot, battery change and allows the following to work natively with uinput: numbers,arrows,enter(center pad) and return.
which leaves all the other buttons unused 
i was unable to make the bd driver to work or get lirc to work.
xev shows only have of the buttons working with uinput
wish they all work then a remap would do the trick:(

using blueman is nice since the cakemote-mythtv.py get along then the wife can put in new batteries and have minimum usage in myth.

---

