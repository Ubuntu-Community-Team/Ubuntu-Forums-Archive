---
title: "dhcp errors"
date: 2009-03-07
forum: Networking &amp; Wireless
---

### Post by petee1979 on 2009-03-07
i am trying to seup ltsp on ubuntu 7.10 but keep getting errors:
heres what i've done:
sudo /etc/network/interfaces
                   contents of that file      AUTO ETH0
                                              iface eth0 inet dhcp

                                              auto eth1
                                              iface eth1 inet dhcp
sudo /etc/init.d/networking restart
sudo apt-get update
sudo apt-get install dhcp3-server
sudo apt-get install ltsp-server-standalone openssh-server
sudo ltsp-build-client
sudo rm /var/tmp/dhcp3-server.swp
sudo vim /etc/defaults/dhcp3-server
                   contents of that file     INTERFACES="eth0 eth1"
sudo /etc/init.d/dhcp3-server start              FAIL
sudo tail -f /var/log/syslog   LOG CONTAINS

no subnet declaraion for eth0 (10.0.2.15).
ignoring requests on eth0. if this is not
what you want , please write a subnet declaration
in your dhcpd.conf file for the network segment
to which interface eth0 is attached.


PLEASE HELP

---

### Post by linuxisevolution on 2009-03-07
> **petee1979 said:**
> i am trying to seup ltsp on ubuntu 7.10 but keep getting errors:
heres what i've done:
sudo /etc/network/interfaces
                   contents of that file      AUTO ETH0
                                              iface eth0 inet dhcp

                                              auto eth1
                                              iface eth1 inet dhcp
sudo /etc/init.d/networking restart
sudo apt-get update
sudo apt-get install dhcp3-server
sudo apt-get install ltsp-server-standalone openssh-server
sudo ltsp-build-client
sudo rm /var/tmp/dhcp3-server.swp
sudo vim /etc/defaults/dhcp3-server
                   contents of that file     INTERFACES="eth0 eth1"
sudo /etc/init.d/dhcp3-server start              FAIL
sudo tail -f /var/log/syslog   LOG CONTAINS

no subnet declaraion for eth0 (10.0.2.15).
ignoring requests on eth0. if this is not
what you want , please write a subnet declaration
in your dhcpd.conf file for the network segment
to which interface eth0 is attached.


PLEASE HELP

Try changing eth1 in the file to eth0.

---

### Post by petee1979 on 2009-03-07
i just opened the dhcpd.conf file and there is no listing of any eth0 or eth1, what should the file contain?

---

