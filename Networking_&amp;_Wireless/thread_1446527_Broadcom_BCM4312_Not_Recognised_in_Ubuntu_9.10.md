---
title: "Broadcom BCM4312 Not Recognised in Ubuntu 9.10"
date: 2010-04-04
forum: Networking &amp; Wireless
---

### Post by cks93 on 2010-04-04
Hi there

 I have only recently installed dualboot Vista/Ubuntu 9.10. I am unable to get the wireless working in Ubuntu. I have followed nearly all the forum threads on this issue but nothing to seem to have worked. The wireless card in my Dell Inspiron 1545 is BCM 4312  802.11b/g 14e4:4315.

I have followed the instruction in the Readme.txt for 32 bit driver "hybrid-portsrc.tar.gz" as downloaded from Broadcom site.



In a thread on similar issue pytheas22 and Ayuthia advised to execute a few commnads and place the results which i am doing in this mail.  Any help from them and other is greatly appreciated. I executed all these commands while connected to Internet on wire,

k@CK-Laptop-Ubuntu:~$ sudo -s
[sudo] password for ck:
root@CK-Laptop-Ubuntu:~# echo 'blacklist b43' >> /etc/modprobe.d/blacklist
root@CK-Laptop-Ubuntu:~# echo 'blacklist b43legacy' >> /etc/modprobe.d/blacklist
root@CK-Laptop-Ubuntu:~# sudo su
root@CK-Laptop-Ubuntu:/home/ck# echo 'blacklist b43legacy' >> /etc/modprobe.d/blacklist
root@CK-Laptop-Ubuntu:/home/ck# echo 'blacklist ssb' >> /etc/modprobe.d/blacklist
root@CK-Laptop-Ubuntu:/home/ck# echo 's/blacklist bcm43xx/#blacklist bcm43xx' >> /etc/modprobe.d/blacklist
root@CK-Laptop-Ubuntu:/home/ck# apt-get install bcm43xx-fwcutter
Reading package lists... Done
Building dependency tree      
Reading state information... Done
E: Couldn't find package bcm43xx-fwcutter
root@CK-Laptop-Ubuntu:/home/ck#
root@CK-Laptop-Ubuntu:/home/ck#
root@CK-Laptop-Ubuntu:/home/ck#
root@CK-Laptop-Ubuntu:/home/ck#
root@CK-Laptop-Ubuntu:/home/ck#
root@CK-Laptop-Ubuntu:/home/ck# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

root@CK-Laptop-Ubuntu:/home/ck# lshw -C Network
  *-network UNCLAIMED    
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:25:64:45:0c:6d
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 duplex=full firmware=N/A ip=192.168.2.6 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:29 memory:f68fc000-f68fffff ioport:de00(size=256)
root@CK-Laptop-Ubuntu:/home/ck# cat /etc/modprobe.d/blacklist
blacklist b43
blacklist b43legacy
blacklist b43legacy
blacklist ssb
s/blacklist bcm43xx/#blacklist bcm43xx
root@CK-Laptop-Ubuntu:/home/ck# dmesg | grep -e bcm -e ethl
root@CK-Laptop-Ubuntu:/home/ck#
root@CK-Laptop-Ubuntu:/home/ck# lspci -nn | grep -i broadcom
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
root@CK-Laptop-Ubuntu:/home/ck# lsmod | grep bcm43xx
root@CK-Laptop-Ubuntu:/home/ck#
root@CK-Laptop-Ubuntu:/home/ck#



root@CK-Laptop-Ubuntu:/home/ck#
root@CK-Laptop-Ubuntu:/home/ck# uname -a
Linux CK-Laptop-Ubuntu 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux
root@CK-Laptop-Ubuntu:/home/ck#
root@CK-Laptop-Ubuntu:/home/ck#
root@CK-Laptop-Ubuntu:/home/ck#
root@CK-Laptop-Ubuntu:/home/ck# lsmod|grep -i -e b43 -e wl -e bcm43xx
root@CK-Laptop-Ubuntu:/home/ck#
root@CK-Laptop-Ubuntu:/home/ck# 



Much appreciate help from all experts. Thanks.

---

### Post by bkratz on 2010-04-04
> **cks93 said:**
> 

BCM 4312  802.11b/g [COLOR="Red"]14e4:4315[/COLOR].

I have followed the instruction in the Readme.txt for 32 bit driver "hybrid-portsrc.tar.gz" as downloaded from Broadcom site.

Do you have links for what you have tried?

root@CK-Laptop-Ubuntu:/home/ck# apt-get install [COLOR="red"]bcm43xx-fwcutter[/COLOR]
This is used when trying to install b43 drivers.

From this page:
[http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices)

"14e4:4315
supported 2.6.32 and later
BCM4312
b/g
LP
b43
"

You will see that your card is only supported by b43 in kernel 2.6.32 or later.  Yours isn't see below.

root@CK-Laptop-Ubuntu:/home/ck# uname -a
[COLOR="red"]Linux CK-Laptop-Ubuntu 2.6.31-14-generic[/COLOR] #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux
root@CK-Laptop-Ubuntu:/home/ck#

Therefore you need to use the STA driver.
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
read the readme files first


As a quick try you could go here and read this also
[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by cks93 on 2010-04-07
Thanks a lot, will try that.

---

