---
title: "Kicked out of Windows 2003 Domain?"
date: 2010-04-25
forum: Networking &amp; Wireless
---

### Post by rajesh0975 on 2010-04-25
Hi,

I recently got a new machine at my workplace with Win 7 Pro x64  installed. The machine named PC-04 is a member of the workplace domain. Since there were no Win 7 x64 drivers available for the shared printer, I decided to add ubuntu to this machine.

The machine dual boots with Ubuntu 9.10 x64 installation given a new name, PC-05. I then joined this machine to workplace domain using likewise open. The likewise installer and the manual was downloaded from the likewise website since the workplace network does not have internet access. I had to modify the line in /etc/nsswitch.conf
from
"hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4"
to
"hosts:          files dns mdns4_minimal [NOTFOUND=return] mdns4"

This machine had created active directory account on joining the domain. BTW, the domain server runs Windows 2003 x64 R2 with DNS, Active Directory and DHCP running on it. The machine worked satisfactorily on Ubuntu for 3-4 days when one morning I logged in with network account but could not browse the network. I checked network manager to find that the machine could not get an address from the DHCP. The same machine however works fine when logged into Windows.

The ubuntu log indicates timeout on DHCPDISCOVER. I have tried changing the eth0 hardware address in Ubuntu to register with DHCP. Even re-installed Ubuntu once.

I am clueless as to why it has happened? Need help in resolving the issue. 

Regards

Rajesh

---

