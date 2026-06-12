---
title: "borked system"
date: 2011-01-04
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by rburkartjo on 2011-01-04
i knew this was going to happen when i upgraded form 10.10 to 11/04. retired and have the time to fix.
i want to run through the whole testing cycle this time. when it works it works. i cant boot into the unity or classic desktop. i forgot but what is the best command to use from the commandline to upgrade and update. any ideas of a fix at this point. tks

---

### Post by cariboo on 2011-01-04
You can start in recovery mode, and once at the menu drop to a netroot prompt. I would suggest you run:

```
sudo apt-get -f install
```

first just to make sure the upgrade is completed. Then install aptitude, as it isn't installed by default:

```
sudo apt-get install aptitude
```

then run:

```
sudo aptitude update && sudo aptitude safe-upgrade
```

---

### Post by rburkartjo on 2011-01-04
car nice talking to you again
tks for the help will try
the way it is now i can access my desktop all my icons show.
but there is no top menu bar. no app/etc so can access anything. will keep playing with it.

---

### Post by rburkartjo on 2011-01-04
car did what you said no changes. but i think i know what the problem is i had my monitor set at 1440 X 900 before i upgraded and that is too high it wont let me read or even access the top panel. i know that it is still there because my gmail notifier popup up below where the top panel bar used to be visabe. how could i change my screen res to lets say 800 X 600 by the commandline/tks

---

### Post by cariboo on 2011-01-04
You could start in failsafe X from the recovery mode menu, then set the screen resolution from the desktop.

---

### Post by rburkartjo on 2011-01-04
this is how i fixed
i opened a folder that had games for my wife on the desktop

then usr/share/applications/monitor reset to lower resolution

then ctr/alt/backspace

logged back in and worked only can get a res of  1152 x 864 can live with that

everything else is working fine

---

### Post by ronacc on 2011-01-05
what video card or gpu do you have ? you may have to install a driver for it to get back to full resolution , check system>administration>additional drivers .

---

### Post by rburkartjo on 2011-01-05
ron i have a great new graphic card however ubuntu and even windows7 just dont like. supposedly it is going to be supported when 11.04 goes public. will see if that happens

---

### Post by rburkartjo on 2011-01-05
i installed a ati radeon 9200 256mb pci card

---

### Post by rburkartjo on 2011-01-05
ron when i went to their website and downloaded the recommended drive it borked my system and had to reinstall. dont want to do that again

---

### Post by ronacc on 2011-01-05
I can't help with ATI I'm Nvidia here on all my boxes , mabye someone with an
ATI card will chime in with some ideas .

---

### Post by jerrylamos on 2011-01-05
> **ronacc said:**
> I can't help with ATI I'm Nvidia here on all my boxes , mabye someone with an
ATI card will chime in with some ideas .
Compiz is busted on ati radeon mobility 7500 but does work on ati radeon xpress 200.  Or at least works until the next dread natty update.

On the 7500 installing from the 2nd line in CD live, an xorg.conf specifying "radeon" ("ati" won't work) and a lot of command line stuff (see: "No Gnome panel") I was finally able to get enough up to logout and log back in setting "classic".  Since it is at least able to boot now let me try an update to see if it capsizes again.

CD Live is pretty badly broken for "Try Ubuntu...." on the 7500.  The developers have chosen not to have a "classic" boot that I've discovered.  Seems to always try Ubuntu and Compiz doing very fancy graphics eye candy stuff before Ubuntu is booted far enough up to recover from problems.

Jerry

---

