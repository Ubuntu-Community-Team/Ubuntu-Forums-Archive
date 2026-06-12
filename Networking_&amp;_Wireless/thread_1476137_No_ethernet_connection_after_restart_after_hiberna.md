---
title: "No ethernet connection after restart after hibernation"
date: 2010-05-07
forum: Networking &amp; Wireless
---

### Post by terryscott on 2010-05-07
Hi,
Following upgrading my 09.04 partition to 09.10 then 10.04, all was working fine until I tried hibernate out for the first time - big mistake!
If I can get to a position where i can log on to the system, I find that my ethernet network connection is disabled and I cannot get it to restart. My 09.10 system still works ok. I am tempted to do a clean install of 10.04, even though I'll have to spend some time reloading the extra's and re-configuring.

---

### Post by oviorus on 2011-05-14
Same problem here, ubuntu 10.04.2 LTS, hibernated my machine for the first time, when I tried to restore sesion it freezes and I had to hard reset, when logged in again ethernet is not available

***Edit***

I was able to get ethernet working again by using the command

*sudo ifconfig eth0 up*

and then adding these lines at the end of /etc/network/interfaces

[I]auto eth0
iface eth0 inet dhcp[/I]

and finally the command

*sudo /etc/init.d/networking restart*

---

