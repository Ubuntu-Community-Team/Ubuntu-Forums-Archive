---
title: "network-manager starting late"
date: 2009-08-04
forum: Networking &amp; Wireless
---

### Post by hydrotemplar on 2009-08-04
running Jaunty on an Acer Aspire One

when I start my computer, it takes about 5 minutes after booting to start network-manager.  when I type ifconfig, it recognizes lo, but not eth0 or wlan.  i've tried running network-manager in the terminal (though I don't think that's the right way to day it, it says network-manager doesn't exist) then about 5 minutes later, it starts on its own.
I also looked in my startup programs, and network-manager is set to start at boot.
and also, if i don't log in for that time, then it starts itself up like the "countdown" starts from loading the login screen rather than login itself...
any help would be much appreciated
thanks,
david

---

### Post by hydrotemplar on 2009-08-30
bump.

It's doing it again on a fresh install.  Same computer though...  It worked fine for the first week or so of the install, but just tonight for no apparent reason it started doing this again.

My hardware is standard Acer Aspire One AOA150-1329 RT, but I replaced the Atheros wireless card with an Intel Corporation PRO/Wireless 4965 AG/AGN, and I upgraded the RAM.

If anyone else has seen this issue before, I'd be grateful to at least know I'm not alone, even if you don't have a solution...

Thanks,
David

---

### Post by hydrotemplar on 2009-09-10
nobody has any idea?  I Really don't want to do a fresh install for something that seems like it should have a simple fix...

---

### Post by jward3010 on 2009-09-10
I have a mad idea, have you ever done a profiled boot up?

---

### Post by speedwell68 on 2009-09-10
> **hydrotemplar said:**
> running Jaunty on an Acer Aspire One

when I start my computer, it takes about 5 minutes after booting to start network-manager.  when I type ifconfig, it recognizes lo, but not eth0 or wlan.  i've tried running network-manager in the terminal (though I don't think that's the right way to day it, it says network-manager doesn't exist) then about 5 minutes later, it starts on its own.
I also looked in my startup programs, and network-manager is set to start at boot.
and also, if i don't log in for that time, then it starts itself up like the "countdown" starts from loading the login screen rather than login itself...
any help would be much appreciated
thanks,
david

My Acer One A150 had this problem and the fix was very simple.  Replace the standard network manager with Wicd.  Simply do this in the terminal...

```
sudo apt-get wicd
```

It will remove the standard network manager and install Wicd in it's place.  It is best to do a full restart to make sure it loads automatically at start up.

---

### Post by hydrotemplar on 2009-09-14
awesome, thank you so much, i've been putting up with that way too long...
and so far, I think I'm going to like wicd better anyway...

---

