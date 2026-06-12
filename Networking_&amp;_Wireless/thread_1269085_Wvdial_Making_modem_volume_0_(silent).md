---
title: "Wvdial: Making modem volume 0 (silent) ?"
date: 2009-09-17
forum: Networking &amp; Wireless
---

### Post by rob86 on 2009-09-17
I think I'm going to use wvdial by itself instead of with a gui dialer, because all the gui dialers lack the ability to connect on start and I think I can figure out a way to get wvdial to do that. I can't seem to get wvdial to dial with the modem volume turned off though, and the connection noises are annoying.

For bonus points..can someone tell me how to make wvdial execute in the background when I boot up? I want it to be completely in the background, no sounds, no terminals popping up.. as I have a panel icon that lights up when I'm connected.

---

### Post by GeorgeVita on 2009-09-19
Hi **rob86**, I think some standard Hayes AT commands may fix 'noise':

**&#913;&#932;&#924;0** turns speaker off
**ATL0** zero volume
**ATL1** minimum volume

About running a script or 'sudo wvdial ...' at start up, you can add a line into file **/etc/rc.local** just above 'exit 0' line, without 'sudo'. Think about adding a 'sleep 3' if you want an extra delay (3 is an example for 3 seconds).

Tested as a 'logger' to show me when my modem is recognized on boot or not (it must assigned as ttyUSB0): ```
#!/bin/sh -e
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

echo -n "booting at: " >> /home/g/Desktop/MyLog.txt
date >> /home/g/Desktop/MyLog.txt
sleep 3
echo -n "after sleep time was: " >> /home/g/Desktop/MyLog.txt
date >> /home/g/Desktop/MyLog.txt
dmesg | grep ttyUSB0 >> /home/g/Desktop/MyLog.txt

exit 0
```
Note that my Ubuntu username is **g** and the output file named **MyLog.txt**
below is the output shown 2 boots (with the 3 seconds delay) with no modem recognized on boot! ```
booting at: Sat Sep 19 21:41:23 EEST 2009
after sleep time was: Sat Sep 19 21:41:26 EEST 2009
booting at: Sat Sep 19 21:44:12 EEST 2009
after sleep time was: Sat Sep 19 21:44:15 EEST 2009
```
You could also use extra checks (I do not know how) to test for a successful connection (ping? dns?). 

Regards,
George

---

