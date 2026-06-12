---
title: "ATi Radeon Propeitary Drivers problem"
date: 2012-01-13
forum: Multimedia Software
---

### Post by dstructor on 2012-01-13
Hey all,
Quite new to Ubuntu but i have a knack of dabbling around so i did just that with all the manual driver installations troubleshooters regarding my laptop's dedicated ATi Radeon VGA card

After all failed & i had to reinstall Ubuntu 11.10 Oneric...

I opted to try & install the drivers normally, take the normal steps, screenshot it & let you guys help me

Specs:
Laptop, Lenovo G570; 3GB RAM, Core i5 2.5GHz, Ubuntu 11.10, HDD 500GB; VGA, ATi Radeon 6300 Series 1GB

After regular install & reboot through the Additional Hardware app,

Opened Terminal, here's the output of 'fglrxinfo' command:
[IMG]http://i40.tinypic.com/2zdy8nt.png

Here's the error when trying to open the AMD Catalyst program:
[IMG]http://i41.tinypic.com/121edcw.jpg

Here's the output of the 'aticonfig --initial' command
[IMG]http://i43.tinypic.com/2hpk95j.png


[SIZE=3][B]So, What's the dealyo?
How to fix it?

[SIZE=1]thanks,
D
[/SIZE][/B][/SIZE]

---

### Post by 2F4U on 2012-01-14
Did I miss that or did you run aticonfig without root privileges (sudo)? If yes, try

sudo aticonfig --initial

---

### Post by dstructor on 2012-01-14
> **2F4U said:**
> Did I miss that or did you run aticonfig without root privileges (sudo)? If yes, try

sudo aticonfig --initial
Oh, thanks.

Seems to have worked smoothly, **BUT** output of fglrx command still the same as above

**EDIT:**
After "sudo aticonfig --initial" i rebooted and Ubuntu crashed
and i cannot login low graphics mode; opening grub menu & choosing recovery mode doesn't give me the option in the next menu to open in safe mode

Recommendations?

---

