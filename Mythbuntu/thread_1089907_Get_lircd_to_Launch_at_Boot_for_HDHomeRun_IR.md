---
title: "Get lircd to Launch at Boot for HDHomeRun IR"
date: 2009-03-07
forum: Mythbuntu
---

### Post by uncle hammy on 2009-03-07
I am trying to use one of my HDHomeRun units as an IR receiver for a frontend.  I have followed the instructions from Silicondust, and have it working just fine.  However, lircd needs to be running in "udp" mode.  In order to achieve this (as per the instructions), I issue the command ( I am changing the port to match the port in Myth's general listings)...

lircd -H udp -d 6546

which doesn't work, and requires it to be issued by root...

sudo lircd -H udp -d 6546

and I am off an running, works fine.  However, I have been trying all day to get lircd to launch in udp mode at boot time, with no luck.  I have tried adding the command to the auto start apps, adding it to rc.local, creating an init.d script and simlinking it to rc2.d all with no luck.  I have messed around with sudoers to try and get lircd to automatically run with root privileges, also with no luck.   

I have checked the "enable network remote control" option in Myth's general settings which also doesn't seem to have any effect.

Can anyone please help me get lircd running at boot time in such a way that I can use the HDHomeRun IR over the network?  I'd really like to not have to go to a terminal session and enter lircd -H udp -d 6546 every time I turn this machine on.

Thanks,
Scott

---

### Post by azmyth on 2009-03-08
I've found it's best to start lirc through the /etc/lirc/hardware.conf. There's a setting that will allow you to pass arguments to lirc. When I switched from fedora to mubuntu, I tried using the same config as F in MythU with commands in modprobe.conf and rc.local and it failed for me as well.

---

### Post by uncle hammy on 2009-03-09
Thanks, that got me going.

---

