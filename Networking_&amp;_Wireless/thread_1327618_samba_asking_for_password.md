---
title: "samba asking for password"
date: 2009-11-15
forum: Networking &amp; Wireless
---

### Post by froggger on 2009-11-15
I have a windows 7 machine that I have set up to share without requiring a password.
My other windows machines can access the shares fine, and so could my ubuntu rig too. Until just out of the blue i noticed the drives weren't connecting automatically like before.  When I tried to do it manually, they asked me for a password.  
There is nothing on my network that is passworded.  Everything is open access.  I don't even have a password on my windows 7 machine.

I have to assume that some update caused this, but i have no idea exactly when it started otherwise i'd hunt through the logs.
I updated to karmic after this started to see if that would fix it, but it didn't.

I'm considering a reinstall, but i'd prefer to avoid that if possible.

Any help?

---

### Post by froggger on 2009-11-17
bump

---

### Post by dmizer on 2009-11-17
Please see the 6th link in my sig.

---

### Post by froggger on 2009-11-20
I tried all of those steps, none fixed it...

---

### Post by froggger on 2009-11-21
bump

---

### Post by dmizer on 2009-11-21
In Win7, please post the following. Go to:

start orb > control panel > network and sharing center > click on "Change advanced sharing settings"

What options are selected here?

---

### Post by froggger on 2009-11-21
home(public is the same, minus the homegroup stuff of course)
network discovery-on
file printer sharing-on
public folder sharing-on
media streaming-on
file sharing connections-enable file sharing for devices that use 40- or 56-bin encryption(just in case that happened to be the problem, needless to say, it wasn't)
password protected sharing-off
homegroup- use user accounts and passwords to connect

---

### Post by dmizer on 2009-11-21
Please try changing "homegroup- use user accounts and passwords to connect" to "Allow Windows users to manage homegroup connections"

---

### Post by froggger on 2009-11-22
Just tried that, no dice.

---

### Post by dmizer on 2009-11-22
> **froggger said:**
> Just tried that, no dice.
Ok, I'll do some more testing when I get home from work.

---

### Post by froggger on 2009-11-24
thanks, i may just reinstall, i guess i shouldn't have messed with what worked.

---

### Post by froggger on 2009-11-28
I fixed it by using your other guide, thanks for the help
[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

---

