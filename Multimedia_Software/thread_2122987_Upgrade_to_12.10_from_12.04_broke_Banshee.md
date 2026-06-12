---
title: "Upgrade to 12.10 from 12.04 broke Banshee"
date: 2013-03-06
forum: Multimedia Software
---

### Post by reswob on 2013-03-06
I used a CD/DVD to upgrade to 12.10 and during that upgrade, I got a window saying that several packages could not be moved or upgraded and would need to be reinstalled.  Ok, no problem.  But when I logged in for the first time and clicked on Banshee to start playing some tunes, nothing happened.  When I tried to start if from the terminal I got the following message:

Unhandled Exception: System.TypeLoadException: Could not load type 'Banshee.ServiceStack.DBusServiceManager' from assembly 'Banshee.Services, Version=2.6.0.0, Culture=neutral, PublicKeyToken=null'.
[ERROR] FATAL UNHANDLED EXCEPTION: System.TypeLoadException: Could not load type 'Banshee.ServiceStack.DBusServiceManager' from assembly 'Banshee.Services, Version=2.6.0.0, Culture=neutral, PublicKeyToken=null'.


I've removed Banshee (apt-get remove and apt-get --purge remove) and reinstalled several times.  Still get the same error.
Searching on Google turned up two links, but neither had a solution.  Has anyone seen this and if so, how do I get my music playing back?


BTW, Rhythmbox doesn't work either (and it did before).  I will open a separate post for that since the error is different.  If they turn out to have the same cause, I will make sure that gets noted.

---

### Post by mc4man on 2013-03-06
I would make sure I was fully updated (& wasn't using any ppa that could affect banshee or rhythmbox.

Them maybe create a new user, login & see if either work.
If so then would look for & delelte or move to a .bak the associated local  config files, found in any of these locations
~/.gstreamer-0.10
~/.config
~/.cache
~/.local/share

Probably would first start with  - 
~/.gstreamer-0.10 & delete file inside

---

### Post by reswob on 2013-03-06
Thanks for the suggestion.  No luck.

---

### Post by reswob on 2013-03-06
.

---

### Post by mc4man on 2013-03-07
Seen that error previously (banshee), but no real confirmed fixes.
Maybe purge banshee then remove all it's dependencies that can be safely removed, then re-install

```
sudo apt-get purge banshee && sudo apt-get update
```

Then run this as a sim, if looking ok then do for real,(remove red)  or post output first if unsure
```
sudo apt-get [COLOR="#FF0000"]-s [/COLOR]autoremove
```

(you're looking to remove all the libmono*, libdbus-glib1.0-cil,  libdbus1.0-cil, libgtk2.0-cil & a few other packages

---

### Post by robertmf on 2013-03-28
[COLOR="#800000"]Ditto for me.  Neither banshee nor rhythmbox working now with 12.04.   [/COLOR]

**SOLVED**
[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

---

