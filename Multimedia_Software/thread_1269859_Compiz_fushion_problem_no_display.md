---
title: "Compiz fushion problem: no display"
date: 2009-09-18
forum: Multimedia Software
---

### Post by mojo dodo on 2009-09-18
I installed the Compiz fusion settings manager according to these instructions:

[http://linuxowns.wordpress.com/2008/09/11/new-to-ubuntu/](http://linuxowns.wordpress.com/2008/09/11/new-to-ubuntu/)                           

everything was fine until i checked one setting in compiz (I think it was window fade, or something like that) and then my display turned black. When i restart and log back in i can see the desktop and menus until i click anything, at which point the display goes black again.

My machine may not have the graphics capability (no fancy graphics card), or it may have something to do with the fact that i have to output the display to a monitor, since my laptop lcd is cracked (due to a runaway nunchaku incident).

im using jaunty

please help...

---

### Post by mojo dodo on 2009-09-20
If anyone has the same problem, i fixed it by doing this:

1. Removed compiz (in recovery mode terminal with networking)

sudo apt-get purge compiz-core && sudo apt-get autoremove

2. repaired broken packages and repair graphics problems (in recovery mode)
    I'm not sure if this was necessary

3. reinstalled compiz

sudo apt-get compiz compiz-core

4. rebooted and enabled enhanced visual effects in system>preferences>appearance

---

