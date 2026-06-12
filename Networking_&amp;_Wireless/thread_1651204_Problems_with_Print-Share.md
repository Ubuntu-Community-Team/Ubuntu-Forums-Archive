---
title: "Problems with Print-Share"
date: 2010-12-22
forum: Networking &amp; Wireless
---

### Post by belize1334 on 2010-12-22
Greetings all,

I have an old(er) GX520 desktop which I've set up with 10.04 and am attempting to use as a print-server. I've got to the point where the printer is visible over the network and machines can proceed to install it but once they get the the test-page there's nothing. The remote computer finishes sending the print-job but nothing appears in the job queue and nothing prints. I've even tried finding the printer over the network from the local machine and installing it that way. Same thing... visible on the network and verified as accessible but then nothing prints. I get an error message NT_STATUS_LOGON_FAILURE

I'm hoping that this is as simple as not having the appropriate user(s) and privileges. I've tried altering the cups/printers.conf file and all sorts of other purported fixes to no avail. I'm finally back to the original configuration and a modified smb.conf listed below...

> 
[global]
workgroup = physics
netbios name = dpg-linux-box
passdb backend = tdbsam
name resolve order = bcast host lmhosts wins
server string =
printing = cups
printcap name = cups
printcap cache time = 750
cups options = raw
use client driver = yes
map to guest = Bad User
usershare allow guests = Yes
usershare max shares = 100
usershare owner only = False

[printers]
comment = All Printers
path = /var/spool/samba
browsable = no
Set Public = yes
guest ok = yes
writable = no
printable = yes
I know it's busy around the holidays but any help would be appreciated.

---

