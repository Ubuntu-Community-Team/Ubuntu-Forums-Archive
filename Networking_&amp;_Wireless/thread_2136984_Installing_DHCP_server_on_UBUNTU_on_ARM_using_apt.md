---
title: "Installing DHCP server on UBUNTU on ARM using apt"
date: 2013-04-19
forum: Networking &amp; Wireless
---

### Post by deeptitv on 2013-04-19
Hi,

I'm tring to configure wi-fi on an ARM board and have done this by installing the hostapd package. Now to enable DHCP for this interface, I am trying to install a DHCP server on an ARM platform - ( [SIZE=2]PANDA Board 2 : ES Rev B1 Model number : 750-2170-002 RevB  ). 
The OS version of Ubuntu installed is 11.10. 

When I try to install the "isc-dhcp-server" using apt-get, I get the following error : 

"
Err [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) oneiric-updates/main isc-dhcp-client armel 4.1.1-P1-17ubuntu10.1
  404  Not Found
Err [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) oneiric-updates/main isc-dhcp-common armel 4.1.1-P1-17ubuntu10.1
  404  Not Found
Err [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) oneiric-updates/main isc-dhcp-server armel 4.1.1-P1-17ubuntu10.1
  404  Not Found
Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/pool/main/i/isc-dhcp/isc-dhcp-client_4.1.1-P1-17ubuntu10.1_armel.deb](http://ports.ubuntu.com/ubuntu-ports/pool/main/i/isc-dhcp/isc-dhcp-client_4.1.1-P1-17ubuntu10.1_armel.deb)  404  Not Found
Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/pool/main/i/isc-dhcp/isc-dhcp-common_4.1.1-P1-17ubuntu10.1_armel.deb](http://ports.ubuntu.com/ubuntu-ports/pool/main/i/isc-dhcp/isc-dhcp-common_4.1.1-P1-17ubuntu10.1_armel.deb)  404  Not Found
Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/pool/main/i/isc-dhcp/isc-dhcp-server_4.1.1-P1-17ubuntu10.1_armel.deb](http://ports.ubuntu.com/ubuntu-ports/pool/main/i/isc-dhcp/isc-dhcp-server_4.1.1-P1-17ubuntu10.1_armel.deb)  404  Not Found
"

I found the exact same error when I tried with dhcp3-server package as well. 
Does this require a change in the UBUNTU repository or am I doing something wrong? 


The exact commands I gave are given below . 


=======================================================================
root@ue_2:~# apt-get install isc-dhcp-server
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  isc-dhcp-client isc-dhcp-common
Suggested packages:
  resolvconf isc-dhcp-server-ldap
The following NEW packages will be installed:
  isc-dhcp-server
The following packages will be upgraded:
  isc-dhcp-client isc-dhcp-common
2 upgraded, 1 newly installed, 0 to remove and 312 not upgraded.
Need to get 929 kB of archives.
After this operation, 758 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  isc-dhcp-client isc-dhcp-common isc-dhcp-server
Install these packages without verification [y/N]? y
Err [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) oneiric-updates/main isc-dhcp-client armel 4.1.1-P1-17ubuntu10.1
  404  Not Found
Err [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) oneiric-updates/main isc-dhcp-common armel 4.1.1-P1-17ubuntu10.1
  404  Not Found
Err [http://ports.ubuntu.com/ubuntu-ports/](http://ports.ubuntu.com/ubuntu-ports/) oneiric-updates/main isc-dhcp-server armel 4.1.1-P1-17ubuntu10.1
  404  Not Found
Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/pool/main/i/isc-dhcp/isc-dhcp-client_4.1.1-P1-17ubuntu10.1_armel.deb](http://ports.ubuntu.com/ubuntu-ports/pool/main/i/isc-dhcp/isc-dhcp-client_4.1.1-P1-17ubuntu10.1_armel.deb)  404  Not Found
Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/pool/main/i/isc-dhcp/isc-dhcp-common_4.1.1-P1-17ubuntu10.1_armel.deb](http://ports.ubuntu.com/ubuntu-ports/pool/main/i/isc-dhcp/isc-dhcp-common_4.1.1-P1-17ubuntu10.1_armel.deb)  404  Not Found
Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/pool/main/i/isc-dhcp/isc-dhcp-server_4.1.1-P1-17ubuntu10.1_armel.deb](http://ports.ubuntu.com/ubuntu-ports/pool/main/i/isc-dhcp/isc-dhcp-server_4.1.1-P1-17ubuntu10.1_armel.deb)  404  Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
root@ue_2:~#
[/SIZE][SIZE=2]=======================================================================[/SIZE]
[SIZE=2]





[/SIZE]

---

### Post by SeijiSensei on 2013-04-19
A little Google searching brought me to this page: [https://launchpad.net/ubuntu/oneiric/armel/isc-dhcp-server/4.1.1-P1-17ubuntu10.5](https://launchpad.net/ubuntu/oneiric/armel/isc-dhcp-server/4.1.1-P1-17ubuntu10.5)

---

### Post by jdthood on 2013-04-19
In [http://ports.ubuntu.com/ubuntu-ports/pool/main/i/isc-dhcp/](http://ports.ubuntu.com/ubuntu-ports/pool/main/i/isc-dhcp/) I find isc-dhcp-server_4.1.1-P1-17ubuntu10.5_armel.deb but not version 4.1.1-P1-17ubuntu10.1. 

Perhaps you need to run "apt-get update"?

---

### Post by Slim Odds on 2013-04-19
FYI, 11.10 is no longer supported

---

