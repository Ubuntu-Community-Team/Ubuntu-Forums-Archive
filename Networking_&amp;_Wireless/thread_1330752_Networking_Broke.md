---
title: "Networking Broke"
date: 2009-11-18
forum: Networking &amp; Wireless
---

### Post by lunchboxtheman on 2009-11-18
I upgraded from 9.04 to 9.10 and everything has been working perfectly for about two weeks.

Then, all of a sudden, the network manager wasn't showing in my notification area and I had no network.  ifconfig shows no eth0 device.

I tried doing a /etc/init.d/networking restart and it says "* Reconfiguring network interfaces...   [ OK ]" but nothing changes.

Some other threads suggest doing a /etc/init.d/NetworkManager start/stop but that doesn't exist on my machine.  All I have is /etc/init.d/NetworkManager.dpkg-backup.

Doing a 'ifconfig eth0 up' shows the eth0 device in 'ifconfig' output, but I still don't have network connectivity.

I'm not a complete newb, but I don't know enough to go much further than I have.  I really want to learn how to solve this though.

Does anyone have thoughts?

Thanks,
Lunchboxtheman


SOLVED:
I don't know why, but it turns out that NetworkManager became completely uninstalled from my system O_o.  Anywho, by a recommendation from [this]("http://ubuntuforums.org/showthread.php?p=8287481") thread, I reinstalled it.

---

