---
title: "nsd not using libwrap0 / hosts.deny ? axfr queries not denied"
date: 2011-03-17
forum: Networking &amp; Wireless
---

### Post by Mozai on 2011-03-17
I installed NSD ([http://packages.ubuntu.com/maverick/nsd](http://packages.ubuntu.com/maverick/nsd)) and in the instructions /usr/share/doc/nsd/README.gz it mentions in section 3.2:
> 3.2 AXFR access
When compiled with libwrap nsd will use daemon name ``axfr'' and
``axfr-zone'' to verify access privileges for the client trying to
initiate the transfer.
...
Example:

axfr-nlnetlabs.nl. : ns.sidn.nl : allow
axfr : 127.0.0.1 : allow
axfr : ns1.ripe.net : allow
axfr : ns1.sidn.nl : allow
axfr : ALL : deny


I can see from the package description (linked at the top of this post) that nsd was compiled with libwrap0, so I'm confident that it should be using tcpwrappers, but I'm unable to prevent people from making zone transfers.

I tried 'echo "axfr : ALL" >>/etc/hosts.deny' (proper form as per 'man 5 hosts_access' and I tried 'echo "axfr : ALL : deny' >> /etc/hosts.allow' (as per the instructions that came with NSD), but in both cases I'm still able to zone transfer from a remote machine with 'host -t axfr $zone $server'.

Am I overlooking something?  Or should I file a bug report?

---

### Post by Mozai on 2011-03-18
Didn't think I would get an answer, but it was worth a shot.

Turns out the 'libwrap0' package has "Recommends: tcpd".  Programs compiled with libwrap needs libwrap0 to launch, but the tcpwrappers feature doesn't work unless 'tcpd' is installed and running.  (I turned off auto-install of "Recommends" because too many packages were recommending GNOME and Xorg stuff when this is a headless server).

No tcpd, no answer when libwrap0 asks questions.
This becomes moot in NSD version 3.x -- access control gets built in.

Solution:  Install package 'tcpd' and start it.
Alternate Solution: Don't install nds from maverick; use nds v3 instead.
Better Alternate Solution: request ubuntu-motu to upgrad the nds package from v2.3.7 to v3.x

---

