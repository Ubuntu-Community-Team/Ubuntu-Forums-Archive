---
title: "Compiling &quot;compat-wireless&quot; drivers"
date: 2012-06-25
forum: Networking &amp; Wireless
---

### Post by joblafors on 2012-06-25
Hello, so I managed to compile drivers, but when im trying to load it I get "FATAL: Module rt2x00 not found.". Could someone take a look am I doing something wrong? I'm fighting this problem for 2 days now, and managed to get this far, just the last step.

**MY CARD**
> 
*-network UNCLAIMED     
       description: Network controller
       product: RT2561/RT61 802.11g PCI
       vendor: Ralink corp.
       physical id: 7
       bus info: pci@0000:01:07.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32
       resources: memory:fb000000-fb007fff


**ME COMPILING - UNLOADING OLD - LOADING NEW DRIVER**
> 
home@home-desktop:~$ cd Desktop/compat3.5/compat-wireless-3.5-rc3-1/
home@home-desktop:~/Desktop/compat3.5/compat-wireless-3.5-rc3-1$ ./scripts/driver-select rt2x00
Processing new driver-select request...
Backup exists: Makefile.bk
Backup exists: drivers/net/wireless/Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: Makefile.bk
Backup exists: net/wireless/Makefile.bk
Backup exists: drivers/ssb/Makefile.bk
Backup exists: drivers/bcma/Makefile.bk
Backup exists: Makefile.bk
home@home-desktop:~/Desktop/compat3.5/compat-wireless-3.5-rc3-1$ make
make -C /lib/modules/3.2.0-25-generic/build M=/home/home/Desktop/compat3.5/compat-wireless-3.5-rc3-1 modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-25-generic'
  Building modules, stage 2.
  MODPOST 6 modules
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-25-generic'
home@home-desktop:~/Desktop/compat3.5/compat-wireless-3.5-rc3-1$ sudo make install
[sudo] password for home: 

make -C /lib/modules/3.2.0-25-generic/build M=/home/home/Desktop/compat3.5/compat-wireless-3.5-rc3-1 modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-25-generic'
  Building modules, stage 2.
  MODPOST 6 modules
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-25-generic'
make -C /lib/modules/3.2.0-25-generic/build M=/home/home/Desktop/compat3.5/compat-wireless-3.5-rc3-1 "INSTALL_MOD_DIR=updates"  \
		modules_install
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-25-generic'
  INSTALL /home/home/Desktop/compat3.5/compat-wireless-3.5-rc3-1/compat/compat.ko
  INSTALL /home/home/Desktop/compat3.5/compat-wireless-3.5-rc3-1/compat/sch_codel.ko
  INSTALL /home/home/Desktop/compat3.5/compat-wireless-3.5-rc3-1/compat/sch_fq_codel.ko
  INSTALL /home/home/Desktop/compat3.5/compat-wireless-3.5-rc3-1/net/mac80211/mac80211.ko
  INSTALL /home/home/Desktop/compat3.5/compat-wireless-3.5-rc3-1/net/rfkill/rfkill-regulator.ko
  INSTALL /home/home/Desktop/compat3.5/compat-wireless-3.5-rc3-1/net/wireless/cfg80211.ko
  DEPMOD  3.2.0-25-generic
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-25-generic'
depmod will prefer updates/ over kernel/ -- OK!

Now run:

sudo make unload to unload all: wireless, bluetooth and ethernet modules
sudo make wlunload to unload wireless modules
sudo make btunload to unload bluetooth modules

Run sudo modprobe driver-name to load your desired driver.
If unsure reboot.

home@home-desktop:~/Desktop/compat3.5/compat-wireless-3.5-rc3-1$ sudo make wlunload
Unloading eeprom_93cx6...
Unloading mac80211...
home@home-desktop:~/Desktop/compat3.5/compat-wireless-3.5-rc3-1$ sudo modprobe rt2x00
FATAL: Module rt2x00 not found.



---

### Post by chili555 on 2012-06-25
> home@home-desktop:~/Desktop/compat3.5/compat-wireless-3.5-rc3-1$ sudo modprobe rt2x00
FATAL: Module rt2x00 not found.rt2x00 is the name of a whole family of drivers; you want the specific driver name. Please try:```
sudo modprobe rt61pci
```Post back if you need additional guidance.

---

### Post by joblafors on 2012-06-25
Thank you, it seems I'm step further, now I get:
> 
home@home-desktop:~/Desktop/compat3.5/compat-wireless-3.5-rc3-1$ sudo modprobe rt61pci
WARNING: Error inserting rt2x00pci (/lib/modules/3.2.0-25-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko): Invalid argument
WARNING: Error inserting crc_itu_t (/lib/modules/3.2.0-25-generic/kernel/lib/crc-itu-t.ko): Invalid argument
FATAL: Error inserting rt61pci (/lib/modules/3.2.0-25-generic/kernel/drivers/net/wireless/rt2x00/rt61pci.ko): Invalid argument


> 
home@home-desktop:~/$ ls /lib/modules/3.2.0-25-generic/kernel/drivers/net/wireless/rt2x00
rt2400pci.ko  rt2500pci.ko  rt2500usb.ko  rt2800lib.ko  rt2800pci.ko  rt2800usb.ko  rt2x00lib.ko  rt2x00pci.ko  rt2x00usb.ko  rt61pci.ko  rt73usb.ko


---

### Post by chili555 on 2012-06-25
Would you please try a reboot so we have a clean slate? Then do:```
sudo modprobe rt61pci
dmesg | grep rt6
```Why did you decide to compile these drivers? Why didn't the built-in rt61pci work for you?

---

### Post by joblafors on 2012-06-25
After reboot:
> 
home@home-desktop:~$ sudo modprobe rt61pci
[sudo] password for home: 
WARNING: Error inserting rt2x00pci (/lib/modules/3.2.0-25-generic/kernel/drivers/net/wireless/rt2x00/rt2x00pci.ko): Invalid argument
WARNING: Error inserting crc_itu_t (/lib/modules/3.2.0-25-generic/kernel/lib/crc-itu-t.ko): Invalid argument
FATAL: Error inserting rt61pci (/lib/modules/3.2.0-25-generic/kernel/drivers/net/wireless/rt2x00/rt61pci.ko): Invalid argument
home@home-desktop:~$ dmesg | grep rt6
home@home-desktop:~$ 


And nothing in "/var/log//dmesg" about rt6 : (

---

### Post by chili555 on 2012-06-25
Why did you decide to compile these drivers? Why didn't the built-in rt61pci work for you? Also, why did you compile this bleeding edge, go fast version instead of the latest daily build?> compat-wireless-3.5-rc3-1In fact, why not just install the backports modules right out of Synaptic; essentially Ubuntu-ized compat-wireless?

---

### Post by joblafors on 2012-06-25
I want to set up my card to work in AP mode. And there is some sort of bug with channel showing up as -1 so I have to patch the drivers.

[http://www.aircrack-ng.org/doku.php?id=compat-wireless](http://www.aircrack-ng.org/doku.php?id=compat-wireless)

---

### Post by chili555 on 2012-06-25
Sorry, I can't help. I know nothing about aircrack and we don't support it here. I suggest you ask them.

---

### Post by joblafors on 2012-06-26
I managed to fix this.
I downloaded one version older "compat-wireless-3.4-rc3-1" and compiled all the drivers, then installed and they worked.
Thank you chili555 for all your help.

---

