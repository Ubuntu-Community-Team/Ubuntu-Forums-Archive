---
title: "Network Manager Bug????"
date: 2009-02-02
forum: Networking &amp; Wireless
---

### Post by tpurch on 2009-02-02
It appears that I am experiencing problems with Network Manager overwriting resolv.conf.  I currently use VPNC to connect to work and the resolv.conf file is updated with resolvconf (DNS_UPDATE) but I am now getting a problem where the resolv.conf (symbolic link file to /etc/resolvconf/run/resolv.conf) is being overwritten by network manager on boot up.  The symbolic link disappears and is replaced by a new resolv.conf this means that when I logon to my vpn the resolvconf is unable to update DNS because resolv.conf should be a symbolic link.   I have to delete the resolv.conf file and re-create the symbolic link to /etc/resolvconf/run/resolv.conf to get it to work.  After reboot the symbolic link has disappeared again......  I have checked network-manager its set to obtain IP, DNS and default routes dynamically. 

Does anyone know how to fix this issue?

---

