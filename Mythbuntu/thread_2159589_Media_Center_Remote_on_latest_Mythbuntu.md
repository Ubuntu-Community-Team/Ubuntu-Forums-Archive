---
title: "Media Center Remote on latest Mythbuntu"
date: 2013-07-03
forum: Mythbuntu
---

### Post by clueo8 on 2013-07-03
I installed the latest mythbuntu for my frontend, and I have the original ms media center remote (philips aka mceusb I believe).

Out of the box install, no configuration yet, the OK button would not work, but up down left right did.

So I went to the IR section of mythbuntu setup and set it up for the microsoft remotes and then all was good... It installed LIRC and configured it.

Now I'm trying to get the KEY_POWER to put the computer to sleep.  I setup my USB to allow wakeup and I know thats good to go.

The only time the sleep button works is when I stop the lircd!  I noticed that upon startup that my mythtv user account runs the lircd and root runs irexec... I believe its the irexec which is allowing the sleep button to work... Upon resume, lircd starts back up and I can't put back to sleep unless I stop lircd!  Has anyone else experienced this or know how to fix it?  Thank in advance.

---

### Post by topcat5 on 2013-07-07
You might want to do some reading on the various wikis to see if your mceusb remote is identifying itself as a keyboard/mouse combination.  If so, you will not need to install lirc.

---

### Post by tgm4883 on 2013-07-07
> **topcat5 said:**
> You might want to do some reading on the various wikis to see if your mceusb remote is identifying itself as a keyboard/mouse combination.  If so, you will not need to install lirc.

That is exactly what it's doing (and why it was semi working without needing LIRC installed). He'll need to fix his keymap though. Take a look here [http://askubuntu.com/a/191202/2159](http://askubuntu.com/a/191202/2159)

---

