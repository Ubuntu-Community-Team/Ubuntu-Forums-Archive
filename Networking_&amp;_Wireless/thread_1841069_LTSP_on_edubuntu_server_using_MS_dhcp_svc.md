---
title: "LTSP on edubuntu server using MS dhcp svc"
date: 2011-09-08
forum: Networking &amp; Wireless
---

### Post by coreyk67 on 2011-09-08
Hello,

I am new to Linux and have been experimenting with edubuntu and LTSP in my school network environment.

I installed the latest release of edubuntu with LTSP preinstalled, but would like to use my existing DHCP svr instead of the ltsp box's DHCP svc.

I uninstalled the DHCP service with ...
sudo apt-get remove dhcp3-server

but my network adapter eth0 is not grabbing an IP from my existing DHCP svr. 
Im not really sure where to go to configure the network interface. 

What additional steps will i need to take tgo get the LTSP svr to work with a single net card using another dhcp server in another vlan?

---

