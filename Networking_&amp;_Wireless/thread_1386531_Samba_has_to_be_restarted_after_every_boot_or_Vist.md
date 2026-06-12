---
title: "Samba has to be restarted after every boot or Vista client can't use printer - why ?"
date: 2010-01-20
forum: Networking &amp; Wireless
---

### Post by drhabber on 2010-01-20
I have Cups configured HP 710C LPT printer connected to PC with Ubuntu 9.10 and after every reboot I have to restart Samba (when it's already up and running)  if I want to print something from LAN (Vista PC over wifi). Otherwise the printer is unreachable over the network but browsing shared files can be performed.

With my Debian Lenny everything works just fine and even the very same config files (smb.conf and cupsd.conf) are fully operational. I had also to disable the ECC mode in bios because the device got stuck after printing first line of any document.

Can anyone tell me what could be the cause of this all ?

---

### Post by CovenStine on 2010-01-23
I have the same issue with a HP LaserJet 1200 running 9.10 on a PPC.  I know my CUPS and samba prefs are good, because on boot the shares are all browseable, and upon samba restart the printer is accessible to os x 10.4, 10.5, 10.6, ubuntu 9.10 and XP.
However, before that samba restart, it's invisible to every OS I've tried, though I don't have 7 or Vista available to test.

My issue was solved when I solved the directions in this thread: [http://ubuntuforums.org/showthread.php?t=1313049](http://ubuntuforums.org/showthread.php?t=1313049)

> **Gazneth said:**
> I worked around this problem by adding a line to /etc/rc.local ```
sudo gedit /etc/rc.local
``` then insert this line before exit0 ```
/etc/init.d/samba restart
``` This restarts Samba and starts the nmbd process, that is causing the problem by initializing too early in the boot process. After doing this test by rebooting or a```
sudo /etc/init.d/samba restart
``` then check nmbd with ```
sudo /etc/init.d/samba status
```

The strange thing is, even after it works and a test page has succeeded from XP, the printer queue in XP still is titled "HP-LaserJet-1200 on <UbuntuComputer> Access denied, unable to connect"  ...which strikes me as odd.
Hopefully that solves your issue regardless.

---

### Post by drhabber on 2010-01-24
In the meantime I've managed to solve the problem exactly the same way - by adding restart command to *rc.local*.

Thanks for confirming this bug and letting me know that it's not because of my messy tweaking ;).

---

### Post by drhabber on 2010-05-05
Something has to be wrong with my PC, printer, Samba - that's for sure ;) or this bug is persistent. I've upgraded to Ubuntu 10.04 LTS and again printing is broken. The only solution is like before - restarting Samba. Although the command is different in the latest Ubuntu:  **/etc/init.d/smbd restart** instead of /etc/init.d/samba restart which goes to **/etc/rc.local**.

---

### Post by ZanusisBZG on 2010-12-01
same, 10.10 64 bit and 10.10 32 bit  and xp, server 2003, vista
[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=9242058](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=9242058)

---

