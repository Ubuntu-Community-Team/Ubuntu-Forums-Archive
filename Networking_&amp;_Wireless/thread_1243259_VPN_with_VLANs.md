---
title: "VPN with VLANs"
date: 2009-08-18
forum: Networking &amp; Wireless
---

### Post by tata_tulen on 2009-08-18
Hi all,

First of all, I've to say I'm linux newbie (win-positive with few days old dualboot :-)

I'm running Ubuntu 9.04 (up-to-date) and I've problem with PPTP VPN with using VLAN virtual ifaces. I've set up the VLAN ifaces using this link: [http://ubuntuforums.org/showthread.php?t=703387](http://ubuntuforums.org/showthread.php?t=703387).

However, the following procedure (that worked in virtual machine w/o problems) does not work now:

```

1) install ubuntu (optionally set IP when there's no DHCP server on the network)
2) application bar -> system -> login window -> security tab -> allow local system administrator login
3) sudo passwd
4) logoff & logon as root
5) update manager
6) apt-get install network-manager-pptp network-manager-vpnc --fix-missing
7) killall NetworkManager
8) NetworkManager *
9) app. bar -> network icon rightclick -> configure -> VPN -> add
10) Connect to VPN (Main panel -> Networking -> VPN Connections)


```The physical iface (eth1 - i've two) seems to be disconnected and thereby the 10th step of the procedure above does not apply (the vpn connection is greyed).

Thanks for any help.

-tt-

---

