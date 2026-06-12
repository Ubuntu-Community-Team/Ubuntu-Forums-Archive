---
title: "Configuring Kismet"
date: 2009-03-11
forum: Networking &amp; Wireless
---

### Post by DevinMcElheran on 2009-03-11
I have been trying to get kismet going for a while, but I have had no luck, I think it's just my configuration file, but I could be wrong. This is the output when I try to run it:

devin@Ubuntutop:~/kismet-2007-01-R1b$ sudo kismt
sudo: unable to resolve host Ubuntutop
sudo: kismt: command not found
devin@Ubuntutop:~/kismet-2007-01-R1b$ sudo kismet
sudo: unable to resolve host Ubuntutop
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (addme): Opening none source interface none...
FATAL: Please configure at least one packet source.  Kismet will not function if no packet sources are defined in kismet.conf or on the command line.  Please read the README for more information about configuring Kismet.
Kismet exiting.
Done.


I have a Broadcom 4311 Card, and I'm using the driver that came preinstalled in Ubuntu, I'm not sure, but I think it's b43. Any help would be appreciated a lot.

---

### Post by chili555 on 2009-03-11
"Search" is your friend. Please see here: [http://ubuntuforums.org/showthread.php?t=1067390&highlight=kismet.conf](http://ubuntuforums.org/showthread.php?t=1067390&highlight=kismet.conf)

---

