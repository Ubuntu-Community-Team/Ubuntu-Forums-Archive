---
title: "Unable to Install Wireless Drivers"
date: 2010-10-12
forum: Networking &amp; Wireless
---

### Post by Sef on 2010-10-12
When I download the drivers for my Broadcom card (BCM-4312), I get this error message:
> 
SystemError: installArchives() failedIs there any way to fix it, or should I post to launchpad about a bug?

I have 10.10.

Update: When I install from the Ubuntu Software Center, it completes successfully, but I get this error message:


installArchives() failed: Selecting previously deselected package glines.
> (Reading database ... 
<snip>
(Reading database ... 100%
(Reading database ... 131362 files and directories currently installed.)
Unpacking glines (from .../glines_1%3a2.32.0-0ubuntu1_amd64.deb) ...
Processing triggers for gconf2 ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache...
Processing triggers for hicolor-icon-theme ...
Processing triggers for python-support ...
Setting up firmware-b43-installer (4.150.10.5-4) ...
Not supported low-power chip with PCI id 14e4:4315!
Aborting.
dpkg: error processing firmware-b43-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
Setting up glines (1:2.32.0-0ubuntu1) ...
Setting up firmware-b43-installer (4.150.10.5-4) ...
Not supported low-power chip with PCI id 14e4:4315!
Aborting.
dpkg: error processing firmware-b43-installer (--configure):
 subprocess installed post-installation script returned error exit status 1

---

### Post by Sef on 2010-10-17
bump

---

### Post by garvinrick4 on 2010-10-17
Give this ago it seems to be working for that particular broadcom card.
Seems lots of Dell folks having proprietary problems with drivers and broadcom.
Seems every new version we get of Ubuntu new users with Dell and its proprietary drivers likes
to smack people on the knuckles who try to stray to far from Dell and Windows. Just an observation
from roaming these Forums the first weeks after new version's are announced. I see they do work though.

[http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)

---

### Post by Sef on 2010-10-22
> [http://www.ubuntumini.com/2009/11/br...in-karmic.html](http://www.ubuntumini.com/2009/11/br...in-karmic.html)

Did not work. Still can't get the firmware to install. It is a known bug.

Update: I have a solution thanks to Kontza [here]("https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/651010").

What to do is this:

System > Administration > Synaptic Package Manager > Search: firmware-b43-lpphy-installer > Click Mark > Click install > close

---

