---
title: "Wifi problem on HpNotebook"
date: 2012-10-16
forum: Networking &amp; Wireless
---

### Post by dep0 on 2012-10-16
Hi, i have just installed Ubuntu 10.04.4 LTS on my hp notebook (cause it  was kinda old for a newer distro) but i cannot connect on wifi.
I run the Hardware Driver application a few times but, as it seems, there are no proprietary  drivers for my system.
I should also point out that there is a key in my keyboard that handles  wireless connection but it seems to lost its use right after the  installation.
Any suggest? Any help is welcome.
Thank you in advance for your time.

---

### Post by coldraven on 2012-10-16
There are lots of threads about this usually invoking the "rfkill" command.
If the wifi was switched off when you installed it won't be detected and you cannot install the driver.
My HP has a touch sensitive  button on the bezel and I was stumped when trying to get it back on. My solution was to go into the BIOS setup and select "Restore Defaults", the wifi light will come on and then do a fresh install.
If I let it boot into the existing installation it would switch it back off again.
Not the neatest solution but it worked for me.

---

