---
title: "Help with GUFW and port forwarding"
date: 2010-02-24
forum: Networking &amp; Wireless
---

### Post by whein on 2010-02-24
Ok, so I have three computers on a LAN and one of those computers has a second NIC that talks to the cable modem(?) box from Comcast.  I managed to piece together enough from the web and forums to get the main computer talking to the Comcast box to get an IP using DHCP and to have the LAN run off of static IP addresses where the dual NIC box is 192.168.0.1 and the other two are 192.168.0.2 and 192.168.0.3 respectively.  I can ping from .1 to .2 and .3, SSH, have .3 fetch apt updates from the internet, etc.  All seems happy with the world so far.  Now I try to add in GUFW to the mix.  I enable GUFW (with default of deny all) and added three rules:
ALLOW 192.168.0.255 22/tcp 192.168.0.2 22/tcp
ALLOW 192.168.0.255 2049/tcp 192.168.0.2 2049/tcp
ALLOW 192.168.0.255 5900/tcp 192.168.0.2 5900/tcp

When I enable the firewall in GUFW, I can ping and ssh to .3 from .1 but .3 cannot see the internet when I run apt-get update.  .1 can still see the internet just fine.  If I disable the firewall (uncheck the Enabled box in GUFW) then internet works again from .3

What rules do I need to add to GUFW to allow .2 and .3 to see the internet again?  The applications I am interested in for .2 and .3 are
mythfilldatabase
apt
firefox
ntpd

I'd prefer to find out what to use for GUFW and not commands for the terminal, but worst case I can work a mean text editor/terminal shell.  Thanks in advance,
-Will

---

