---
title: "strange gksudo behavior"
date: 2011-02-04
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ronacc on 2011-02-04
I am getting strange behavior when ever anything gui that requires root privileges is invoked  . For example synaptic ( started from menu or desktop icon) or something run with gksudo (but not sudo) from terminal . The screen goes blank with the password box appearing in the middle, on entering your password the desktop returns and the program starts normally .

edit: this started with last nights update and a large update this AM did not clear it .

---

### Post by Quackers on 2011-02-04
Just a little white rectangle with a flashing cursor in it, to put your password in? I've had that once or twice. It seems to have righted itself somewhere along the line :-)

---

### Post by ronacc on 2011-02-04
yes thats the one . as I noted in my edit to the above this AM's update didn't fix it .

---

### Post by Quackers on 2011-02-04
From memory, I think a couple of reboots seemed to fix it for me - but don't quote me on that :-)

---

### Post by ronacc on 2011-02-04
I'll give that a try , after all were here to test:lolflag:

---

### Post by Quackers on 2011-02-04
Testing, testing, 1, 2, oops!

---

### Post by ronacc on 2011-02-04
well I tried 2 reboots and 1 full shut down and poweroff and restart no help , checked for new updates found none , I'm 64bit here and running "classic desktop".

---

### Post by Quackers on 2011-02-04
I'm on 64 bit too, but running desktop edition at the time, with unity. It'll probably wander off on its own, which is how it arrived :-)

---

### Post by ronacc on 2011-02-04
yeah , I never file a bug until something has persisted for awhile .

---

### Post by mc4man on 2011-02-04
Sounds like you're having some graphical glitch with apps that when the auth. box pops up the screen darkens behind. Probably not related to the continuing window issues, though you never know.
(don't think that's a config item (darken screen),, remember seeing but possibly in a source file

one app that's quite likely to cause an issue is synaptic, try to refrain from maximizing it.

A slight workaround would be to revert to a sudo that uses the auth timeout, that would prevent an auth. popup during the timeout period or you could adjust the time from default of 300 sec or whatever it is. 
(or eliminate needing a password for sudo after login altogether - I do that here - once per session

Edit:
while probably not a factor here, (caused issues elsewhere), you could ck. in ccsm > OpenGl and make sure lighting is disabled
The default was recently changed to disable it, was causing some problems, particularly w/ the rotate plugin

---

### Post by Quackers on 2011-02-04
auth timeout hasn't worked here for weeks! Every time I open synaptic I have to enter my password - evin if I closed 20 seconds ago! It's ridiculous when you are only checking for updates to need to enter the password! This behaviour stopped in Meerkat for a while, but obviously somebody decided to regress........again!

I even posted my gratitude about it :-)  Wasted effort :-(
[http://ubuntuforums.org/showthread.php?t=1585452](http://ubuntuforums.org/showthread.php?t=1585452)

---

### Post by mc4man on 2011-02-04
> auth timeout hasn't worked here for weeks...
I'm not sure what's up with that, filed a bug (unconfirmed), quite some time ago with no response on. ( see several possibilities there - there is an existing bug, no time yet to triage, is an upstream issue or that is the new intention.
[https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/692391](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/692391)

I've done as I described in your prev. thread and is working fine (no password after login needed for sudo which inc.'s synaptic.

Ot. I see no indication that there is any 3d solution for nvidia in A2, which returns first (nvidia or nouveau 3d), who knows, personally can't consider nouveau 3d anything more than a temp solution, if even that.

---

### Post by Quackers on 2011-02-04
> **mc4man said:**
> I'm not sure what's up with that, filed a bug (unconfirmed), quite some time ago with no response on. ( see several possibilities there - there is an existing bug, no time yet to triage, is an upstream issue or that is the new intention.
[https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/692391](https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/692391)

I've done as I described in your prev. thread and is working fine (no password after login needed for sudo which inc.'s synaptic.

Ot. I see no indication that there is any 3d solution for nvidia in A2, which returns first (nvidia or nouveau 3d), who knows, personally can't consider nouveau 3d anything more than a temp solution, if even that.
I know, I posted in it on 26-1-11 :-)

---

