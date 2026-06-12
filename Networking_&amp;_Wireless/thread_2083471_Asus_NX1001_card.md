---
title: "Asus NX1001 card"
date: 2012-11-12
forum: Networking &amp; Wireless
---

### Post by Oskarm on 2012-11-12
I have two network cards on my computer:
ASUS NX1001 and Realtek RTL 8111/8168B

For some reason I cannot get any one of them to work! I tried to install Realtek driver from the web and nothing happened! Asus has a CD with drivers for kernels 2.4 and 2.6, but none of the commands in README file work!

I am a beginner in this and I have searched around for AGES trying to get an answer for either two and I still can't find anything that would help me.

EDIT: I found the README file for Asus network card. None of this actually want to work.
```
                ASUS NX1001 Network Adapter  
                       Linux Driver  
 
Contents: 
----------- 
1. File Description 
2. Driver Installation for Linux 
3. Driver Parameter 
 
1. File Description 
------------------- 
 
Filename                Description 
====================    ======================================================= 
NX1001_main.c           ASUS NX1001 Network Adapter Driver Source Code. 
                        This file is the main part of ASUS NX1001 Network Adapter. 
 
compat.h                Network interface message level settings. 
 
crc32.h                 Crc function for early Linux 2.4.19pre kernel inclusion 
 
ethtool.h:              Defines for Linux ethtool. 
 
mii.h                   definitions for MII-compatible transceivers. 
 
mii.c                   MII interface library. 
 
makefile                Make File For ASUS NX1001 Network Adapter. 
                        Using "make all" for your kernel. 
 
readme.txt              A summary of the contents for Linux Driver. 
                        This file, which you are reading me now. 
 
 
 
2. Driver Installation for Linux 
----------------------------------------- 
a. for kernel 2.4.x 
   a1. Redhat 7.3 (linux kernel 2.4.18) 
   a2. Mandrake 8.1 (kernel 2.4.8) 
b. for kernel 2.6.x 
c. automatically load and configure at next boot time 
 
   a.for kernel 2.4.x 
   ------------------- 
     a1. Redhat 7.3 (linux kernel 2.4.18) 
     a1.1. install way 1: 
         #make all =>generate NX1001.o 
         #cp NX1001.o /lib/modules/2.4.18-3/kernel/drivers/net/ 
         #insmod ./NX1001.o 
         #ifconfig eth0 xxx.xxx.xxx.xxx netmask yyy.yyy.yyy.yyy 
            eth0 is your network adapter,use "dmesg" to check it, ex: eth0, eth1... 
            xxx  is your ip address, ex: 192.168.102.211 
            yyy  is your netmask address, ex:255.255.255.0 
 
     a1.2.  install way 2: 
        #make all =>generate NX1001.o 
        #cp NX1001.o /lib/modules/2.4.18-3/kernel/drivers/net/ 
        #insmod./NX1001.o 
        #setup 
        [network configuration] =>to setup your ip address 
        #ifup eth0 
           eth0 is your network adapter, ex: eth0, eth1...     
 
 
     a2. Mandrake 8.1 (kernel 2.4.8) 
       #make all  => generate Nx1001.o 
       #cp NX1001.o /lib/modules/2.4.8-26mdk/kernel/drivers/net 
       #insmod ./NX1001.o 
       #ifconfig eth0 xxx.xxx.xxx.xxx netmask yyy.yyy.yyy.yyy 
           eth0 is your network adapter,use "dmesg" to check it, ex: eth0, eth1... 
           xxx  is your ip address, ex: 192.168.102.211 
           yyy  is your netmask address, ex:255.255.255.0 
 
 
   b. for kernel 2.6.x 
   ------------------- 
      #make all  => generate NX1001.ko 
      #insmod ./NX1001.ko (or NX1001.o) 
      #ifconfig eth0 xxx.xxx.xxx.xxx netmask yyy.yyy.yyy.yyy 
            eth0 is your network adapter,use "dmesg" to check it, ex: eth0, eth1... 
            xxx  is your ip address, ex: 192.168.102.211 
            yyy  is your netmask address, ex:255.255.255.0       
    
   c. automatically load and configure at next boot time 
   ----------------------------------------------------- 
     c1. cp NX1001.o /lib/modules/`uname -r`/kernel/drivers/net 
     *note: The `uname -r` is a command. Don't replace `uname -r` with 
            2.4.18, 2.4.20smp, or some others. Must type `uname -r` directly. 
 
     c2. Add the following lines at /etc/modules.conf: 
                
          alias eth0 NX1001 
          options NX1001 <optional parameters> 
                               
     c3. Run "netconfig" or "netconf" to create configuration script  
 
              ifcfg-eth0 located at /etc/sysconfig/network-scripts or  
              create it manually. 
              [see - Configuration Script Sample] 
 
     c4. Driver will automatically load and configure at  
              next boot time. 
               
     c5. Configuration Script Sample 
     =========================== 
         Here is a sample of a simple configuration script: 
 
         DEVICE=eth0 
         USERCTL=no 
         ONBOOT=yes 
         POOTPROTO=none 
         BROADCAST=207.200.5.255 
         NETWORK=207.200.5.0 
         NETMASK=255.255.255.0 
         IPADDR=207.200.5.2 
               
 
3. Driver Parameter 
------------------- 
  If you want to change the link speed, you could use parameter after  
  insmod command. 
   
  insmod NX1001.o <optional parameter>    ; add parameter 
 
  ======================================================================== 
   example: insmod NX1001.o media=100mbps_hd 
   or        insmod NX1001.o media=3 
   or        insmod NX1001.o media=1,2,3,4    ; for 4 cards or NX1001 
  ========================================================================               
   
  Parameter Description 
  ===================== 
  You can install this driver without any addtional parameter. However, if  
  you are going to have extensive functions then it is necessary to set  
  extra parameter. Below is a list of the command line parameters supported  
  by the Linux device driver. 
 
media=xxxxxxxxx            - Specifies the media type the NIC operates at. 
                  autosense    Autosensing active media. 
                  10mbps_hd    10Mbps half duplex. 
                  10mbps_fd    10Mbps full duplex. 
                  100mbps_hd    100Mbps half duplex. 
                  100mbps_fd    100Mbps full duplex. 
                  0        Autosensing active media. 
                  1        10Mbps half duplex. 
                  2        10Mbps full duplex. 
                  3        100Mbps half duplex. 
                  4        100Mbps full duplex. 
                  By default, the copper devices operate at  
                  autosense, the fiber devices operate at 
                  100Mbps full duplex. 
                  Note that, the fiber adapter only support  
                  100Mbps half/full duplex types.     
 
  If wanting to change speed, this driver needed to be unloaded and reloaded with  
  new media parameter. 
 
flowctrl=[0|1]            - Specifies the flow control function. 
                  0    Disable flow control.     
                  1    Enable flow control.     

```

---

### Post by chili555 on 2012-11-12
Driver-dawg is here and we'll solve the mystery. First of all, this antique is mostly useless:> ASUS NX1001 Network Adapter  
                       Linux Driver  
 
Contents: 
----------- 
1. File Description 
2. Driver Installation for Linux 
3. Driver Parameter 
 <snip>It was written in 2005 (!!) which is 1492 in Linux years. It does, however, offer some clues. Here is a quote from the nx1001_main.c file:> // 04/13/2004 	{"Sundance Technology Alta"},
    {"ASUS NX1001 Network Adapter"},
    {"ASUS NX1001 Network Adapter" },
	{0,},			/* 0 terminated list. */'Sundance' you say?? We have a module named sundance in Ubuntu. Here is its modinfo:> $ modinfo sundance
filename:       /lib/modules/3.5.0-18-generic/kernel/drivers/net/ethernet/dlink/sundance.ko
license:        GPL
description:    Sundance Alta Ethernet driver
author:         Donald Becker <becker@scyld.com>
srcversion:     EFE11127C4FE4C585542FB2
alias:          pci:v000013F0d00000200sv*sd*bc*sc*i*
alias:          pci:v000013F0d00000201sv*sd*bc*sc*i*
alias:          pci:v00001186d00001002sv*sd*bc*sc*i*
alias:          pci:v00001186d00001002sv00001186sd00001040bc*sc*i*
alias:          pci:v00001186d00001002sv00001186sd00001012bc*sc*i*
alias:          pci:v00001186d00001002sv00001186sd00001003bc*sc*i*
alias:          pci:v00001186d00001002sv00001186sd00001002bc*sc*i*
depends:        
intree:         Y
vermagic:       3.5.0-18-generic SMP mod_unload modversions 
parm:           media:array of charp
parm:           debug:Sundance Alta debug level (0-5) (int)
parm:           rx_copybreak:Sundance Alta copy breakpoint for copy-only-tiny-frames (int)
parm:           flowctrl:Sundance Alta flow control [0|1] (int)
Let's see if your device is claimed by sundance. Please open a terminal and run and post:```
lspci -nn | grep 0200
uname -rp
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

Are you planning somehow to run both cards at the same time? Is the Realtek not working as expected?

---

### Post by Oskarm on 2012-11-13
Okay I did some tap tapping into terminal and here are the results.

```
lspci -nn | grep 0200
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 01)
05.00.0 Ethernet controller [0200]: Sundance Technology Inc / IC Plus Corp IC Plus IP100A Integrated 10/100 Ethernet MAC + PHY [13f0:0200] (rev 31)
```

```
uname -rp
3.2.0-29-generic x86_64
```

I am still using Ubuntu 12.04 on the PC mainly because it stays idle due to no internet connection.
The realtek card didn't even want to work under Windows. For some reason whenever I tried to install the driver for it, it changed its own name and declined that the driver was correct. Anyhow, that's the reason I got the Asus card and it works fine under Windows (because it has an auto-installer), but can't get it to work here just yet.

I don't plan to run both of them together, just one so I can start using ubuntu with internet. Right now I'm typing with laptop on my lap.

---

### Post by chili555 on 2012-11-13
> *Sundance* Technology Inc / IC Plus Corp IC Plus IP100A Integrated 10/100 Ethernet MAC + PHY [[COLOR="Red"]13f0:0200[/COLOR]]Here is a snip from the modinfo I posted above:> $ modinfo sundance | grep 13F0
alias:          pci:v0000[COLOR="Red"]13F0[/COLOR]d0000[COLOR="Red"]0200[/COLOR]sv*sd*bc*sc*i*
alias:          pci:v000013F0d00000201sv*sd*bc*sc*i*Let's save ourselves some anguish. In case the driver for the Realtek is trying to load and interfer, let's blacklist it:```
sudo su
echo 'blacklist r8169' >> /etc/modprobe.d/blacklist.conf
```Now, let's get *sundance* to load automagically:```
echo sundance >> /etc/modules
exit
```Now hook up the ethernet cable and reboot. Now run and post:```
ifconfig
dmesg | grep -e sundance -e eth
```Thanks.

---

### Post by Oskarm on 2012-11-13
Okay I did the blacklist thing then this:
```
oscar@ubuntu:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:26:18:eb:8f:9e  
          inet6 addr: fe80::226:18ff:feeb:8f9e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:247 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:35804 (35.8 KB)  TX bytes:6346 (6.3 KB)
          Interrupt:16 Base address:0xec00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

oscar@ubuntu:~$ dmesg | grep -e sundance -e eth
[    0.252496] i2c-core: driver [aat2870] using legacy suspend method
[    0.252498] i2c-core: driver [aat2870] using legacy resume method
[    1.365623] sundance.c:v1.2 11-Sep-2006 Written by Donald Becker
[    1.365669] sundance 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.366903] eth0: IC Plus Corporation IP100A FAST Ethernet Adapter at 000000000001ec00, 00:26:18:eb:8f:9e, IRQ 16.
[    1.367470] eth0: MII PHY found at address 0, status 0x7849 advertising 01e1.
[    9.023588] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    9.596669] udevd[386]: renamed network interface eth0 to eth1
[   10.701340] eth1: Link up
[   10.701646] eth1: Link changed: 100Mbps, full duplex

```

---

### Post by chili555 on 2012-11-13
Looking good so far! Are you using Network Manager? Is there any recognition of your Wired Network? Let's see what NM is doing behind the scenes:```
sudo cat /var/log/syslog | grep etwork | tail -n15
```

---

### Post by Oskarm on 2012-11-13
I'm not sure, if I have a Network Manager. I mean when I got to connections at the top of the screen it says Wired Network device not ready.

Anyway, more terminal results:
```
oscar@ubuntu:~$ sudo cat /var/log/syslog | grep etwork | tail -n15
[sudo] password for oscar: 
Nov 13 18:23:40 ubuntu NetworkManager[730]: <info> Networking is enabled by state file
Nov 13 18:23:40 ubuntu NetworkManager[730]: <warn> failed to allocate link cache: (-10) Operation not supported
Nov 13 18:23:40 ubuntu NetworkManager[730]: <info> (eth1): driver 'sundance' does not support carrier detection.
Nov 13 18:23:40 ubuntu NetworkManager[730]: <error> [1352831020.641210] [nm-device-ethernet.c:456] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 22)
Nov 13 18:23:40 ubuntu NetworkManager[730]: <info> (eth1): new Ethernet device (driver: 'sundance' ifindex: 2)
Nov 13 18:23:40 ubuntu NetworkManager[730]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/0
Nov 13 18:23:40 ubuntu NetworkManager[730]: <info> (eth1): now managed
Nov 13 18:23:40 ubuntu NetworkManager[730]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Nov 13 18:23:40 ubuntu NetworkManager[730]: <info> (eth1): bringing up device.
Nov 13 18:23:40 ubuntu NetworkManager[730]: nm_netlink_monitor_get_flags_sync: assertion `self != NULL' failed
Nov 13 18:23:40 ubuntu NetworkManager[730]: <warn> (eth1): couldn't get carrier state: (-1) unknown
Nov 13 18:23:40 ubuntu NetworkManager[730]: <info> (eth1): carrier now OFF (device state 20, deferring action for 4 seconds)
Nov 13 18:23:40 ubuntu NetworkManager[730]: <info> (eth1): preparing device.
Nov 13 18:23:40 ubuntu NetworkManager[730]: <info> (eth1): deactivating device (reason 'managed') [2]
Nov 13 18:23:40 ubuntu kernel: [   10.909915] type=1400 audit(1352831020.662:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=783 comm="apparmor_parser"
oscar@ubuntu:~$ 

```

---

### Post by chili555 on 2012-11-13
Let's see:```
cat /etc/network/interfaces
nm-tool
```And just for the amusement of an old student of networking:```
sudo modprobe -rf sundance
sudo modprobe  r8169
dmesg | grep r8169
```I ask for the latter so we can see if the Realtek can work.

---

### Post by Oskarm on 2012-11-13
EDIT: Please note, that I have to disconnect the ethernet cable from PC and put it in laptop, so I can actually post this. :)

I didn't know if r8169 was a typo or not so I did 8168 and 8169.
```
oscar@ubuntu:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

oscar@ubuntu:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sundance
  State:             unavailable
  Default:           no
  HW Address:        00:26:18:EB:8F:9E

  Capabilities:

  Wired Properties
    Carrier:         off

oscar@ubuntu:~$ sudo modprobe -rf sundance
[sudo] password for oscar: 
WARNING: All config files need .conf: /etc/modprobe.d/blacklist.confg, it will be ignored in a future release.
oscar@ubuntu:~$ sudo modprobe r8169
WARNING: All config files need .conf: /etc/modprobe.d/blacklist.confg, it will be ignored in a future release.
FATAL: Module r8169 not found.
oscar@ubuntu:~$ sudo modprobe r8168
WARNING: All config files need .conf: /etc/modprobe.d/blacklist.confg, it will be ignored in a future release.
oscar@ubuntu:~$ dmesg | grep r8169
oscar@ubuntu:~$ 
oscar@ubuntu:~$ dmesg | grep r8168
[    1.359474] r8168 Gigabit Ethernet driver 8.034.00-NAPI loaded
[    1.359506] r8168 0000:04:00.0: enabling device (0000 -> 0003)
[    1.359517] r8168 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.359530] r8168 0000:04:00.0: PowerManagement capability not found.
[    1.359547] r8168 0000:04:00.0: setting latency timer to 64
[    1.359624] Modules linked in: r8168(O+) pata_jmicron(+) floppy(+)
[    1.359732]  [<ffffffffa002cdf2>] rtl8168_init_one+0x673/0x2c6ff [r8168]
[    1.359814]  [<ffffffffa005f01e>] rtl8168_init_module+0x1e/0x1000 [r8168]
oscar@ubuntu:~$

```

---

### Post by chili555 on 2012-11-13
> WARNING: All config files need .conf: /etc/modprobe.d/blacklist.confg, it will be ignored in a future release.Quite a little problem we have here. Let's unravel this first:```
cat /etc/modprobe.d/blacklist.confg
```We'll put the contents in the correct place.

It appears you built the newer r816**8** module to replace the sometimes stubborn r816**9**. > [    [COLOR="Red"]1.359474[/COLOR]] r8168 Gigabit Ethernet driver 8.034.00-NAPI loadedThe timestamp indicates the r8168 module is being loaded as the computer is booting and therefor isn't effectively blacklisted.

---

### Post by Oskarm on 2012-11-13
Blacklist displays only one thing.
```
oscar@ubuntu:~$ cat /etc/modprobe.d/blacklist.confg
blacklist r8168
```

---

### Post by chili555 on 2012-11-13
Please do:```
sudo su
echo "blacklist r8168" >> /etc/modprbe.d/blacklist.conf
rm /etc/modprobe.d/blacklist.confg  [COLOR="Red"]<--proofread carefully before you press Enter![/COLOR]
exit
```Reboot and let us see:```
dmesg | grep r816
```Hopefully, it's blank.```
nm-tool
```I hope there is some change here:> Type:              Wired
  Driver:            sundance
  [COLOR="Red"]State:             unavailable[/COLOR]
  Default:           no
  HW Address:        00:26:18:EB:8F:9E

---

### Post by Oskarm on 2012-11-14
I typed in everything word for word (except the first line, where it said no such file or directory - modprbe.d/blacklist.conf
I did modprobe.d/blacklist.conf

Then the rest I did the same as you instructed and yet:
```
oscar@ubuntu:~$ dmesg | grep r816
[    1.388084] r8168 Gigabit Ethernet driver 8.034.00-NAPI loaded
[    1.388114] r8168 0000:04:00.0: enabling device (0000 -> 0003)
[    1.388125] r8168 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.388139] r8168 0000:04:00.0: PowerManagement capability not found.
[    1.388155] r8168 0000:04:00.0: setting latency timer to 64
[    1.388227] Modules linked in: r8168(O+) floppy pata_jmicron
[    1.388332]  [<ffffffffa002cdf2>] rtl8168_init_one+0x673/0x2c6ff [r8168]
[    1.388416]  [<ffffffffa005f01e>] rtl8168_init_module+0x1e/0x1000 [r8168]
oscar@ubuntu:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sundance
  State:             unavailable
  Default:           no
  HW Address:        00:26:18:EB:8F:9E

  Capabilities:

  Wired Properties
    Carrier:         off
```
Too bad it didn't go as planned. I also went to /etc/modprobe.d/blacklist.conf and found this at the end of the file:
```
# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist r8168
blacklist r8168
```

---

### Post by chili555 on 2012-11-14
> [    1.388084] r8168 Gigabit Ethernet driver 8.034.00-NAPI loaded
[    1.388114] r8168 0000:04:00.0: enabling device (0000 -> 0003)
[    1.388125] r8168 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.388139] r8168 0000:04:00.0: PowerManagement capability not found.
[    1.388155] r8168 0000:04:00.0: setting latency timer to 64
[    1.388227] Modules linked in: r8168(O+) floppy pata_jmicron
[    1.388332]  [<ffffffffa002cdf2>] rtl8168_init_one+0x673/0x2c6ff [r8168]
[    1.388416]  [<ffffffffa005f01e>] rtl8168_init_module+0x1e/0x1000 [r8168]
The module r8168 is somehow *still* loading! There must be some other file that invokes it. Let's see:```
cat /etc/modules
ls /etc/modprobe.d
```> (except the first line, where it said no such file or directory - modprbe.d/blacklist.conf
I did modprobe.d/blacklist.confGood catch; sorry about that.

*Chili cleans his glasses and monitor*

---

### Post by Oskarm on 2012-11-15
Sorry for the long delay in reply.. had a busy day. heh

Here's the stuff that were asked.

```
oscar@ubuntu:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
alias eth0 NX1001
options NX1001
sundance

oscar@ubuntu:~$ ls /etc/modprobe.d
alsa-base.conf           blacklist-framebuffer.conf   blacklist-watchdog.conf
blacklist-ath_pci.conf   blacklist-modem.conf         vmwgfx-fbdev.conf
blacklist.conf           blacklist-oss.conf
blacklist-firewire.conf  blacklist-rare-network.conf
```

---

### Post by chili555 on 2012-11-15
> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
[COLOR="Red"]alias eth0 NX1001
options NX1001[/COLOR]
sundanceThe parts I've highlighted are meaningless; they may be confusing to the system, I don't know. In either case, let's remove them:```
gksudo gedit /etc/modules
```Remove the highlighted lines so that it reads:```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
sundance
```Proofread, save and close gedit.

Is r8168 still loading as if by magic?```
lsmod | grep r816
```I am still trying to work out how; back in a few minutes.

EDIT: I still see no reason it's loading. Does it appear still in dmesg and lsmod?

---

### Post by Oskarm on 2012-11-16
Erased the part and saved.

Yes, r8168 still shows up in lsmod and dmesg.

---

### Post by chili555 on 2012-11-16
Frankly, I think our chances of getting the Realtek going are a lot better than the NX1001. If you are still convinced the NX1001 is a better choice, let's rename the r8168 driver so it won't load:```
sudo mv /lib/modules/`uname -r`/kernel/drivers/net/ethernet/realtek/r8168.ko /lib/modules/`uname -r`/kernel/drivers/net/ethernet/realtek/r8168.bak
```Those backticks are on the left side of my US keyboard on the same key with ~.

By renaming the r8168 driver, we can prevent it from loading and yet restore it again in the future if needed.

Reboot and confirm it's no longer in lsmod and demsg. Then let us see:```
sudo cat /var/log/syslog | grep -e sundance -e etwork | tail -n20
```

---

### Post by Oskarm on 2012-11-16
This is ridiculous. I have renamed the file as said, I checked if its there, rebooted and r8168 still shows up in lsmod and dmesg. 
It seems you are more than right - Asus just doesn't seem to be a good choice in this situation. I mean it works just fine on Windows, whilst Realtek doesn't work at all in there.
On Ubuntu, however, Realtek is the stubborn one...

I did the syslog and here's what showed up:
```
oscar@ubuntu:~$ sudo cat /var/log/syslog | grep -e sundance -e etwork | tail -n20
Nov 16 14:10:06 ubuntu NetworkManager[744]: <info> modem-manager is now available
Nov 16 14:10:06 ubuntu NetworkManager[744]: <info> monitoring kernel firmware directory '/lib/firmware'.
Nov 16 14:10:06 ubuntu NetworkManager[744]: <info> WiFi enabled by radio killswitch; enabled by state file
Nov 16 14:10:06 ubuntu NetworkManager[744]: <info> WWAN enabled by radio killswitch; enabled by state file
Nov 16 14:10:06 ubuntu NetworkManager[744]: <info> WiMAX enabled by radio killswitch; enabled by state file
Nov 16 14:10:06 ubuntu NetworkManager[744]: <info> Networking is enabled by state file
Nov 16 14:10:06 ubuntu NetworkManager[744]: <warn> failed to allocate link cache: (-10) Operation not supported
Nov 16 14:10:06 ubuntu NetworkManager[744]: <info> (eth1): driver 'sundance' does not support carrier detection.
Nov 16 14:10:06 ubuntu NetworkManager[744]: <error> [1353075006.175899] [nm-device-ethernet.c:456] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 22)
Nov 16 14:10:06 ubuntu NetworkManager[744]: <info> (eth1): new Ethernet device (driver: 'sundance' ifindex: 2)
Nov 16 14:10:06 ubuntu NetworkManager[744]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/0
Nov 16 14:10:06 ubuntu NetworkManager[744]: <info> (eth1): now managed
Nov 16 14:10:06 ubuntu NetworkManager[744]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Nov 16 14:10:06 ubuntu NetworkManager[744]: <info> (eth1): bringing up device.
Nov 16 14:10:06 ubuntu NetworkManager[744]: nm_netlink_monitor_get_flags_sync: assertion `self != NULL' failed
Nov 16 14:10:06 ubuntu NetworkManager[744]: <warn> (eth1): couldn't get carrier state: (-1) unknown
Nov 16 14:10:06 ubuntu NetworkManager[744]: <info> (eth1): carrier now OFF (device state 20, deferring action for 4 seconds)
Nov 16 14:10:06 ubuntu NetworkManager[744]: <info> (eth1): preparing device.
Nov 16 14:10:06 ubuntu NetworkManager[744]: <info> (eth1): deactivating device (reason 'managed') [2]
Nov 16 14:10:06 ubuntu kernel: [   10.445144] type=1400 audit(1353075006.201:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=781 comm="apparmor_parser"
```

I know it seems silly at this point, where we tried to get rid of Realtek by any means, but if it is really easier to get it working than Asus then I think we'd go with it.

---

### Post by chili555 on 2012-11-16
> if it is really easier to get it working than Asus then I think we'd go with it.I suspect it is. I suggest you physically remove the NX1001. Restore the r8168 driver:```
sudo mv /lib/modules/`uname -r`/kernel/drivers/net/ethernet/realtek/r8168.bak /lib/modules/`uname -r`/kernel/drivers/net/ethernet/realtek/r8168.ko
```Remove the blacklists:```
gksudo gedit /etc/modprobe.d/blacklist.conf
```Attach the ethernet cable to the Realtek and reboot. Then let us see:```
nm-tool
sudo cat /var/log/syslog | grep -e r816 -e etwork | tail -n20
```

> (eth1): unable to read permanent MAC address (error 22)This is probably most of the problem. I have no idea what to do to try to fix it.

---

### Post by Oskarm on 2012-11-17
Okay I removed the Asus card. I renamed the r8168 file, removed it from blacklist, put in the ethernet cable to realtek card (light started flashing) and rebooted.

However, here's the stuff from the terminal:
```
oscar@ubuntu:~$ nm-tool

NetworkManager Tool

State: disconnected

oscar@ubuntu:~$ sudo cat /var/log/syslog | grep -e r816 -e etwork | tail -n20
Nov 17 12:22:19 ubuntu avahi-daemon[746]: Network interface enumeration completed.
Nov 17 12:22:19 ubuntu kernel: [   11.102752] type=1400 audit(1353154939.846:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=775 comm="apparmor_parser"
Nov 17 12:22:19 ubuntu NetworkManager[721]:    SCPlugin-Ifupdown: init!
Nov 17 12:22:19 ubuntu NetworkManager[721]:    SCPlugin-Ifupdown: update_system_hostname
Nov 17 12:22:19 ubuntu NetworkManager[721]:    SCPluginIfupdown: management mode: unmanaged
Nov 17 12:22:19 ubuntu NetworkManager[721]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Nov 17 12:22:19 ubuntu NetworkManager[721]:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Nov 17 12:22:19 ubuntu NetworkManager[721]:    SCPlugin-Ifupdown: end _init.
Nov 17 12:22:19 ubuntu NetworkManager[721]: <info> Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Nov 17 12:22:19 ubuntu NetworkManager[721]: <info> Loaded plugin keyfile: (c) 2007 - 2010 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Nov 17 12:22:19 ubuntu NetworkManager[721]:    Ifupdown: get unmanaged devices count: 0
Nov 17 12:22:19 ubuntu NetworkManager[721]:    SCPlugin-Ifupdown: (11559072) ... get_connections.
Nov 17 12:22:19 ubuntu NetworkManager[721]:    SCPlugin-Ifupdown: (11559072) ... get_connections (managed=false): return empty list.
Nov 17 12:22:19 ubuntu NetworkManager[721]:    Ifupdown: get unmanaged devices count: 0
Nov 17 12:22:19 ubuntu NetworkManager[721]: <info> modem-manager is now available
Nov 17 12:22:19 ubuntu NetworkManager[721]: <info> monitoring kernel firmware directory '/lib/firmware'.
Nov 17 12:22:19 ubuntu NetworkManager[721]: <info> WiFi enabled by radio killswitch; enabled by state file
Nov 17 12:22:19 ubuntu NetworkManager[721]: <info> WWAN enabled by radio killswitch; enabled by state file
Nov 17 12:22:19 ubuntu NetworkManager[721]: <info> WiMAX enabled by radio killswitch; enabled by state file
Nov 17 12:22:19 ubuntu NetworkManager[721]: <info> Networking is enabled by state file
```
I am usually reading it as well just to learn what those messages mean. ;)

---

### Post by chili555 on 2012-11-17
Do you have an interface eth0?```
ifconfig
```Is eth0 listed in /etc/network/interfaces? We hope not.```
cat /etc/network/interfaces
```Any informative messages here?```
dmesg | grep r816
```

---

### Post by Oskarm on 2012-11-17
No eth0 in ifconfig:
```
oscar@ubuntu:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```No eth0 here neither:
```
oscar@ubuntu:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback
```And dmesg:
```
oscar@ubuntu:~$ dmesg | grep 816
[    0.248831] pci 0000:04:00.0: [10ec:8168] type 0 class 0x000200
[    0.248909] pci 0000:04:00.0: reg 20: [mem 0x816810e0-0x816810ff 64bit pref]
[    0.262836] pci 0000:04:00.0: no compatible bridge window for [mem 0x816810e0-0x816810ff 64bit pref]
[    0.284250] pci 0000:04:00.0: BAR 4: error updating (0xf000000c != 0x816810ec)
[    1.014816] ata1: SATA link down (SStatus 0 SControl 300)
[    1.323816] scsi8 : pata_jmicron
[    1.331214] r8168 Gigabit Ethernet driver 8.034.00-NAPI loaded
[    1.331246] r8168 0000:04:00.0: enabling device (0000 -> 0003)
[    1.331257] r8168 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.331270] r8168 0000:04:00.0: PowerManagement capability not found.
[    1.331287] r8168 0000:04:00.0: setting latency timer to 64
[    1.331369] Modules linked in: r8168(O+) pata_jmicron usb_storage
[    1.331476]  [<ffffffffa0026df2>] rtl8168_init_one+0x673/0x2c6ff [r8168]
[    1.331557]  [<ffffffffa005901e>] rtl8168_init_module+0x1e/0x1000 [r8168]
[    1.331572]  [<ffffffff81661ec2>] system_call_fastpath+0x16/0x1b
```

Also, Realtek doesn't work on Windows, but if we manage to get it working on Ubuntu, then I don't think that will matter too much. However, is there a way to have ASUS physically installed in my PC, so I can use it with Windows, but sort of blacklisted for Ubuntu?

---

### Post by chili555 on 2012-11-17
I think I am starting to get the bigger picture. The Realtek doesn't work because it's probably defective. I reluctantly hang my head and concede. 

Our next problem is to find r8168 and disable it. I downloaded and installed the package and looked for the method to uninstall it. It eludes me. All I know to do is search for and rename each and every instance of r8168.ko. Please do:```
sudo updatedb
locate r8168.ko
```updatedb takes a few moments, please be patient.

When you find them all, rename them .bak.```
sudo mv /lib/modules/`uname -r`/kernel/drivers/net/ethernet/realtek/r8168.ko /lib/modules/`uname -r`/kernel/drivers/net/ethernet/realtek/r8168.bak
````uname -r` is shorthand for your running kernel version. If you locate other instances, rename them to .bak similarly.

Remove sundance from the blacklist. Move the ethernet cable and reboot.

Now do:```
ifconfig
```Is there an interface, perhaps eth1? Then do:```
sudo ifconfig eth1 up
sudo dhclient eth1
```With Network Manager running, I'm not confident it will connect, but it may produce some interesting messages:```
dmesg | grep -e eth -e sundance
```Fingers crossed.

---

### Post by Oskarm on 2012-11-18
Okay I did all as said, found all the .ko files, renamed them. Sundance wasn't on blacklist. Anyway, I rebooted with cable plugged. Here is ifconfig:
```
oscar@ubuntu:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:26:18:eb:8f:9e  
          inet6 addr: fe80::226:18ff:feeb:8f9e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:395 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:64162 (64.1 KB)  TX bytes:3842 (3.8 KB)
          Interrupt:16 Base address:0xec00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```

And dmesg:
```
oscar@ubuntu:~$ sudo ifconfig eth1 up
oscar@ubuntu:~$ sudo dhclient eth1
oscar@ubuntu:~$ dmesg | grep -e eth -e sundance
[    0.251731] i2c-core: driver [aat2870] using legacy suspend method
[    0.251734] i2c-core: driver [aat2870] using legacy resume method
[    1.375832] sundance.c:v1.2 11-Sep-2006 Written by Donald Becker
[    1.375877] sundance 0000:05:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.376734] eth0: IC Plus Corporation IP100A FAST Ethernet Adapter at 000000000001ec00, 00:26:18:eb:8f:9e, IRQ 16.
[    1.377368] eth0: MII PHY found at address 0, status 0x7849 advertising 01e1.
[    8.665530] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    9.256581] udevd[372]: renamed network interface eth0 to eth1
[   10.636816] eth1: Link up
[   10.637137] eth1: Link changed: 100Mbps, full duplex
```

---

### Post by chili555 on 2012-11-18
> [   10.636816] eth1: Link up
[   10.637137] eth1: Link changed: 100Mbps, full duplexA good sign! When you click the Network Manager icon, is there any sign of an available wired connection? How about:```
nm-tool
sudo cat /var/log/syslog | grep -e eth1 -e etwork | tail -n20
cat /etc/network/interfaces
```I'm encouraged.

---

### Post by Oskarm on 2012-11-19
As again, it says Wired Connection device not ready.

It still shows up the same error as before: unable to read permanent MAC address:
```
oscar@ubuntu:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sundance
  State:             unavailable
  Default:           no
  HW Address:        00:26:18:EB:8F:9E

  Capabilities:

  Wired Properties
    Carrier:         off
```

```
oscar@ubuntu:~$ sudo cat /var/log/syslog | grep -e eth1 -e etwork | tail -n20
Nov 19 08:47:48 ubuntu NetworkManager[796]: <info> WWAN enabled by radio killswitch; enabled by state file
Nov 19 08:47:48 ubuntu NetworkManager[796]: <info> WiMAX enabled by radio killswitch; enabled by state file
Nov 19 08:47:48 ubuntu NetworkManager[796]: <info> Networking is enabled by state file
Nov 19 08:47:48 ubuntu NetworkManager[796]: <warn> failed to allocate link cache: (-10) Operation not supported
Nov 19 08:47:48 ubuntu NetworkManager[796]: <info> (eth1): driver 'sundance' does not support carrier detection.
Nov 19 08:47:48 ubuntu NetworkManager[796]: <error> [1353314868.959841] [nm-device-ethernet.c:456] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 22)
Nov 19 08:47:48 ubuntu NetworkManager[796]: <info> (eth1): new Ethernet device (driver: 'sundance' ifindex: 2)
Nov 19 08:47:48 ubuntu NetworkManager[796]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/0
Nov 19 08:47:48 ubuntu NetworkManager[796]: <info> (eth1): now managed
Nov 19 08:47:48 ubuntu NetworkManager[796]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Nov 19 08:47:48 ubuntu NetworkManager[796]: <info> (eth1): bringing up device.
Nov 19 08:47:48 ubuntu NetworkManager[796]: nm_netlink_monitor_get_flags_sync: assertion `self != NULL' failed
Nov 19 08:47:48 ubuntu NetworkManager[796]: <warn> (eth1): couldn't get carrier state: (-1) unknown
Nov 19 08:47:48 ubuntu NetworkManager[796]: <info> (eth1): carrier now OFF (device state 20, deferring action for 4 seconds)
Nov 19 08:47:48 ubuntu NetworkManager[796]: <info> (eth1): preparing device.
Nov 19 08:47:48 ubuntu NetworkManager[796]: <info> (eth1): deactivating device (reason 'managed') [2]
Nov 19 08:47:48 ubuntu kernel: [   11.228759] type=1400 audit(1353314868.982:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=856 comm="apparmor_parser"
Nov 19 08:47:50 ubuntu avahi-daemon[821]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::226:18ff:feeb:8f9e.
Nov 19 08:47:50 ubuntu avahi-daemon[821]: New relevant interface eth1.IPv6 for mDNS.
Nov 19 08:47:50 ubuntu avahi-daemon[821]: Registering new address record for fe80::226:18ff:feeb:8f9e on eth1.*.
```

```
oscar@ubuntu:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

```

---

### Post by chili555 on 2012-11-19
> It still shows up the same error as before: unable to read permanent MAC address:Weird, because we know the MAC address:> eth1      Link encap:Ethernet  HWaddr [COLOR="Red"]00:26:18:eb:8f:9e  [/COLOR]
          inet6 addr: fe80::226:18ff:feeb:8f9e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:395 errors:0 dropped:0 overruns:0 frame:0You might right-click the Network Manager icon and select 'Edit Connections,' edit eth1 and try to place the MAC address in the appropriate slot. Save and close. Then try to connect.

Please see attached. Please note, yours will be in the form 00:26:18:EB:8F:9E. Also, the leading characters are zeros.

---

### Post by Oskarm on 2012-11-19
Network manager even find eth1 device in a drop down list with correct MAC address. It creates a wired connection entry, but doesn't connect. It still displays as device not ready.
All the information still look the same.

---

### Post by chili555 on 2012-11-19
I am getting pretty low on ideas. Let's try a driver parameter temporarily:```
sudo modprobe -r sundance
sudo modprobe sundance media=autosense
```Now let's see if it has made an improvement. Try to connect and then do:```
sudo cat /var/log/syslog | grep -e eth1 -e etwork -e sundance | tail -n20
```

---

### Post by Oskarm on 2012-11-20
Something change I think, don't know if for good or bad.
```
oscar@ubuntu:~$ sudo cat /var/log/syslog | grep -e eth1 -e etwork | tail -n20
Nov 20 09:13:25 ubuntu NetworkManager[798]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Nov 20 09:13:25 ubuntu NetworkManager[798]: <info> Unmanaged Device found; state CONNECTED forced. (see http://bugs.launchpad.net/bugs/191889)
Nov 20 09:13:39 ubuntu NetworkManager[798]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:05:00.0/net/eth1, iface: eth1)
Nov 20 09:13:39 ubuntu NetworkManager[798]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:05:00.0/net/eth1, iface: eth1): no ifupdown configuration found.
Nov 20 09:13:39 ubuntu NetworkManager[798]: <warn> failed to allocate link cache: (-10) Operation not supported
Nov 20 09:13:39 ubuntu NetworkManager[798]: <info> (eth1): driver 'sundance' does not support carrier detection.
Nov 20 09:13:39 ubuntu NetworkManager[798]: <error> [1353402819.18935] [nm-device-ethernet.c:456] real_update_permanent_hw_address(): (eth1): unable to read permanent MAC address (error 22)
Nov 20 09:13:39 ubuntu NetworkManager[798]: <info> (eth1): new Ethernet device (driver: 'sundance' ifindex: 3)
Nov 20 09:13:39 ubuntu NetworkManager[798]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/1
Nov 20 09:13:39 ubuntu NetworkManager[798]: <info> (eth1): now managed
Nov 20 09:13:39 ubuntu NetworkManager[798]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Nov 20 09:13:39 ubuntu NetworkManager[798]: <info> (eth1): bringing up device.
Nov 20 09:13:39 ubuntu NetworkManager[798]: nm_netlink_monitor_get_flags_sync: assertion `self != NULL' failed
Nov 20 09:13:39 ubuntu NetworkManager[798]: <warn> (eth1): couldn't get carrier state: (-1) unknown
Nov 20 09:13:39 ubuntu NetworkManager[798]: <info> (eth1): carrier now OFF (device state 20, deferring action for 4 seconds)
Nov 20 09:13:39 ubuntu NetworkManager[798]: <info> (eth1): preparing device.
Nov 20 09:13:39 ubuntu NetworkManager[798]: <info> (eth1): deactivating device (reason 'managed') [2]
Nov 20 09:13:40 ubuntu avahi-daemon[815]: Joining mDNS multicast group on interface eth1.IPv6 with address fe80::226:18ff:feeb:8f9e.
Nov 20 09:13:40 ubuntu avahi-daemon[815]: New relevant interface eth1.IPv6 for mDNS.
Nov 20 09:13:40 ubuntu avahi-daemon[815]: Registering new address record for fe80::226:18ff:feeb:8f9e on eth1.*.
```

---

### Post by Oskarm on 2012-11-23
Does it mean I should just give up and get a card that works on ubuntu?

---

### Post by chili555 on 2012-11-23
> **Oskarm said:**
> Does it mean I should just give up and get a card that works on ubuntu?I'm sorry to say I have no other suggestions than just that.

---

