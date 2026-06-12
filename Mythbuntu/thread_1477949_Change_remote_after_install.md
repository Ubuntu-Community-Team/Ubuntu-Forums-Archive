---
title: "Change remote after install?"
date: 2010-05-09
forum: Mythbuntu
---

### Post by SquareRootofBlue on 2010-05-09
Despite selecting the right option for my remote during installation I have not been able to get it to do anything. I can currently only control it using a keyboard which is not ideal and it at least partially worked under 10.04, albeit with a slightly different model. I'd like to try telling myth to use a similar model to see if I get any further but can't see how to change it after installation. Unfortunately I can't find an option to change it in either mythbackend or mythfrontend, is it possible to do so after installation?

---

### Post by ian dobson on 2010-05-09
Hi,

Maybe you can use mythbuntu-controlcenter to change the lirc remote.

Otherwise you need to manually edit the lirc configuration files.

Regards
Ian Dobson

---

### Post by SquareRootofBlue on 2010-05-09
Thanks, I found the option in the Control Center but it didn't make any difference. On the lirc configuration files, how do I know what they should look like?

---

### Post by williammanda on 2010-05-09
> **SquareRootofBlue said:**
> Thanks, I found the option in the Control Center but it didn't make any difference. On the lirc configuration files, how do I know what they should look like?

You will need to look at:

/etc/lirc

for 2 files:

hardware.conf and lircd.conf

These files will tell you the remote being used.

---

