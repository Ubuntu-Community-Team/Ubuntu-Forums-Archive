---
title: "Hardy froze - now no Wireless Connection"
date: 2009-01-14
forum: Networking &amp; Wireless
---

### Post by 2CV67 on 2009-01-14
Hi guys!

As a preliminary to making a system image with Remastersys, I decided to switch off my Wireless Connection, something I otherwise never do.

I went to "Network settings", signed in, saw "Wireless connection" alone was ticked, and unticked it.
I got the signal something was running (mouse pointer turned to timer) then that pointer froze & I was stuck.
Num Lock showing steady.
No caps lock or scroll lock flashing.
No reaction to REISUB or Ctr/Alt/Sup etc etc
So powered off.
Rebooted OK but no Internet connection, as shown by Evolution & Firefox.
In Network settings, Wireless connection is still ticked.
Tried unticking it again - no freezing this time.
On closing & opening Network settings again, Wireless connection is already ticked but no connection.
I re-entered the WEP key & all the other details look OK.

I tried booting to kernel 2.6.24-22 (instead of 24-23) but same condition.

The same hardware is still working OK in XP (where I am now...).

I never had anything like this before.
I do get systematic hard kernel panics (caps lock & scroll lock flashing) with every new kernel until I install backports modules (presumed related to RT2561) but never any problem after installing backports.

Suggestions please?

Thanks!

---

### Post by 2CV67 on 2009-01-14
After a long pause & no other action - it is working normally again...

---

### Post by 2CV67 on 2009-01-15
This freeze is reproducible.

Any time I go to Network Settings, select Wireless Connection & try to deselect the ticked box, then the tick disappears & reappears immediately, the pointer changes to timer configuration for a few seconds then freezes.
Other symptoms exactly as first post.

I have not found a sure path to recovery, having tried a few combinations but not with consistent results.
Some combination of rebooting Ubuntu &/or router &/or waiting &/or luck...
As luck does not last forever, I think I will stop playing while with I am ahead!

I have var/log/messages traces of several freezes this morning, but they don't mean much to me.

Anybody?

Thanks

---

