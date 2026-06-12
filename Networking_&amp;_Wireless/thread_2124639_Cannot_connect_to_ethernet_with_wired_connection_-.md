---
title: "Cannot connect to ethernet with wired connection - 12.10"
date: 2013-03-11
forum: Networking &amp; Wireless
---

### Post by tonyoz on 2013-03-11
I am new to Ubuntu (installed Ubuntu 12.10 desktop on my Mac Mini  today from Ubuntu iso – mac mini had blank SSD on it i.e. no OS X at  all).


 First drama is that Ubuntu installer seems to be setup for DHCP whereas my LAN is all static IP based.


 Anyway, Ubuntu installed okay except that it seems to have gone into  loopback mode and cannot find the Ethernet adapter on the Mac Mini.


 Doing an 'ifconfig -a' confirms the loopback.


 Doing an lspci reveals the following:
 01:00.0 Ethernet controller: Broadcom Corporation Netxtreme BCM57766 Gigabit Ethernet PCIe (rev 05)


 I tried the following:


 Setting /etc/hosts file to include:
 127.0.0.1 localhost
192.168.0.2 merlot


 I wanted to set /etc/network/interfaces file to have:
 auto eth0
iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1

 Except that eth0 doesn't seem to exist as far as Ubuntu is concerned.
192.168.0.1 is my modem/router which connects directly to the Internet.


 I wanted to edit /etc/resolv.conf so that I could specify some DNS name servers  (3 in total) that should be used except  that the resolv.conf file  contained text warning me that the file would be overwritten so don't  bother doing anything manually in that file.


 Checking 'System Settings > Network' I cannot see wired Ethernet  at all. There is, for some reason, a 'Network Proxy' defined. A messagebox appears saying:

 "The system network services are not compatible with this version."


 I have not been able to establish a network connection at all.


 1. What can I try to fix this?

 2. Do I need a driver from somewhere and can I install said driver without having to recompile the kernel?
 3. Is there a GUI way of setting network parameters or is editing the  hosts, resolv.conf (???), and interfaces file the only way?
 4. How can I find the Ethernet Mac address from terminal (I couldn't get it by doing 'ifconfig -a')?

---

### Post by sparklyballs on 2013-03-11
on the stock install of 12.10 on my mac mini late 2012 with the broadcom card in it i got working using info from here. 

hopefully it works for you, 

[http://bharath.lohray.com/weblog/installing-mint-on-a-late-2012-macmini/](http://bharath.lohray.com/weblog/installing-mint-on-a-late-2012-macmini/)

i've pushed my kernel up to 3.8 though and it doesn't work anymore for me :(

---

### Post by tonyoz on 2013-03-11
A bit more information for you (I don't know what it means though):

lspci -knn | grep -i eth -A 2

01:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM57766 Gigabit Ethernet PCIe [14e4:1686] (rev 01)
    Subsystem: Broadcom Corporation NetXtreme BCM57766 Gigabit Ethernet PCIe [14e4:1686]
01:00.1 SD Host controller [0805]: Broadcom Corporation NetXtreme BCM57765 Memory Card Reader [14e4:16bc] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:0000]


lspci -nn | grep 0200

01:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM57766 Gigabit Ethernet PCIe [14e4:1686] (rev 01)

---

### Post by steeldriver on 2013-03-11
If you have installed the **desktop** version, then networking is done by default through network-manager - controlled through the nm-applet on the GUI where you can set static IP  and DNS servers for your wired connection via Edit connections... -> Wired -> IPv4 Settings 

The /etc/network/interfaces file relates to the older / server 'networking' service, and you really shouldn't be messing with it - and certainly shouldn't be manually editing /etc/resolv.conf

By default, any interfaces you *do* define in /etc/network/interfaces will get ignored by the desktop network-manager service

---

