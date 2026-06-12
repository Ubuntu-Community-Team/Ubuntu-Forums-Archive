---
title: "Upgrading from 10.04.1 LTS hung!"
date: 2010-09-08
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by iClouseau88 on 2010-09-08
Hi,

This evening while I was upgrading my laptop from Lucid to Meerkat, I felt asleep.  When I woke up, I saw two superimposed screens:

1) Upgrading Ubuntu to version 10.10 (in the foreground)

>Installing the upgrades: configuring grub-pc

About 19 minutes remaining

2) Configuring grub-pc(in the background)

I cannot see the rest of the one in the background.  I can move the mouse but nothing else works. This has been a very long time.  I set the laptop to never sleeps.

I don't know what else to do.  Please help me!  Thanks a lot!

---

### Post by iClouseau88 on 2010-09-08
Hi,

Disaster averted, partially thanks to the following Steps 3 & 4 as suggested by [COLOR="DarkRed"]cariboo907[/COLOR] (Post#9) in a nearby thread started by zachin 2036 ("Upgraded to 10.10 Netbook from 10.04-frozen/blinking desktop on boot?"):

1. Pulled the power cable;
2. Booted into recovery mode;
3. Selected [COLOR="Blue"]netroot[/COLOR];
4. Selected [COLOR="Blue"]apt-get -f install[/COLOR]
5. Error message: dpkg was interrupted, must run "dpkg --configure -a"
6. Ran [COLOR="Blue"]dpkg --configure -a[/COLOR]
7. Selected "[COLOR="Blue"]keep local grub currently installed[/COLOR]" (because my box is multibooted);
8. Ignored Grub's warning message;
9. Select "Resume normal boot"

 Voila!

```
~$ uname -a
Linux tt888-laptop [COLOR="Blue"]2.6.35-20-generic[/COLOR] #29-Ubuntu SMP Fri Sep 3 14:49:14 UTC 2010 i686 GNU/Linux

```

:D

---

