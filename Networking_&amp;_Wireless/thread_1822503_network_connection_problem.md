---
title: "network connection problem"
date: 2011-08-10
forum: Networking &amp; Wireless
---

### Post by mohamed1042002 on 2011-08-10
i need to change my net speed from 100Mb/s  to 10 Mb/s how can i do it ? thanks for answering

---

### Post by chili555 on 2011-08-10
In a terminal, do:```
sudo ethtool -s eth0 speed 10
```If it works as expected, add the command to rc.local:```
sudo gedit /etc/rc.local
```Add one line above exit 0:```
ethtool -s eth0 speed 10
```Proofread, save and close gedit.

---

### Post by mohamed1042002 on 2011-08-10
[B]i do that command and i got 

code 
[/B]sudo: ethtool: command not found

---

### Post by chili555 on 2011-08-10
Then let's install it:```
sudo apt-get install ethtool
```

---

### Post by mohamed1042002 on 2011-08-10
[B][COLOR=Black]i do wat u told me here're the result 
mohamed@ubuntu:~$ sudo apt-get install ethtool[/COLOR][/B]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ethtool is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

---

### Post by chili555 on 2011-08-10
Do you instead have *mii-tool*?```
sudo mii-tool -F 10baseT-FD eth0 
```The entry in rc.local will be as above without sudo.

---

### Post by mohamed1042002 on 2011-08-11
***thanks alot man.it solved ***

---

### Post by chili555 on 2011-08-11
Glad to hear it's working! Would you please use thread tools at the top and Mark Solved?

---

### Post by mohamed1042002 on 2011-08-12
hello ....  i got little problem 
when i restart my notebook i got no connection again   ....and to get connected i must retype the last code again ......
and i type 
mii-tool -F 10baseT-FD eth0
in rc.local as u said above no change happen 
can any one help me to avoid it ?

---

### Post by mohamed1042002 on 2011-08-12
[B][SIZE=3]> **mohamed1042002 said:**
> hello ....  i got little problem 
when i restart my notebook i got no connection again   ....and to get connected i must retype the last code again ......
and i type 
mii-tool -F 10baseT-FD eth0
in rc.local as u said above no change happen 
can any one help me to avoid it ?
  

any kind of help here plsssssssssssssssssss[/SIZE][/B]

---

### Post by chili555 on 2011-08-13
Please change your rc.local just a bit:```
sudo gedit /etc/rc.local
```Change it so it reads like this:```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

ifconfig eth0 down
mii-tool -F 10baseT-FD eth0
ifconfig eth0 up

exit 0

```Proofread carefully, save and close gedit. Reboot and let us have your report. If it doesn't work, we'll look into your ethernet driver. Find out what it is with:```
sudo lshw -C network
```Here is an example from my computer:>  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 00
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes [COLOR="Red"]driver=e1000e[/COLOR] driverversion=1.2.20-k2 firmware=0.5-1We don't need to see all of it; just tell us what the driver is.

*lshw* takes a few moments, please be patient.

---

### Post by mohamed1042002 on 2011-08-13
i do what u said and when i type in rc.local and restart i lost connection and it become disable i remove wat i wrote ans restart i enter the Code :
sudo lshw -C network
here wat i got 
Quote:
*-network
        description: Ethernet interface
        product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
        vendor: Realtek Semiconductor Co., Ltd.
        physical id: 0
        bus info: pci@0000:06:00.0
        logical name: eth0
        version: 01
        serial: 00:1e:68:1a:d6:7a
        size: 10Mbit/s
        capacity: 100Mbit/s
        width: 64 bits
        clock: 33MHz
        capabilities: pm vpd msi pciexpress bus_master cap_list rom  ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
        configuration: autonegotiation=off broadcast=yes driver=r8169  driverversion=2.3LK-NAPI duplex=full ip=192.168.1.103 latency=0 link=yes  multicast=yes port=MII speed=10Mbit/s
        resources: irq:45 ioport:c000(size=256) memory:f8000000-f8000fff memory:80000000-8001ffff

---

### Post by mohamed1042002 on 2011-08-14
any kinda of help here guys pls .....................
i become mad from that :(

---

### Post by VipX1 on 2011-08-14
> **mohamed1042002 said:**
> i do what u said and when i type in rc.local and restart i lost connection and it become disable i remove wat i wrote ans restart i enter the Code :
sudo lshw -C network
here wat i got 
Quote:
*-network
        description: Ethernet interface
        product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
        vendor: Realtek Semiconductor Co., Ltd.
        physical id: 0
        bus info: pci@0000:06:00.0
        logical name: eth0
        version: 01
        serial: 00:1e:68:1a:d6:7a
        size: 10Mbit/s
        capacity: 100Mbit/s
        width: 64 bits
        clock: 33MHz
        capabilities: pm vpd msi pciexpress bus_master cap_list rom  ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
        configuration: autonegotiation=off broadcast=yes driver=r8169  driverversion=2.3LK-NAPI duplex=full ip=192.168.1.103 latency=0 link=yes  multicast=yes port=MII speed=10Mbit/s
        resources: irq:45 ioport:c000(size=256) memory:f8000000-f8000fff memory:80000000-8001ffff

According to the above output you are nw running at "speed=10Mbit/s" after reboot. Therefore the rc.local changes are working.
Why do you want to run at 10Mbit/s. That is very slow for a modern LAN connection.

Did your connection work before the change to 10Mbit/s? Perhaps the original problem still applies at the lower speed.

---

### Post by mohamed1042002 on 2011-08-14
when i running at 100Mb/s i lost connection i donno why....... and i got this info. above after i wrote the Code:
sudo mii-tool -F 10baseT-FD eth0 
 to get connection but always i must wrote this code to get connected after each restart 
i become desperate from that problem

---

### Post by mohamed1042002 on 2011-08-15
im still w8ing for help  plssssss............................. :(

---

