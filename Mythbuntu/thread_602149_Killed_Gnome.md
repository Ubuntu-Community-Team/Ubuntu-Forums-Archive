---
title: "Killed Gnome"
date: 2007-11-03
forum: Mythbuntu
---

### Post by c_plus_plus on 2007-11-03
I decided to try using mythbuntu to simplfy getting mythtv to work. so I went to synaptic and installed the mytbuntu-desktop meta-package. I logged out, checked the mythbuntu session, then tried to log back into my gnome session. I heard only the "bump-ba-dump" part of the startup sound then it chashed. I tried Gnome-failsafe, but nautalus wouldn't start. I fixed that by killing the procces it recomended to kill, then restarting nautalus. I then decided to try Gnome without failsafe, same. Then I went back to failsafe, and got only sound with completely blank brown screen with a working mouse cursor. I am now typing this from my KDE sesion, with is the only one that works other than the mythbuntu session.

---

### Post by superm1 on 2007-11-04
Have you restarted since doing all this?  Gnome has a nasty habit of letting some stale processes stick around if you quit improperly.

---

### Post by c_plus_plus on 2007-11-04
Ok, since restarting, the gnome login manager is slow coming up, and i can only get failsafe gnome to start.
Edit: Well, technically only Gnome w/out failsafe can't start. I looked at tty8 and noticed a large box with the following text:
> LIRC IS NOT CONFIGURED

read /usr/share/doc/lirc/html/configure.html
I found out that LIRC is th remote controll (you guys probably already knew that.) Could this be the problem? If so, how do I fix it if I don't want to configure my remote yet?

---

### Post by superm1 on 2007-11-04
> **c_plus_plus said:**
> Ok, since restarting, the gnome login manager is slow coming up, and i can only get failsafe gnome to start.
Edit: Well, technically only Gnome w/out failsafe can't start. I looked at tty8 and noticed a large box with the following text:

I found out that LIRC is th remote controll (you guys probably already knew that.) Could this be the problem? If so, how do I fix it if I don't want to configure my remote yet?
This is just installed (but not configured).  It has nothing to do with the startup process of gnome.  It starts before the GUI even starts.

You can configure it if you want right now, but no urgency.  It's not affecting things.

I'm really not sure what happened to your gnome session though.  Perhaps look at ~/.xsession-errors.  Did you install Xgl?  Did you turn on compiz fusion?  You can always blow away your ~/.gconf*, ~/.gnome* directories and give your profile a fresh start.

---

