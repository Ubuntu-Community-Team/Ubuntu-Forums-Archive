---
title: "Wireless stops working after reboot"
date: 2009-12-22
forum: Networking &amp; Wireless
---

### Post by johnmic on 2009-12-22
Hi,

I'm having problems with my wireless - after every reboot, the wireless doesn't work until I enter the command:
```

sudo modprobe b43

```This is obviously less than ideal. I tried creating a shell script to run at startup, but I'm pretty much a newbie with Linux, so I hacked together various other tutorials to try and get it running. The shell script, 'wifi-fix.sh', was created using the command 'sudo gedit /etc/init.d/wifi-fix.sh', and contains the text:
```

#! /bin/bash

modprobe b43
ifconfig eth1 up

```(It also didn't work without the line 'ifconfig eth1 up'). I then tried to remove the script, so you can get a better idea of what is going on when I put it in - this is the subsequent terminal output - it includes the original 'sudo modprobe b43' command to get the wireless working:
```

philip@Mathis:~$ sudo modprobe b43
[sudo] password for philip: 
Sorry, try again.
[sudo] password for philip: 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
philip@Mathis:~$ sudo gedit /etc/init.d/wifi-fix.sh
philip@Mathis:~$ sudo update-rc.d -f wifi-fix.sh remove
 Removing any system startup links for /etc/init.d/wifi-fix.sh ...
   /etc/rc0.d/K20wifi-fix.sh
   /etc/rc1.d/K20wifi-fix.sh
   /etc/rc2.d/S20wifi-fix.sh
   /etc/rc3.d/S20wifi-fix.sh
   /etc/rc4.d/S20wifi-fix.sh
   /etc/rc5.d/S20wifi-fix.sh
   /etc/rc6.d/K20wifi-fix.sh
philip@Mathis:~$ sudo update-rc.d wifi-fix.sh defaults
update-rc.d: warning: /etc/init.d/wifi-fix.sh missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 Adding system startup for /etc/init.d/wifi-fix.sh ...
   /etc/rc0.d/K20wifi-fix.sh -> ../init.d/wifi-fix.sh
   /etc/rc1.d/K20wifi-fix.sh -> ../init.d/wifi-fix.sh
   /etc/rc6.d/K20wifi-fix.sh -> ../init.d/wifi-fix.sh
   /etc/rc2.d/S20wifi-fix.sh -> ../init.d/wifi-fix.sh
   /etc/rc3.d/S20wifi-fix.sh -> ../init.d/wifi-fix.sh
   /etc/rc4.d/S20wifi-fix.sh -> ../init.d/wifi-fix.sh
   /etc/rc5.d/S20wifi-fix.sh -> ../init.d/wifi-fix.sh
philip@Mathis:~$ 

```I'm hoping it's as simple as I'm using a command incorrectly. If you need any more information to diagnose the problem, don't hesitate to ask. Thanks in advance!

---

