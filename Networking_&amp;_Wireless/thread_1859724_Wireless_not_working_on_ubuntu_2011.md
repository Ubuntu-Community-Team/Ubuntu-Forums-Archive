---
title: "Wireless not working on ubuntu 2011"
date: 2011-10-14
forum: Networking &amp; Wireless
---

### Post by odaijeriss on 2011-10-14
wireless not working at all.

Laptop model Dell Latitiude E6410
Ubuntu 11.04

connection manager shows:
Wireless Networks
Disconnected.

checked 

[sudo] password for odaijeriss: 
  *-network               
       description: Ethernet interface
       product: 82577LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 05
       serial: 00:26:b9:b6:f8:83
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.2.20-k2 duplex=full firmware=0.12-1 ip=192.168.2.5 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:40 memory:96900000-9691ffff memory:96980000-96980fff ioport:7040(size=32)
  *-network DISABLED
       description: Wireless interface
       product: Centrino Ultimate-N 6300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 35
       serial: 00:24:d7:03:ee:18
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-10-generic firmware=9.221.4.1 build 25532 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:44 memory:94100000-94101fff


any help pleeeeeeeeeeeeeeeeeeeeeeeez

---

### Post by praseodym on 2011-10-14
Hi,

this device may be "too new", install the latest driver and firmware via cable:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential 
wget http://www.orbit-lab.org/kernel/compat-wireless-2.6/compat-wireless-2.6.tar.bz2
tar jxvf compat-wireless-2.6.tar.bz2
cd compat-wireless-20*
make clean
make
sudo make install
wget http://media.cdn.ubuntu-de.org/forum/attachments/2767012/Intel_Firmware.tar.gz
sudo tar xvf Intel_Firmware.tar.gz -C /lib/firmware
```
Reboot.

After a kernel update (kernel -11 is up-to-date) the driver needs to be installed again via:

```
cd compat-wireless-20*
make clean
make
sudo make install
```
If kernel -11 is installed you should install the metapackage of the headers:

```
sudo apt-get install linux-headers-generic
```

---

### Post by odaijeriss on 2011-10-15
first of all thank you my friend for the reply:

i tried the procedure provided and got the following results, the first two was during the procedure the last one i got after issuing the last command

.c:1139:4: error: implicit declaration of function ‘olpc_ec_wakeup_clear’
/home/odaijeriss/compat-wireless-2011-10-14/drivers/net/wireless/libertas/if_usb.c:1141:4: error: implicit declaration of function ‘olpc_ec_wakeup_set’
make[4]: *** [/home/odaijeriss/compat-wireless-2011-10-14/drivers/net/wireless/libertas/if_usb.o] Error 1
make[3]: *** [/home/odaijeriss/compat-wireless-2011-10-14/drivers/net/wireless/libertas] Error 2
make[2]: *** [/home/odaijeriss/compat-wireless-2011-10-14/drivers/net/wireless] Error 2
make[1]: *** [_module_/home/odaijeriss/compat-wireless-2011-10-14] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-11-generic'
make: *** [modules] Error 2





/home/odaijeriss/compat-wireless-2011-10-14/drivers/net/wireless/libertas/if_usb.c: In function ‘if_usb_suspend’:
/home/odaijeriss/compat-wireless-2011-10-14/drivers/net/wireless/libertas/if_usb.c:1139:4: error: implicit declaration of function ‘olpc_ec_wakeup_clear’
/home/odaijeriss/compat-wireless-2011-10-14/drivers/net/wireless/libertas/if_usb.c:1141:4: error: implicit declaration of function ‘olpc_ec_wakeup_set’
make[4]: *** [/home/odaijeriss/compat-wireless-2011-10-14/drivers/net/wireless/libertas/if_usb.o] Error 1
make[3]: *** [/home/odaijeriss/compat-wireless-2011-10-14/drivers/net/wireless/libertas] Error 2
make[2]: *** [/home/odaijeriss/compat-wireless-2011-10-14/drivers/net/wireless] Error 2
make[1]: *** [_module_/home/odaijeriss/compat-wireless-2011-10-14] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-11-generic'
make: *** [modules] Error 2




odaijeriss@odaijeriss-Latitude-E6410:~/compat-wireless-2011-10-14$ sudo apt-get install linux-headers-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.38-8 linux-headers-2.6.38-8-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


* i believe that i installed the latest backport for wireless, so i believe this is what caused these errors to appear.

any thing else that might help me with this.

thank you again :)

---

### Post by praseodym on 2011-10-15
Uninstall the backport modules completely, reboot and try it again.

---

### Post by odaijeriss on 2011-10-16
i removed all the backports were installed.
reboot the system
following the procedure again

sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential  wget [http://www.orbit-lab.org/kernel/compat-wireless-2.6/compat-wireless-2.6.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-2.6/compat-wireless-2.6.tar.bz2) tar jxvf compat-wireless-2.6.tar.bz2 cd compat-wireless-20* make clean make <=== at this command i am getting  the following after some time from issuing the command:

/home/odaijeriss/compat-wireless-2011-10-14/drivers/net/wireless/libertas/if_usb.c:1139:4: error: implicit declaration of function ‘olpc_ec_wakeup_clear’
/home/odaijeriss/compat-wireless-2011-10-14/drivers/net/wireless/libertas/if_usb.c:1141:4: error: implicit declaration of function ‘olpc_ec_wakeup_set’
make[4]: *** [/home/odaijeriss/compat-wireless-2011-10-14/drivers/net/wireless/libertas/if_usb.o] Error 1
make[3]: *** [/home/odaijeriss/compat-wireless-2011-10-14/drivers/net/wireless/libertas] Error 2
make[2]: *** [/home/odaijeriss/compat-wireless-2011-10-14/drivers/net/wireless] Error 2
make[1]: *** [_module_/home/odaijeriss/compat-wireless-2011-10-14] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-11-generic'
make: *** [modules] Error 2

any idea why?

---

### Post by odaijeriss on 2011-10-16
i upgraded the system today to 11.10 and when issuing "sudo lshw -C network" i got the following:

odaijeriss@odaijeriss-Latitude-E6410:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82577LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 05
       serial: 00:26:b9:b6:f8:83
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.3.10-k2 duplex=full firmware=0.12-1 ip=192.168.12.28 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:40 memory:96900000-9691ffff memory:96980000-96980fff ioport:7040(size=32)
  *-network DISABLED
       description: Wireless interface
       product: Centrino Ultimate-N 6300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 35
       serial: 00:24:d7:03:ee:18
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=3.0.0-12-generic firmware=9.221.4.1 build 25532 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:44 memory:94100000-94101fff



Connection manager showing "device not ready"

any idea??

---

