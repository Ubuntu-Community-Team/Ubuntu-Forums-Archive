---
title: "Broadcom/8.10/Dell Inspiron 6000"
date: 2009-02-07
forum: Networking &amp; Wireless
---

### Post by woknam66 on 2009-02-07
I've been trying to get my wireless working on my laptop for some time now. Here's what I've tried.

With [this guide]("http://linuxwireless.org/en/users/Drivers/b43#firmware"), it's fine until I get to the command "make", then it tells me:```
make: Nothing to be done for `all'.

```



With [this guide]("https://help.ubuntu.com/community/WifiDocs/WiFiTroubleshooting"), it's fine until I get to step 5, then it tells me:```
bash: syntax error near unexpected token `newline'

```



With [this guide]("http://ubuntuforums.org/showthread.php?t=1059223"), in post 5, at the first command, it tells me:```
FATAL: Module ssb is in use.

```



With [this guide]("http://ubuntuforums.org/showthread.php?t=201902"), it's all fine until I get to step 11. In the command "make distclean", it tells me:```
make -C driver clean
make[1]: Entering directory `/home/woknam66/ndiswrapper/ndiswrapper-1.53/driver'
rm -f *.o *.ko .*.cmd *.mod.c *.symvers modules.order *~ .\#*
rm: cannot remove `built-in.o': Permission denied
rm: cannot remove `crt.o': Permission denied
rm: cannot remove `hal.o': Permission denied
rm: cannot remove `.built-in.o.cmd': Permission denied
rm: cannot remove `.crt.o.cmd': Permission denied
rm: cannot remove `.crt_exports.h.cmd': Permission denied
rm: cannot remove `.hal.o.cmd': Permission denied
rm: cannot remove `.hal_exports.h.cmd': Permission denied
rm: cannot remove `.ndis_exports.h.cmd': Permission denied
rm: cannot remove `.ntoskernel_exports.h.cmd': Permission denied
rm: cannot remove `.ntoskernel_io_exports.h.cmd': Permission denied
rm: cannot remove `.rtl_exports.h.cmd': Permission denied
rm: cannot remove `.usb_exports.h.cmd': Permission denied
make[1]: *** [clean] Error 1
make[1]: Leaving directory `/home/woknam66/ndiswrapper/ndiswrapper-1.53/driver'
make: *** [clean] Error 2

```
And I tried to install ndiswrapper from the live cd like it explains in number 13, but I couldn't find bcmwl5.inf using "Search for Files..." in the "Places" toolbar.



With [this guide]("http://linux.dell.com/wiki/index.php/Tech/Wireless/Truemobile_ndiswrapper"), it's all fine until step 5. In the command "sudo depmod -a", it tells me:```
WARNING: Module /lib/modules/2.6.27-11-generic/kernel/drivers/misc/ioc4.ko is not an elf object
WARNING: Module /lib/modules/2.6.27-11-generic/kernel/drivers/net/arcnet/rfc1201.ko is not an elf object
WARNING: Module /lib/modules/2.6.27-11-generic/kernel/drivers/net/at1700.ko is not an elf object

```

The command "sudo modprobe ndiswrapper" seems to go fine, but when I check for error messages with the command "tail /var/log/messages", it tells me:```
Feb  7 19:15:39 Alex-Laptop kernel: [ 7488.204596] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb  7 19:15:41 Alex-Laptop kernel: [ 7489.931537] VFS: busy inodes on changed media.
Feb  7 19:15:41 Alex-Laptop kernel: [ 7489.942432] VFS: busy inodes on changed media.
Feb  7 19:15:43 Alex-Laptop kernel: [ 7491.940619] VFS: busy inodes on changed media.
Feb  7 19:16:07 Alex-Laptop kernel: [ 7516.000256] b44: eth0: Link is up at 100 Mbps, full duplex.
Feb  7 19:16:07 Alex-Laptop kernel: [ 7516.000264] b44: eth0: Flow control is off for TX and off for RX.
Feb  7 19:16:07 Alex-Laptop kernel: [ 7516.001925] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Feb  7 19:31:16 Alex-Laptop -- MARK --
Feb  7 19:43:35 Alex-Laptop kernel: [ 9166.173875] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
Feb  7 19:43:35 Alex-Laptop kernel: [ 9166.216839] usbcore: registered new interface driver ndiswrapper

```



And [this guide]("http://ubuntuforums.org/showthread.php?t=684495") provides a nearly uncountable number of problems.



Here is some suggested information about my computer from [HOWTO post a Wireless issue]("http://ubuntuforums.org/showthread.php?p=6183681"):

1. Machine Brand and Model (PC/Laptop):
Dell Inspiron 6000 laptop0

2. Wireless Brand, Model and Wireless Chipset:```
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
03:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)

```

3. Check interface:
The relevant information from "ifconfig" is:```
wlan0     Link encap:Ethernet  HWaddr 00:0b:7d:15:f0:00  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
And the relevant information from "iwconfig" is:```
wlan0     Link encap:Ethernet  HWaddr 00:0b:7d:15:f0:00  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

4. Check for modules:
From "lsmod", it gives me tons of information, and I'm not sure which part of it is useful. And I'm not sure what to type between the quotes in "lsmod | grep "wlan_module_name"".

5. Kernel boot messages:
From "dmesg", it gives me tons of information, and I'm not sure which part of it is useful.

6. Network configuration:```
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:11:43:70:74:fe
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.123.199 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:0b:7d:15:f0:00
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 96:6f:98:ba:b2:2a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

7. Scan for networks:
The relevant information from "iwlist scan" is:```
wlan0     No scan results

```
But "iwlist scan wlan0" gave me an error message, but "iwlist wlan0 scan" worked.

8. Ubuntu Version:
8.10

9. Kernel/architecture (including 32 vs. 64 bit):
2.6.27-11-generic i686

10. Restarting the network:
When I type "sudo /etc/init.d/networking restart", it tells me:```
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]

```

---

### Post by ieee488 on 2009-02-08
You shouldn't need to do all of the steps in Step #11 if you have internet access via Ethernet (wired).

```
sudo apt-get install ndisgtk
``` was all I had to do to install ndiswrapper

---

### Post by superprash2003 on 2009-02-08
hope this helps [http://www.prash-babu.com/2008/11/how-to-configure-broadcom-wireless-in.html](http://www.prash-babu.com/2008/11/how-to-configure-broadcom-wireless-in.html)

---

### Post by woknam66 on 2009-02-08
ieee488:
I have a dual-boot system, and I needed to do some stuff in my windows boot, so I shut down ubuntu and booted up windows. I later hibernated windows and booted up ubuntu. I then realized that while trying to get the wifi to work on ubuntu, I had never restarted my computer. When ubuntu booted, the wifi worked. I still used the command "sudo apt-get install ndisgtk" to install ndiswrapper for that guide, and then finished the guide with no problems, just to be safe.

superprash2003:
My computer didn't find a "Broadcom STA wireless driver", it found a "Broadcom B43 wireless driver", which isn't a proprietary driver.

---

