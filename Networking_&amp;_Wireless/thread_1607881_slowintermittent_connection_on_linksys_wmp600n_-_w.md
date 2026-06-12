---
title: "slow/intermittent connection on linksys wmp600n - wubi 10.10"
date: 2010-10-28
forum: Networking &amp; Wireless
---

### Post by mugwood on 2010-10-28
i'm guessing that another post on this subject is going to raise eyebrows, but i'm afraid i'm not that handy with ubuntu and can't fathom which approach to take from the various other posts surrounding this adaptor :confused:

i have just installed 10.10 under wubi, first time trying to use this network card under ubuntu. works fine on XP where it connects with good signal strength to a zyxel p-600 b/g router (my 3 other machines also connect fine to this router)

i am using WPA2, it takes 30secs to 1min to connect in the first place, then runs slowly and with intermittent disconnects, reports good signal strength in network manager.

i'm not even sure what config/status i should be posting for further help, any advice appreciated! i have been fortunate enough to have 3 machines that run ubuntu flawlessly out of the box... i guess i was going to run into trouble sometime :)

---

### Post by mugwood on 2010-10-29
found the solution here:

[http://ubuntuforums.org/showthread.php?t=1606820](http://ubuntuforums.org/showthread.php?t=1606820)

this "blocklist" solution for the rt2800 looked like the easiest thing to try after spotting "RT2800" listed in my connection information, and it worked!

have now gone from unreliable 1Mb/s connection to solid 54Mb/s connection... very happy!

---

