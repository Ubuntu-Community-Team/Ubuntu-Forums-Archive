---
title: "flash crashed, hard reboot, network gone"
date: 2010-12-01
forum: Networking &amp; Wireless
---

### Post by forextsdjc on 2010-12-01
Hey guys writing u from my phone. Really really $%&ing frustrated.
I've been running ubuntu for two years, recently upgraded to ubuntuX64 and got everything running.

Last night I'm watching a flash video in full screen. Frame freezes, can move mouse, can hear audio of flash, key board won't respond to any commands.

Hard reboot

Upon reboot, can't connect to network. Ifconfig shows eth0 with an inet6 address no ipv4. Changed etc/network/interfaces file to;
"Auto eth0
Iface eth0 inet dhcp"
Ran sudo /etc/init.d/networking restart, walla! Nework problem solved.

Conintue watching flash video. Frame freeze crash. Hard reboot.
Now network connections is missing from task bar at top right hand corner. No ipv4 I can ping 127.0.0.1 but cannot get the dhcpdiscover to find an offer.

I've searched up and down the forums and tried some things but no luck. 
I rebooted with my ubuntu disc to see if I could get network connectivity and copy over the config but cannot get any network from there.

I tried a direct connect to modem and no love.and tried another cable
Please help, and guys I have searched the forums and tried stuff as a first step. If I missed a post that will take care of this my bad, but I did give best effort.

Your frustrated geek wannabe,
 Kush

---

