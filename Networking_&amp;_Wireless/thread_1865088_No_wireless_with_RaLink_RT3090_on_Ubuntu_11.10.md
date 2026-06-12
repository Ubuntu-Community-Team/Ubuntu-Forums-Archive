---
title: "No wireless with RaLink RT3090 on Ubuntu 11.10"
date: 2011-10-19
forum: Networking &amp; Wireless
---

### Post by Gurumeditation on 2011-10-19
I am running Ubuntu 11.10 (64bit) on an MSI U160 and the wired network works fine, but I cannot make the wireless working.
davide@ponos:~$ uname -a
Linux ponos 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

The wireless card is a RaLink RT3090 and I got its driver from ppa:markus-tisoft/rt3090.
davide@ponos:~$ lspci | grep -i wireless
03:00.0 Network controller: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe

The firmware seems to be installed correctly, with a rt3090.bin link pointing to rt2860.bin:

davide@ponos:/lib/firmware$ ls -l | grep rt[0-9]
-rw-r--r--  1 root root   34304 2011-08-23 23:22 intelliport2.bin
-rw-r--r--  1 root root    8192 2011-08-23 23:22 rt2561.bin
-rw-r--r--  1 root root    8192 2011-08-23 23:22 rt2561s.bin
-rw-r--r--  1 root root    8192 2011-08-23 23:22 rt2661.bin
-rwxrwxrwx  1 root root    8192 2011-08-23 23:23 rt2860.bin
-rw-r--r--  1 root root    8192 2011-08-23 23:23 rt2870.bin
lrwxrwxrwx  1 root root      10 2011-10-19 08:35 rt3070.bin -> rt2870.bin
-rw-r--r--  1 root root    4096 2011-08-23 23:23 rt3071.bin
lrwxrwxrwx  1 root root      10 2011-10-19 08:35 rt3090.bin -> rt2860.bin
-rw-r--r--  1 root root    2048 2011-08-23 23:22 rt73.bin

davide@ponos:~$ sudo lshw -c net
[sudo] password for davide: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 40:61:86:ae:bf:25
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=N/A ip=192.168.1.2 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:40 ioport:e000(size=256) memory:e2110000-e2110fff memory:e2100000-e210ffff memory:fe000000-fe01ffff
  *-network DISABLED
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: ra0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN driverversion=2.3.1.3 latency=0 multicast=yes wireless=Ralink STA
       resources: irq:17 memory:fd600000-fd60ffff


davide@ponos:~$ lsmod | grep rt3090
rt3090sta             885958  0 

davide@ponos:~$ modinfo rt3090sta
filename:       /lib/modules/3.0.0-12-generic/updates/dkms/rt3090sta.ko
version:        2.3.1.3
srcversion:     FFE8374362ED5B734E14328
alias:          pci:v00001814d00003092sv*sd*bc*sc*i*
alias:          pci:v00001814d00003091sv*sd*bc*sc*i*
alias:          pci:v00001814d00003090sv*sd*bc*sc*i*
depends:        
vermagic:       3.0.0-12-generic SMP mod_unload modversions 
parm:           mac:rt28xx: wireless mac addr (charp)


I tried to disable the wired network and bring up the wireless one, but no luck.
If someone can shed some light on the matter it would be helpful.

---

### Post by Mestarine on 2011-10-19
Hello,

i've got exactly the same issue with my device (a U160 by MSI, with rt3090 wireless system). I setup, as you did, the rt3090 driver provide by  ppa:markus-tisoft/rt3090.
But, there is noway i could find to make it work well. I still got this message from network-manager : your device is not handle.

We need some helpppp. Thanks :-)

---

### Post by kevh on 2011-10-22
I had exactly the same problem on a Sony Vaio with Ralink rt3090 wireless connection lost on upgrade to 11.10. The solution that I found was to edit /etc/modprobe.d/blacklist.conf, remove the line "blacklist rt2800pci" (without quotes), save the file and then reboot.
Have fun!

---

### Post by Gurumeditation on 2011-10-30
rt2800pci is not blacklisted for me.

---

