---
title: "University network printing failure"
date: 2012-10-02
forum: Networking &amp; Wireless
---

### Post by cathalcummins on 2012-10-02
I've been struggling with this problem for quite some time.

Up until a month ago (approx), all linuix users in my dept could print to any network printer they wished. The uni doesn't officially support Linux so we just set it up via samba.

Then suddenly, none of us could print! I've tried all sorts of fixes as suggested here and elsewhere but to no avail.

The errors are of the form:

"Unable to connect to CIFS host"

in the properties of the printer and

"Connection failed: NT_STATUS_BAD_NETWORK_NAME"

from the localhost:631 window.


First I thought it was a CUPS upgrade but it happens with old CUPS as well as new CUPS.

The device urls haven't changed and don't have and spaces in their names so I don't think syntax is the issue.


Here are two printers I use:

Description:	HP LaserJet p2055dn
Location:	A2015
Driver:	HP LaserJet p2055dn pcl3, hpcups 3.12.2 (color, 2-sided printing)
Connection:	smb://castaldi1/MS02
Defaults:	job-sheets=none, none media=iso_a4_210x297mm sides=one-sided


Description:	HP Color LaserJet 3600
Location:	A2015
Driver:	HP Color LaserJet 3600 Foomatic/pxljr (color, 2-sided printing)
Connection:	smb://CASTALDI1/MS_MACSI

Neither work anymore, for anyone in the department. Nothing was changed on our part.

Has anyone any ideas or need me to run some commands?

---

### Post by lfhb on 2012-10-21
Did you manage to get your answer?  Post upgrade syndrome?  Try the non default share perhaps? [NT_STATUS_BAD_NETWORK_NAME]("http://www.microdevsys.com/WordPress/2009/07/27/networking-sharing-folders-between-windows-and-linux-using-samba/3/") 

Couple of CUPS related pages on that site might move you along to the solution as well.

Cheers,

---

