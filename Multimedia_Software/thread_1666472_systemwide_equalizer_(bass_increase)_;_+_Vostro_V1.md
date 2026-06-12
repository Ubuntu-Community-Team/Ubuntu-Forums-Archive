---
title: "systemwide equalizer (bass increase) ; + Vostro V130 install advice"
date: 2011-01-13
forum: Multimedia Software
---

### Post by iaw4 on 2011-01-13
I bought a $400 Dell Vostro V130, and decided to put 10.10 netbook remix onto it.  (Vostro V130 owners: after the reboot into the new system, there is no GUI.  worse, after log in, a startx means the screen goes dead.  fortunately, a power key event is still detected, so reboot still works cleanly.  after I did a full apt-get update, apt-get dist-upgrade, and apt-get upgrade, the screen and remix worked.)

I would now like to increase the bass, systemwide (so that youtube gets sound that is a little better).  the speaker icon on the top right gets me into sound preferences, but I do not see an equalizer.  anyone know where to find one?

/iaw

---

### Post by chunky bacon! on 2011-01-14
> **iaw4 said:**
> I bought a $400 Dell Vostro V130, and decided to put 10.10 netbook remix onto it.  (Vostro V130 owners: after the reboot into the new system, there is no GUI.  worse, after log in, a startx means the screen goes dead.  fortunately, a power key event is still detected, so reboot still works cleanly.  after I did a full apt-get update, apt-get dist-upgrade, and apt-get upgrade, the screen and remix worked.)



Hey there,

Sorry I can't help you with your issues, but were your Vostro no GUI issues related to your upgrade, only?  How was your out of the box experience with the V130 and 10.04? 

I have one on order, and really am getting antsy....

---

### Post by iaw4 on 2011-01-14
No, I did a wipe and reinstall.

Just make sure you remember that you cannot start the GUI until you apt-get by hand.

---

### Post by andagreeney on 2011-03-19
Following a 10.10 upgrade for my V130, I'm having the same problem, though sudo apt-get for those three things don't work. Instead I get a huge scrolling error message about being unable to connect to various websites. Any idea what this means? Perhaps the laptop doesn't have the software for making the wired ethernet connection work?
Thanks!

---

### Post by jangirke on 2011-09-28
Try pulseaudio-equalizer.
[http://exploreubuntu.wordpress.com/2010/04/18/equalizer-for-pulse-audio/](http://exploreubuntu.wordpress.com/2010/04/18/equalizer-for-pulse-audio/)
From Diggs:
         
         Go to System-Admin-software sources-other software and add this -
 ```
ppa:psyke83/ppa
``` Then bring up System-admin-synaptic package manager and search for -
 pulseaudio-equalizer
 Click to install.

---

