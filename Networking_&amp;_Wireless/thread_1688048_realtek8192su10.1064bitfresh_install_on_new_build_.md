---
title: "realtek8192su/10.1064bit/fresh install on new build desktop"
date: 2011-02-14
forum: Networking &amp; Wireless
---

### Post by newbiejosh on 2011-02-14
I have no "enable wireless" option from network manager.  I successfully installed the 8172 driver, however upon enabling it causes a system freeze, and I'm forced to use the reset button.  I have no clue how to proceed from here.  Data that might be of use from the "how to post" thread:

lsusb
Bus 002 Device 002: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191S WLAN Adapter

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:25:22:86:80:da  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::225:22ff:fe86:80da/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1157 errors:0 dropped:0 overruns:0 frame:0
          TX packets:736 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:660314 (660.3 KB)  TX bytes:188407 (188.4 KB)
          Interrupt:42 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

$ iwconfig wlan0
wlan0     No such device


sudo lshw -c network
[sudo] password for josh: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: 00:25:22:86:80:da
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.104 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:42 ioport:e800(size=256) memory:fafff000-faffffff memory:faff8000-faffbfff memory:febe0000-febfffff


 sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]

---

### Post by newbiejosh on 2011-02-15
UPDATE:

Completely reinstalled ubuntu 10.10 and freshly installed drivers.  I now get a result back from iwconfig:


iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  ESSID:"g\xC6isQ\xFFJ\xEC)\xCD\xBA\xAB\xF2\xFB\xE3F|\xC2T\xF8\x1B\xE8\xE7\x8DvZ.c3\x9F\xC9\x9A"  
          Mode:Managed  Access Point: Not-Associated   Bit Rate:0 kb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

however when I go to enter: ifconflag wlan) up
ifconfig wlan0 up
SIOCSIFFLAGS: Resource temporarily unavailable


Seems so close... any input?

---

### Post by newbiejosh on 2011-02-16
Another update!  

lsmod returns
r8192s_usb            317763  0 
eeprom_93cx6            1789  1 r8192s_usb

I've tried blacklisting the eeprom_93cx6 by adding it to the blacklist.conf and I've tried using the command
rmmod eeprom_93cx6
ERROR: Module eeprom_93cx6 is in use by r8192s_usb

So I'm thinking at this point it should be pretty easy, as I'm guessing I just need a command to make the r8192s_usb stop using the incorrect driver, and remove it using rmmod, then modprobe the correct drivers?  Only problem is... I have not a clue how to do that!  

Thanks for the help!

---

### Post by chili555 on 2011-02-16
Josh, Josh, Josh! Let's untangle this bucket of snakes. First of all:> $ modinfo r8192s_usb
filename:       /lib/modules/2.6.35-25-generic/kernel/drivers/staging/rtl8192su/r8192s_usb.ko
firmware:       RTL8192SU/rtl8192sfw.bin
description:    Linux driver for Realtek RTL8192 USB WiFi cards
version:        V 1.1
license:        GPL
license:        GPL
description:    HostAP crypto
author:         Jouni Malinen
license:        GPL
description:    Host AP crypt: TKIP
author:         Jouni Malinen
license:        GPL
description:    Host AP crypt: CCMP
author:         Jouni Malinen
license:        GPL
description:    Host AP crypt: WEP
author:         Jouni Malinen
license:        GPL
author:         Copyright (C) 2004 Intel Corporation <jketreno@linux.intel.com>
description:    802.11 data/management/control stack
srcversion:     93926278505B0EDEC322B52
alias:          usb:v0DF6p004Bd*dc*dsc*dp*ic*isc*ip*
--- snip ---
alias:          usb:v0BDAp8172d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8171d*dc*dsc*dp*ic*isc*ip*
[COLOR="Red"]depends:        eeprom_93cx6[/COLOR]
staging:        Y
vermagic:       2.6.35-25-generic SMP mod_unload modversions 686 
parm:           debug:debug output mask (int)
parm:           ifname: Net interface name, wlan%d=default (charp)
parm:           hwwep: Try to use hardware security support.  (int)
parm:           channels: Channel bitmask for specific locales. NYI (int)
So remove the blacklist, if it's still there. The eeprom_93cx6 module is *required*. Second, let's see if there are any kernel messages about this issue:```
dmesg | grep 819
```I suspect it's a firmware issue.

Is yours a 32- or 64-bit system?

---

### Post by newbiejosh on 2011-02-16
Thanks Chilli  Its a 64 bit system

josh@josh-desktop:~$ dmesg | grep 819
[    0.000000] PERCPU: Embedded 30 pages/cpu @ffff880001e00000 s91520 r8192 d23168 u262144
[    0.000000] pcpu-alloc: s91520 r8192 d23168 u262144 alloc=1*2097152
[    8.642846] r8192s_usb: module is from the staging directory, the quality is unknown, you have been warned.
[    8.652198] Linux kernel driver for RTL8192 based WLAN cards
[    8.916544] usbcore: registered new interface driver rtl819xU
[    9.269078] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[    9.269324] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[    9.283449] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[    9.283697] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[    9.283701] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[    9.306116] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[    9.306310] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[    9.320063] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[    9.320234] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[    9.320238] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[  101.780331] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[  101.780853] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[  101.796613] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[  101.796943] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[  101.796951] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[  640.633352] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[  640.634631] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[  640.650750] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[  640.651437] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[  640.651448] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[ 4620.223924] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[ 4620.224791] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[ 4620.244736] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[ 4620.245535] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[ 4620.245548] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[ 4985.660841] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[ 4985.661443] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[ 4985.683769] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[ 4985.683968] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[ 4985.683980] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[ 4993.260978] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[ 4993.261652] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[ 4993.280333] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[ 4993.280998] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[ 4993.281010] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!
[ 5382.565606] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[ 5382.566316] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[ 5382.583903] rtl819xU:FirmwareRequest92S(): failed with TCR-Status: a
[ 5382.584128] rtl819xU:FirmwareDownload92S(): failed with TCR-Status: a
[ 5382.584131] rtl819xU:ERR!!! _rtl8192_up(): initialization is failed!

---

### Post by chili555 on 2011-02-16
A firmware error. Whadda ya know?

Please see: [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html)

Their fix misses one step; here is a corrected sequence:```
sudo mkdir /lib/firmware/RTL8192SU
wget http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz
gunzip rtl8192sfw.bin.gz
sudo mv rtl8192sfw.bin /lib/firmware/RTL8192SU/

```Reboot and the wireless should be working.

---

### Post by valica1234 on 2011-03-13
> **chili555 said:**
> A firmware error. Whadda ya know?

Please see: [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html)

Their fix misses one step; here is a corrected sequence:```
sudo mkdir /lib/firmware/RTL8192SU
wget http://launchpadlibrarian.net/37387612/rtl8192sfw.bin.gz
gunzip rtl8192sfw.bin.gz
sudo mv rtl8192sfw.bin /lib/firmware/RTL8192SU/

```Reboot and the wireless should be working.

chili thank you very much for this fix.

I've just started using Ubuntu and after searching for a few hours for a way to make my WiFi USB adapter work I was getting ready to wait for the next release.

again, many thanks!

---

