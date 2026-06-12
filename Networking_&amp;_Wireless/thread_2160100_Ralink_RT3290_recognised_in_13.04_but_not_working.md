---
title: "Ralink RT3290 recognised in 13.04 but not working"
date: 2013-07-05
forum: Networking &amp; Wireless
---

### Post by mastablasta on 2013-07-05
So since 12.04.1 64bit didn't recognise this chip, we decided to go with 13.04. 

The first problem is that this version has **short support** and we do not know if chip will work in 13.10 or not. which is the Ubuntu experience....i would realyl prefer it to work with 12.04 and NO MANUAL driver compiling each kernel update!

I've already read the bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1049466](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1049466)

but i can only see that different people got different results. for some it worked, for some it disabled power management and for some it didn't work at all. in this case the card is recognised but when you try to connect it doesn't connect. it also doesn't give out any error (what kind of UI doesn't give any error report if device is not working?). the light is showing as if the wi-fi is off.

so the obvious and main quesiton is **[SIZE=3]how to make the wi-fi work?[/SIZE]** and why is the bug marked as resolved if it is not working? 


and just to make sure the wi-fi is working the maschine came with SUSE Linux preinstalled and the wi-fi card works just fine there. eventhogh the SUSE SP2 is from February last year (which is before 12.04) and it has in general older packages than 12.04.

so manufacturer is not to blame it seems. hardware is definatelly linux compatible.

---

### Post by praseodym on 2013-07-06
Did you check this one:

[http://forum.ubuntuusers.de/topic/nach-update-kein-wlan-mehr-433/2/#post-5641297](http://forum.ubuntuusers.de/topic/nach-update-kein-wlan-mehr-433/2/#post-5641297)

---

### Post by mastablasta on 2013-07-07
we've managed to get it working. Now to get it working (with 13.04) we actually had to unplug the cable and force/make it to connect to network. However the button to turn off the wi-fi is not working.so the button is alway showing as if the wi-fi is off no matter what (even when it is on and wokring). the conenction appears to be stable and speed is ok. 

how to make the button work so they can turn it off when not needed?

btw disk got formated Kubutnu got installed as well as few programmes. not that i knew which GPU drivers one needs to pick so i just selected the first option available.

i will have a look at the link though it seems to me the one in the link does the manul driver compile as in udnerstand. which is not what i want as every kernel update will need recompiling. and this is not the user that is willing do this. i wouldn't be either. if other distros have it working out of the box Ubuntu also has to do it.

---

### Post by praseodym on 2013-07-07
No, dkms will compile the linked driver automatically when the kernel is upgraded.

---

