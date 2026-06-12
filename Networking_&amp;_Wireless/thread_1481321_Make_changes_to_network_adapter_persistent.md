---
title: "Make changes to network adapter persistent"
date: 2010-05-12
forum: Networking &amp; Wireless
---

### Post by nomaan on 2010-05-12
I have a crappy cat5 cable that only works at 10BaseT settings on any nic. 
I have a gigabit nic which I configure using;

> ethtool -s eth2 speed 10 autoneg off

Problem is that this setting doesn't stick after a reboot. How do I make the change permanent?

Thanks.

---

### Post by chili555 on 2010-05-12
```
sudo gedit /etc/rc.local
```Add a line above 'exit 0':```
ethtool -s eth2 speed 10 autoneg off 
```Proofread, save and close gedit. You should be all set.

---

### Post by nomaan on 2010-05-13
Didn't work. Does this command in rc.local run with root privileges?


> #!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
ethtool -s eth2 speed 10 autoneg off
exit 0



EDIT -- Oh **** . I just noticed the 7.04 FF on the left side. I'm on 10.04 these days. Don't know if that made a difference ... updating  ...

---

### Post by chili555 on 2010-05-13
> Does this command in rc.local run with root privileges?
Yes, indeed. > I'm on 10.04 these days. Don't know if that made a differenceIt makes none; rc.local has worked in the same manner since I didn't have a single gray hair.

I wonder if it works if you separate the commands:```
--- snip ---
# bits.
#
# By default this script does nothing.

ethtool -s eth2 autoneg off
ethtool -s eth2 speed 10

exit 0 
```

---

### Post by nomaan on 2010-05-19
It did.. Thanks!!!

> **chili555 said:**
> 
I wonder if it works if you separate the commands:```
--- snip ---
# bits.
#
# By default this script does nothing.

ethtool -s eth2 autoneg off
ethtool -s eth2 speed 10

exit 0 
```

---

### Post by osmak on 2011-10-15
Thanks a million!!!!

I have been stuck on this issue for a day (since I am a linux newbi). All other solutions I saw did not work, but this solved the problem.

---

