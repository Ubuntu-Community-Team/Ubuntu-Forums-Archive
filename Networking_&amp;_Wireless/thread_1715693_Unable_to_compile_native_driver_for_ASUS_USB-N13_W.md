---
title: "Unable to compile native driver for ASUS USB-N13 Wireless device"
date: 2011-03-27
forum: Networking &amp; Wireless
---

### Post by MuchaLucha on 2011-03-27
1. Installed a fresh 10.10 and upgraded all packages (via Ethernet).
2. Downloaded latest drivers from ASUS webiste (DPO_RT3070_LinuxSTA_V2.3.0.2_20100422)
3. Unpacked and tried to compile:

 tar -zxvd DPO_RT3070_LinuxSTA_V2.3.0.2_20100422.tgz
 cd DPO_RT3070_LinuxSTA_V2.3.0.2_20100422
 make

4. Compilation error:

 /home/monkey/Downloads/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/cmm_mac_usb.c: In function ‘NICInitRecv’:
 /home/monkey/Downloads/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/cmm_mac_usb.c:83: error: implicit declaration of function ‘usb_buffer_alloc’
 /home/monkey/Downloads/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/cmm_mac_usb.c:83: warning: assignment makes pointer from integer without a cast
 /home/monkey/Downloads/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/cmm_mac_usb.c:112: error: implicit declaration of function ‘usb_buffer_free’
 make[2]: *** [/home/usaaib/Downloads/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux/../../common/cmm_mac_usb.o] Error 1
 make[1]: *** [_module_/home/usaaib/Downloads/Linux/DPO_RT3070_LinuxSTA_V2.3.0.2_20100422/os/linux] Error 2
 make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic'
 make: *** [LINUX] Error 2

I tried to follow suggestions from other threads but to no avail.

The wireless card is working with the driver rt2870sta, but I've read not all the capabilities of the device is unleash unless the native driver is used.

Any suggestions are welcome, thanks in advance for the support.

Regards.

---

### Post by MuchaLucha on 2011-03-27
Good news I was able to compile the driver using the source code distributed directly from RALinkTech:

[http://www.ralinktech.com/download.php?t=U0wyRnpjMlYwY3k4eU1ERXhMekF4THpFM0wyUnZkMjVzYjJGa016STJNekEyTnpZek5DNWllakk5UFQweU1ERXhYekF4TURkZlVsUXpNRGN3WDFKVU16TTNNRjlNYVc1MWVGOVRWRUZmZGpJdU5TNHdMakZmUkZCUExuUmhjZz09Qw==](http://www.ralinktech.com/download.php?t=U0wyRnpjMlYwY3k4eU1ERXhMekF4THpFM0wyUnZkMjVzYjJGa016STJNekEyTnpZek5DNWllakk5UFQweU1ERXhYekF4TURkZlVsUXpNRGN3WDFKVU16TTNNRjlNYVc1MWVGOVRWRUZmZGpJdU5TNHdMakZmUkZCUExuUmhjZz09Qw==)

the fie is named incorrectly since it has a bz2 extension, however its gziip file.

sudo make
sudo make install

now work, I'm heading now to replace the rt2870sta module with the new rt3070sta one.

Regards,

---

### Post by bkratz on 2011-03-27
As per this thread-- post #22

[http://ubuntuforums.org/showthread.php?t=1473762&page=3](http://ubuntuforums.org/showthread.php?t=1473762&page=3)

Did you "
 Open System > Administration > Synaptic and install linux-headers-generic and build-essential. "

before compiling?

Probably should have renewed the page before posting!!
Looking for this thread

---

