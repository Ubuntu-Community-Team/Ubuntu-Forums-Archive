---
title: "complete white screen after login"
date: 2008-04-28
forum: Multimedia Software
---

### Post by koreshd on 2008-04-28
So after I have entered my password and logged in my screen goes completly white. 

Im guessing this has to do with that I installed the ATI drivers (through the add/remove option) - though I had no problems until I had to restart because of firestarter crashed some time later.

I have a radeon 1950XT and im using the latest 8.04 ubuntu.

How can I solve this? Can I use the ATI drivers at all? I can get to the commandline by the recovery boot alternative but my terminal skills are not too great yet... :confused:

---

### Post by koreshd on 2008-04-28
Ok solved it, incase any other nwb has this problem I typed this at the recovery root console:

[PHP]
apt-get remove --purge xorg-driver-fglrx[/PHP]

to remove the drivers...

still got much to learn ;)

---

