---
title: "Upgraded ubuntu and now lack network manager"
date: 2009-11-20
forum: Networking &amp; Wireless
---

### Post by derkrampus on 2009-11-20
I had been using wicd, but when I upgraded ubuntu to the latest version, I now have neither wicd or network manager and can't connect to the internet.  I want to go back to network manager - I couldn't get wicd to work with my wrt54g.  Please help me install network manager without a network connection!!!  I'm a linux noob

I've tried a few things but to no avail.  Can someone help me from the start?  How do I download network manager w/o a network connection and install it?

Thanks!!!

---

### Post by Iowan on 2009-11-20
Did you upgrade via CD - or Update Manager?

---

### Post by derkrampus on 2009-11-20
I upgraded via package manager.

I just tried to download and install some files but no luck.  Are these dependencies that I need to download, and if so where do I download from?

derkrampus@ubuntu://home/derkrampus/Desktop$ sudo dpkg -i network-manager*.deb
dpkg: considering removing network-manager-pptp in favour of network-manager ...
network-manager-pptp is not properly installed - ignoring any dependencies on it.
dpkg: yes, will remove network-manager-pptp in favour of network-manager.
(Reading database ... 157333 files and directories currently installed.)
Preparing to replace network-manager 0.7~~svn20081018t105859-0ubuntu1.8.10.2 (using network-manager_0.7~~svn20081018t105859-0ubuntu1.8.10.2_i386.deb) ...
Unpacking replacement network-manager ...
Unpacking network-manager-pptp (from network-manager-pptp_0.6.5+svnhead2574-0ubuntu1_i386.deb) ...
Replaced by files in installed package network-manager ...
dpkg: dependency problems prevent configuration of network-manager:
 network-manager depends on libnm-glib0 (>= 0.7~~svn20080908); however:
  Package libnm-glib0 is not installed.
 network-manager depends on libnm-util0 (>= 0.7~~svn20080908); however:
  Package libnm-util0 is not installed.
dpkg: error processing network-manager (--install):
 dependency problems - leaving unconfigured
dpkg: error processing network-manager-pptp (--install):
 package network-manager-pptp is not ready for configuration
 cannot configure (current status `config-files')
Processing triggers for sreadahead ...
Processing triggers for man-db ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Errors were encountered while processing:
 network-manager
 network-manager-pptp
derkrampus@ubuntu://home/derkrampus/Desktop$

---

