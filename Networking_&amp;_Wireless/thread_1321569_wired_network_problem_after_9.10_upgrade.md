---
title: "wired network problem after 9.10 upgrade"
date: 2009-11-10
forum: Networking &amp; Wireless
---

### Post by riknos on 2009-11-10
Took the leap of faith and upgraded my 9.04 system to 9.10 via Synaptic Package Manager Upgrade button. All appeared to go well but there was no network link when system booted. Couldn't ping local network, so network shares unavailable and couldn't get to any web site with Firefox. There was no Network Manager icon on panel. Think initial problem was with DNS and I have also read that there could be a problem with ipv6 settings. Changed latter in Firefox but don't know if there is still a problem elsewhere. 

Googled around, checked this forum and manually updated various files associated with network, changed settings back and forth in NM - see outputs below - and am now able to get network up each session with sudo ifup eth1. But this is not really ideal and would like to get NM working correctly. Have reinstalled NM a couple of times and tried various settings - all to no avail. Has anyone any ideas on what I can try next?

======
/etc/NetworkManager/nm-system-settings.conf

[main]
plugins=ifupdown,keyfile

no-auto-default=00:16:17:42:6e:2b,

[ifupdown]

========
/etc/network/interfaces

auto lo
iface lo inet loopback
iface eth1 inet static
address 192.168.1.201
netmask 255.255.255.0
gateway 192.168.1.1
network	192.168.1.0
broadcast 192.168.1.255

managed=false

=========
/etc/resolv.conf

nameserver 192.168.1.1
nameserver 2xx.xx.xx.xxx
nameserver 2xx.xx.xx.xxx
search xxxxx.fr
+++++++++++++++++++++++++++++++++++++++++++++++

---

