---
title: "ushare hogs cpu"
date: 2011-10-10
forum: Multimedia Software
---

### Post by theone964 on 2011-10-10
I finally got the uShare daemon to startup Ushare automatically when i turn on the PC with

[PHP]sudo update-rc.d ushare start 90 2 3 4 5 . stop 10 0 1 6 .[/PHP]everything is working great, except i notice know that my ushare is using anywhere between 30-90% of my AMD Athlon II X2 250 (dual core 3.0Ghz) cpu even when the Xbox 360 is off. I found out that since its a dual core the max is 200% not 100% (100% for each cpu) but its still pretty high for a service that isnt being used at the time.

is anyone else having the same issue or has anyone else fixed this prob?

---

### Post by theone964 on 2011-10-10
solved it set DNLA to no in ushare.conf and then did

sudo update-rc.d -f ushare remove
sudo update-rc.d ushare defaults

also my directory mustve been in correct because i had /media/ instead of /media . the extra / at the end was throwing it off and also because of that the defaults wouldn't work before.

after changing the directory and resetting the rc.d ushare back to defaults again it auto starts on boot and the process shows sleeping 0 most of the time but still works great.

---

