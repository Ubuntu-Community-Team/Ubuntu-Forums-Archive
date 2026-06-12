---
title: "Can't connect with Intel 3945ABG Wireless"
date: 2009-05-01
forum: Networking &amp; Wireless
---

### Post by Modeverything on 2009-05-01
Hi everyone,

I have an HP nc8430 laptop with an Intel PRO/Wireless 3945ABG wireless card,and I cannot get it to activate or connect.  I am running Ubuntu 8.10, however before I upgraded, when I was running 8.04, my wireless worked fine.

I have searched and followed several thread's suggestions on how to make it work, but all I've done is made the problem worse.  I'll show the results of some queries, but I would also like to mention that I'm now using Wicd 1.5.9 instead of the standard network manager; this was another suggestion I found.

I'm not a Linux expert by any means, so my capabilities are somewhat limited.



mike@n843-001:~$ lspci | grep -i wireless
10:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)



mike@n843-001:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

pan0      no wireless extensions.




mike@n843-001:~$ lsmod | grep iwl



mike@n843-001:~$ dmesg | grep iwl



mike@n843-001:~$ sudo lshw -C network
[sudo] password for mike: 
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5753M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 21
       serial: 00:15:60:c3:d4:39
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full firmware=5753m-v3.56 ip=10.127.53.10 latency=0 link=yes module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Network controller
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: c2:46:72:03:58:f0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes




mike@n843-001:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

vmnet1    Interface doesn't support scanning.

vmnet8    Interface doesn't support scanning.

pan0      Interface doesn't support scanning.




mike@n843-001:~$ lsb_release -d
Description:	Ubuntu 8.10



mike@n843-001:~$ uname -mr
2.6.27-11-generic i686





Thanks in advance for any help!

---

### Post by chili555 on 2009-05-01
First of all, Network Manager will not connect wireless as long as wired is available and it is:> ip=10.127.53.10 latency=0 link=yes module=tg3Please detach the wire and do:```
sudo ifconfig eth0 down
sudo modprobe iwl3945
sudo ifconfig wlan0 up
```Do you have a wireless connection now? Can you click the Network Manager icon and see networks and connect?

---

### Post by Modeverything on 2009-05-01
That worked chili555!  Thanks a lot for the help!

I almost feel foolish for not realizing that wireless would not come up if the lan connection was active.

Well, I learned something new.

Thanks again.

---

### Post by chili555 on 2009-05-01
I am a little surprised that the driver didn't load automatically, even though NM wouldn't allow it to be used unless the wire was disconnected. If it doesn't load upon boot, simply do:```
sudo modprobe iwl3945
sudo gedit /etc/modules
```Add a single new line:```
iwl3945
```Proofread, save and close. You should be all fixed.

---

### Post by bellmh on 2009-06-12
Hi chili555,

I installed Ubuntu 9.04 parallel with Windows Vista on my Dell Inspiron e1705 which has the Intel 3945ABG wireless card.  After the installation and booting with Ubuntu everything was working except the wireless card.  

I know absolutely nothing about Linux and Ubuntu as far as the coding aspect and entering code.  

Would you mind helping me try to get my card recognized and work?  I also am using WPA

thanks,

Michael

---

### Post by chili555 on 2009-06-12
> I know absolutely nothing about Linux and Ubuntu as far as the coding aspect and entering code.Once upon a time, neither did we. Let's see if we can minimize the terminal and command line, although, if you have read my posts, you will see that I love my command line. First, let's define what you mean by, 'everything was working except the wireless card.' Do you see the Network Manager icon at the top right? When you click it, do you see your network? If you do and ask it to connect, does it try and fail? What, more precisely, are your symptoms?

Wow! So far, no terminal commands! I feel like a recovering addict!

---

### Post by idoisler on 2009-06-13
Hey all

I have tried to solve this issue in the past with no success 

I have just reinstalled Ubuntu in hope to try and solve it

I have done a few tests and here are the results 

please have a look and help me....

phoedo@phoedo-laptop:~$ lspci | grep -i wireless
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

phoedo@phoedo-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

phoedo@phoedo-laptop:~$ lsmod | grep iwl
iwl3945               100468  0 
iwlwifi_mac80211      251876  1 iwl3945
cfg80211               17680  1 iwlwifi_mac80211

phoedo@phoedo-laptop:~$ dmesg | grep iwl
[   35.395639] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   35.395643] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   35.396317] iwl3945: Detected Intel PRO/Wireless 3945BG Network Connection
[   36.063719] iwl3945: Tunable channels: 11 802.11bg, 0 802.11a channels
[   36.065052] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[   41.957840] iwl3945: Microcode SW error detected.  Restarting 0x82000008.
[   41.957863] iwl3945: Error Reply type 0x00000005 cmd REPLY_SCAN_CMD (0x80) seq 0x4418 ser 0x0000004B
[   42.964916] iwl3945: Can't stop Rx DMA.

phoedo@phoedo-laptop:~$ sudo lshw -C network
[sudo] password for phoedo: 
  *-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:a0:d1:85:51:24
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 02
       serial: 00:1c:bf:0e:70:ca
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g

phoedo@phoedo-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Failed to read scan data : Resource temporarily unavailable

phoedo@phoedo-laptop:~$ lsb_release -d
Description:	Ubuntu 8.04.2
phoedo@phoedo-laptop:~$ uname -mr
2.6.24-16-generic x86_64

---

### Post by chili555 on 2009-06-14
> iwl3945: Microcode SW error detected. Restarting 0x82000008.This seems to be the issue. A better driver, as well as newer microcode, also known as firmware, is in *linux-backports-modules-generic*. Can you please hook up an ethernet cable and get on line and install it with Synaptic? Then reboot and run:```
dmesg | grep iwl
```Let's see if we have overcome the microcode error and, more importantly, if you can connect.

---

### Post by idoisler on 2009-06-14
Hey there 
thank you for the replay 
but I am still in the dark here, I have no Idea what I should choose in the synaptic the are so many options.
I did a search for linux-backports-modules-generic it finds nothing, searching for linux-backports-modules, it suggests not to install it and instead install linux-generic meta-package but then again so many options 

also you mentioned microcode when I searched for that it gave me Intel IA32/IA64 CPU Microcode Utility, Is that what I need ?

I am using 
Toshiba satellite M200
Ubuntu 8.04.2
2.6.24-16-generic x86_64

---

### Post by chili555 on 2009-06-14
> 2.6.24-16-generic x86_64You are using Hardy. Many of us have moved along to Jaunty, including me, and are taxing our memories to remember the package name. Please try *linux-backports-modules-hardy* or *linux-backports-modules-hardy-generic*. It will complain if it's incorrect and install if it *is* correct.> Intel IA32/IA64 CPU Microcode Utility, Is that what I need ?
Nope. As the title suggests, it is microcode for your? some? CPUs.

---

### Post by idoisler on 2009-06-15
thank you for taking the time and helping me

I tried what you suggested, installing the module this is what i got after doing it
phoedo@phoedo-laptop:~$ dmesg | grep iwl
[   33.261457] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   33.261461] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   33.262074] iwl3945: Detected Intel PRO/Wireless 3945BG Network Connection
[   33.751326] iwl3945: Radio Frequency Kill Switch is On:
[   33.756414] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   33.766538] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   33.786658] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   33.814126] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
[   33.835528] iwl3945: Tunable channels: 11 802.11bg, 0 802.11a channels
[  214.945202] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[  215.963153] iwl3945: Microcode SW error detected.  Restarting 0x82000008.
[  215.963173] iwl3945: Error Reply type 0x00000005 cmd REPLY_SCAN_CMD (0x80) seq 0x4418 ser 0x0000004B
[  216.964643] iwl3945: Can't stop Rx DMA.

---

### Post by chili555 on 2009-06-15
Did you reboot after installing *backports*? May we please see:```
sudo cat /var/log/messages | grep iwl
sudo cat /var/log/messages | grep wlan
```Thanks.

---

### Post by idoisler on 2009-06-15
phoedo@phoedo-laptop:~$ sudo cat /var/log/messages | grep iwl
[sudo] password for phoedo: 
Jun 14 09:47:16 phoedo-laptop kernel: [   58.613158] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
Jun 14 09:47:16 phoedo-laptop kernel: [   58.613161] iwl3945: Copyright(c) 2003-2007 Intel Corporation
Jun 14 09:47:16 phoedo-laptop kernel: [   58.613777] iwl3945: Detected Intel PRO/Wireless 3945BG Network Connection
Jun 14 09:47:16 phoedo-laptop kernel: [   59.725399] iwl3945: Tunable channels: 11 802.11bg, 0 802.11a channels
Jun 14 10:17:53 phoedo-laptop kernel: [   47.723818] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
Jun 14 10:17:53 phoedo-laptop kernel: [   47.723822] iwl3945: Copyright(c) 2003-2007 Intel Corporation
Jun 14 10:17:53 phoedo-laptop kernel: [   47.768193] iwl3945: Detected Intel PRO/Wireless 3945BG Network Connection
Jun 14 10:17:53 phoedo-laptop kernel: [   48.173036] iwl3945: Tunable channels: 11 802.11bg, 0 802.11a channels
Jun 14 10:37:53 phoedo-laptop kernel: [ 1251.322992] iwl3945: Radio Frequency Kill Switch is On:
Jun 14 11:53:52 phoedo-laptop kernel: [   35.395639] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
Jun 14 11:53:52 phoedo-laptop kernel: [   35.395643] iwl3945: Copyright(c) 2003-2007 Intel Corporation
Jun 14 11:53:52 phoedo-laptop kernel: [   35.396317] iwl3945: Detected Intel PRO/Wireless 3945BG Network Connection
Jun 14 11:53:52 phoedo-laptop kernel: [   36.063719] iwl3945: Tunable channels: 11 802.11bg, 0 802.11a channels
Jun 14 12:08:43 phoedo-laptop kernel: [   42.567801] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
Jun 14 12:08:43 phoedo-laptop kernel: [   42.567805] iwl3945: Copyright(c) 2003-2007 Intel Corporation
Jun 14 12:08:43 phoedo-laptop kernel: [   42.568432] iwl3945: Detected Intel PRO/Wireless 3945BG Network Connection
Jun 14 12:08:43 phoedo-laptop kernel: [   43.037450] iwl3945: Tunable channels: 11 802.11bg, 0 802.11a channels
Jun 14 13:43:13 phoedo-laptop kernel: [ 5674.302263] iwl3945: Radio Frequency Kill Switch is On:
Jun 14 14:50:50 phoedo-laptop kernel: [   31.570460] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
Jun 14 14:50:50 phoedo-laptop kernel: [   31.570463] iwl3945: Copyright(c) 2003-2007 Intel Corporation
Jun 14 14:50:50 phoedo-laptop kernel: [   31.571085] iwl3945: Detected Intel PRO/Wireless 3945BG Network Connection
Jun 14 14:50:50 phoedo-laptop kernel: [   32.174612] iwl3945: Radio Frequency Kill Switch is On:
Jun 14 14:50:50 phoedo-laptop kernel: [   32.178789] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Jun 14 14:50:50 phoedo-laptop kernel: [   32.188919] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Jun 14 14:50:50 phoedo-laptop kernel: [   32.209044] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Jun 14 14:50:50 phoedo-laptop kernel: [   32.236511] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Jun 14 14:50:50 phoedo-laptop kernel: [   32.257978] iwl3945: Tunable channels: 11 802.11bg, 0 802.11a channels
Jun 14 20:47:05 phoedo-laptop kernel: [   41.487938] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
Jun 14 20:47:05 phoedo-laptop kernel: [   41.487946] iwl3945: Copyright(c) 2003-2007 Intel Corporation
Jun 14 20:47:05 phoedo-laptop kernel: [   41.489295] iwl3945: Detected Intel PRO/Wireless 3945BG Network Connection
Jun 14 20:47:05 phoedo-laptop kernel: [   44.134480] iwl3945: Radio Frequency Kill Switch is On:
Jun 14 20:47:05 phoedo-laptop kernel: [   44.140630] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Jun 14 20:47:05 phoedo-laptop kernel: [   44.150767] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Jun 14 20:47:05 phoedo-laptop kernel: [   44.170895] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Jun 14 20:47:05 phoedo-laptop kernel: [   44.198658] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Jun 14 20:47:05 phoedo-laptop kernel: [   44.218774] iwl3945: Tunable channels: 11 802.11bg, 0 802.11a channels
Jun 15 07:24:05 phoedo-laptop kernel: [   30.359433] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
Jun 15 07:24:05 phoedo-laptop kernel: [   30.359437] iwl3945: Copyright(c) 2003-2007 Intel Corporation
Jun 15 07:24:05 phoedo-laptop kernel: [   30.360051] iwl3945: Detected Intel PRO/Wireless 3945BG Network Connection
Jun 15 07:24:05 phoedo-laptop kernel: [   30.915908] iwl3945: Radio Frequency Kill Switch is On:
Jun 15 07:24:05 phoedo-laptop kernel: [   30.921060] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Jun 15 07:24:05 phoedo-laptop kernel: [   30.931184] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Jun 15 07:24:05 phoedo-laptop kernel: [   30.951303] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Jun 15 07:24:05 phoedo-laptop kernel: [   30.978772] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Jun 15 07:24:05 phoedo-laptop kernel: [   30.998864] iwl3945: Tunable channels: 11 802.11bg, 0 802.11a channels
Jun 15 22:31:56 phoedo-laptop kernel: [   45.035708] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
Jun 15 22:31:56 phoedo-laptop kernel: [   45.035712] iwl3945: Copyright(c) 2003-2007 Intel Corporation
Jun 15 22:31:56 phoedo-laptop kernel: [   45.036365] iwl3945: Detected Intel PRO/Wireless 3945BG Network Connection
Jun 15 22:31:56 phoedo-laptop kernel: [   45.369718] iwl3945: Radio Frequency Kill Switch is On:
Jun 15 22:31:56 phoedo-laptop kernel: [   45.375020] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Jun 15 22:31:56 phoedo-laptop kernel: [   45.385109] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Jun 15 22:31:56 phoedo-laptop kernel: [   45.405228] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Jun 15 22:31:56 phoedo-laptop kernel: [   45.432712] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Jun 15 22:31:56 phoedo-laptop kernel: [   45.453635] iwl3945: Tunable channels: 11 802.11bg, 0 802.11a channels
Jun 15 22:43:57 phoedo-laptop kernel: [   33.261457] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
Jun 15 22:43:57 phoedo-laptop kernel: [   33.261461] iwl3945: Copyright(c) 2003-2007 Intel Corporation
Jun 15 22:43:57 phoedo-laptop kernel: [   33.262074] iwl3945: Detected Intel PRO/Wireless 3945BG Network Connection
Jun 15 22:43:57 phoedo-laptop kernel: [   33.751326] iwl3945: Radio Frequency Kill Switch is On:
Jun 15 22:43:57 phoedo-laptop kernel: [   33.756414] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Jun 15 22:43:57 phoedo-laptop kernel: [   33.766538] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Jun 15 22:43:57 phoedo-laptop kernel: [   33.786658] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Jun 15 22:43:57 phoedo-laptop kernel: [   33.814126] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Jun 15 22:43:57 phoedo-laptop kernel: [   33.835528] iwl3945: Tunable channels: 11 802.11bg, 0 802.11a channels
Jun 15 22:53:16 phoedo-laptop kernel: [  596.188816] iwl3945: Radio Frequency Kill Switch is On:
Jun 15 22:59:04 phoedo-laptop kernel: [   32.605406] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
Jun 15 22:59:04 phoedo-laptop kernel: [   32.605410] iwl3945: Copyright(c) 2003-2007 Intel Corporation
Jun 15 22:59:04 phoedo-laptop kernel: [   32.606023] iwl3945: Detected Intel PRO/Wireless 3945BG Network Connection
Jun 15 22:59:04 phoedo-laptop kernel: [   33.038578] iwl3945: Radio Frequency Kill Switch is On:
Jun 15 22:59:04 phoedo-laptop kernel: [   33.044719] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Jun 15 22:59:04 phoedo-laptop kernel: [   33.054843] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Jun 15 22:59:04 phoedo-laptop kernel: [   33.074962] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Jun 15 22:59:04 phoedo-laptop kernel: [   33.102433] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Jun 15 22:59:04 phoedo-laptop kernel: [   33.122528] iwl3945: Tunable channels: 11 802.11bg, 0 802.11a channels
Jun 16 07:00:02 phoedo-laptop kernel: [   35.040765] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
Jun 16 07:00:02 phoedo-laptop kernel: [   35.040769] iwl3945: Copyright(c) 2003-2007 Intel Corporation
Jun 16 07:00:02 phoedo-laptop kernel: [   35.041384] iwl3945: Detected Intel PRO/Wireless 3945BG Network Connection
Jun 16 07:00:02 phoedo-laptop kernel: [   35.608456] iwl3945: Radio Frequency Kill Switch is On:
Jun 16 07:00:02 phoedo-laptop kernel: [   35.613608] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Jun 16 07:00:02 phoedo-laptop kernel: [   35.623738] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Jun 16 07:00:02 phoedo-laptop kernel: [   35.643863] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Jun 16 07:00:02 phoedo-laptop kernel: [   35.671330] iwl3945: WARNING: Requesting MAC access during RFKILL wakes up NIC
Jun 16 07:00:02 phoedo-laptop kernel: [   35.691433] iwl3945: Tunable channels: 11 802.11bg, 0 802.11a channels
phoedo@phoedo-laptop:~$ sudo cat /var/log/messages | grep wlan
Jun 14 09:47:16 phoedo-laptop kernel: [   63.962824] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 14 10:17:58 phoedo-laptop kernel: [   56.349866] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 14 10:25:14 phoedo-laptop kernel: [  492.742782] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 14 10:25:16 phoedo-laptop kernel: [  494.809839] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 14 10:26:18 phoedo-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Jun 14 10:31:20 phoedo-laptop kernel: [  858.457246] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 14 10:32:07 phoedo-laptop kernel: [  905.649495] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 14 10:35:09 phoedo-laptop kernel: [ 1087.319269] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 14 11:36:48 phoedo-laptop kernel: [ 4784.089895] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 14 11:37:58 phoedo-laptop kernel: [ 4854.025890] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 14 11:38:00 phoedo-laptop kernel: [ 4856.185190] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 14 11:38:09 phoedo-laptop kernel: [ 4864.904515] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 14 11:38:12 phoedo-laptop kernel: [ 4867.806974] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 14 11:38:12 phoedo-laptop kernel: [ 4868.180797] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 14 11:38:38 phoedo-laptop kernel: [ 4894.501350] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 14 11:38:55 phoedo-laptop kernel: [ 4911.376916] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 14 11:38:57 phoedo-laptop kernel: [ 4913.311269] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 14 11:45:25 phoedo-laptop kernel: [ 5300.908868] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 14 11:46:15 phoedo-laptop kernel: [ 5350.903542] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 14 11:54:18 phoedo-laptop kernel: [   66.008901] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 14 12:03:52 phoedo-laptop kernel: [  639.556343] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 14 12:09:08 phoedo-laptop kernel: [   71.869782] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 14 12:12:18 phoedo-laptop kernel: [  262.040234] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 14 12:12:20 phoedo-laptop kernel: [  264.100613] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 14 12:12:35 phoedo-laptop kernel: [  278.839354] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 14 12:13:16 phoedo-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Jun 14 12:13:50 phoedo-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Jun 15 22:46:54 phoedo-laptop kernel: [  215.051515] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 15 22:47:33 phoedo-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Jun 15 22:48:14 phoedo-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Jun 15 22:49:16 phoedo-laptop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan0 for sub-path wlan0.dbus.get.reason
Jun 16 07:04:30 phoedo-laptop kernel: [  307.734284] ADDRCONF(NETDEV_UP): wlan0: link is not ready
phoedo@phoedo-laptop:~$

---

### Post by chili555 on 2009-06-15
> iwl3945: Radio Frequency Kill Switch is OnI think I would try to manipulate the wireless switch or key combination first and get rid of this. Even though the kernel says:> WARNING: Requesting MAC access during RFKILL wakes up NICI am very skeptical that the hardware switch can be moved by software.

I suggest you open a terminal and do:```
sudo tail -f /var/log/messages
```Leave the terminal open as you move the switch. Look for a kernel message that indicates the RFKILL switch is off; that is, the wireless radio is now on.

Now can you connect?

---

### Post by idoisler on 2009-06-15
this is what I got before turning the wireless on 

phoedo@phoedo-laptop:~$ sudo tail -f /var/log/messages
[sudo] password for phoedo: 
Jun 16 07:26:36 phoedo-laptop kernel: [ 1631.974946] iwl3945: Radio Frequency Kill Switch is On:
Jun 16 07:26:36 phoedo-laptop kernel: [ 1631.974949] Kill switch must be turned off for wireless networking to work.
Jun 16 07:27:04 phoedo-laptop syslogd 1.5.0#1ubuntu1: restart.
Jun 16 07:27:07 phoedo-laptop kernel: [ 1663.724492] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 16 07:27:19 phoedo-laptop kernel: [ 1674.791413] sky2 eth0: Link is down.
Jun 16 07:27:37 phoedo-laptop kernel: [ 1692.799658] iwl3945: Radio Frequency Kill Switch is On:
Jun 16 07:27:37 phoedo-laptop kernel: [ 1692.799662] Kill switch must be turned off for wireless networking to work.
Jun 16 07:28:59 phoedo-laptop kernel: [ 1774.884761] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Jun 16 07:29:47 phoedo-laptop kernel: [ 1823.609971] iwl3945: Radio Frequency Kill Switch is On:
Jun 16 07:29:47 phoedo-laptop kernel: [ 1823.609974] Kill switch must be turned off for wireless networking to work.

When I turned the wireless I got this

Jun 16 07:30:39 phoedo-laptop kernel: [ 1875.002884] ADDRCONF(NETDEV_UP): wlan0: link is not ready


and Its not connecting 
but it dose seem to recognize that the key is on, when I look at the Icon when the key is on it says Enable wireless but I cant see any networks

---

### Post by chili555 on 2009-06-15
We are making progress. Now let's see if Network Manager is the problem or the driver. Please temporarily stop Network Manager:```
sudo /etc/init.d/NetworkManager stop
```Now, please do:```
sudo ifconfig wlan0 up
sudo iwlist wlan0 scan
```Now do you see your network?

---

### Post by idoisler on 2009-06-15
phoedo@phoedo-laptop:~$ sudo /etc/init.d/NetworkManager stop
[sudo] password for phoedo: 
sudo: /etc/init.d/NetworkManager: command not found
phoedo@phoedo-laptop:~$ sudo /etc/init.d/NetworkManager stop
sudo: /etc/init.d/NetworkManager: command not found
phoedo@phoedo-laptop:~$ sudo ifconfig wlan0 up
phoedo@phoedo-laptop:~$ sudo iwlist wlan0 scan
wlan0     Failed to read scan data : Resource temporarily unavailable

I went into /etc/init.d/ but there was no NetworkManager file in there ...

---

### Post by balloooza on 2009-06-15
chili555, I would like to ask (as a linux expert) this series of questions

Do you think that the iwl3924 driver should work out of the box on ubuntu 9.04 (is this issue you are helping with a crazy occurance, or is there a reason)

-**YES** - This is just a rare hardware occurrence.[INDENT]
[LIST]
[*] This is fully supported bu Ubuntu.
[/LIST]
[/INDENT]-**NO**  - The way Ubuntu comes dose not have this support, ready to use.[INDENT]
[LIST]
[*]      It is because the module dose not seem to load up on startup.
[/LIST]
[/INDENT][INDENT]
[LIST]
[*]     It is because the driver built for the card dose not work for the card. (story of my life) (out of the box)
[/LIST]
[/INDENT][INDENT]
[LIST]
[*]     Ubuntu dose not come with driver, this person I am helping has compiled this driver.
[/LIST]
[/INDENT]Then after this is resolved (*I hope* :) ) may you post a guide on what to do to get it to work, if it is not supported on the default Ubuntu install.
Mark

---

### Post by chili555 on 2009-06-15
> **balloooza said:**
> chili555, I would like to ask (as a linux expert) this series of questions

Do you think that the iwl3924 driver should work out of the box on ubuntu 9.04 (is this issue you are helping with a crazy occurance, or is there a reason)

-**YES** - This is just a rare hardware occurrence.[INDENT]
[LIST]
[*] This is fully supported bu Ubuntu.
[/LIST]
[/INDENT]-**NO**  - The way Ubuntu comes dose not have this support, ready to use.[INDENT]
[LIST]
[*]      It is because the module dose not seem to load up on startup.
[/LIST]
[/INDENT][INDENT]
[LIST]
[*]     It is because the driver built for the card dose not work for the card. (story of my life) (out of the box)
[/LIST]
[/INDENT][INDENT]
[LIST]
[*]     Ubuntu dose not come with driver, this person I am helping has compiled this driver.
[/LIST]
[/INDENT]Then after this is resolved (*I hope* :) ) may you post a guide on what to do to get it to work, if it is not supported on the default Ubuntu install.
MarkIt works perfectly for me and has since I installed 7.04 on this laptop two years ago and throughout every upgrade to 9.04 that I use today. I think that most problems are really Network Manager problems. That's why I don't use it.

It is, however, a bit of a chore to configure the *interfaces* file to set up your ESSID and encryption details. NM is supposed to do all that automagically for you but, in my opinion, fails a bit too often. It is still in beta, so a few issues are to be expected.

While I thank you for the compliment, I am no expert. I struggled through every mistake you can make in Linux since I began in 2001. Anyone ever set up HomePNA on Mandrake 7.1? After a while, I felt like I ought to share the hard lessons I learned with the newbies on the forums.

I have successfully used five different wireless cards over the years, all using the native drivers. The 3945ABG is the best I have used so far.

---

### Post by chili555 on 2009-06-15
> when I look at the Icon when the key is on it says Enable wireless but I cant see any networks> there was no NetworkManager file in there ... I wonder what the icon is that you are clicking, then. Did you remove Network Manager (I hope!)? May we please see:```
cat /etc/network/interfaces
```The thick plottens!

---

### Post by idoisler on 2009-06-18
Sorry for some reason I didn't get an email update of your response, I assumed you just didn't respond yet.

I am at work now and don't have the laptop with me, I will continue with out trails as soon as I can

by the way I didn't remove the network manager 
is there any program I should replace it with ?

Cheers

Ido

---

### Post by idoisler on 2009-06-21
phoedo@phoedo-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

---

### Post by chili555 on 2009-06-26
> there was no NetworkManager file in there ... I am not sure Network Manager will work correctly without an */etc/init.d/NetworkManager* file. You don't seem to have one and your wireless isn't working as expected. I wonder if they are related. Let's try to reinstall it and see if our luck improves:```
sudo apt-get install --reinstall network-manager
```I suggest a reboot. Now does clicking the Network Manager icon show your network? Can you connect?

---

### Post by idoisler on 2009-06-26
no nothing has changed

---

### Post by chili555 on 2009-06-27
Now do you have a file: */etc/init.d/NetworkManager*? If so, let's try to rule out...or in...Network Manager as our culprit.```
sudo /etc/init.d/NetworkManager stop
```Now let's see if we get a usable scan result:```
sudo iwlist wlan0 scan
```If you get a scan result and identify your network, let's try to connect:```
sudo iwconfig wlan0 essid your_scanned_network
sudo dhclient wlan0
```This assumes no encryption, WEP, WPA, etc. but at least we can see if the wireless card is responsive.

---

### Post by idoisler on 2009-06-27
phoedo@phoedo-laptop:~$ sudo /etc/init.d/NetworkManager stop
sudo: /etc/init.d/NetworkManager: command not found
phoedo@phoedo-laptop:~$ sudo iwlist wlan0 scan
wlan0     Failed to read scan data : Resource temporarily unavailable


Looks like nothing is working

---

### Post by chili555 on 2009-06-28
I am running out of ammunition here. Please try:```
sudo ifconfig wlan0 down
sudo rmmod -f iwl3945
sudo modprobe iwl3945 disable_hw_scan=1
sudo ifconfig wlan0 up
sudo iwlist wlan0 scan
```Any improvements?

---

### Post by idoisler on 2009-06-28
WOW it actually recognized that there are wireless networks around ......
didn't recognize mine due ....
but I know mine is fine, i do use it when I'm not on Linux

actually I think ESSID:"" is supposed to be my wireless


phoedo@phoedo-laptop:~$ sudo ifconfig wlan0 down
phoedo@phoedo-laptop:~$ sudo rmmod -f iwl3945
phoedo@phoedo-laptop:~$ sudo modprobe iwl3945 disable_hw_scan=1
phoedo@phoedo-laptop:~$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
phoedo@phoedo-laptop:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:12:0E:75:4E:88
                    ESSID:"aolbzCDry4Pg9R"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=55/100  Signal level=-75 dBm  Noise level=-127 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=00000479ca324be1
          Cell 02 - Address: 00:1B:11:F4:68:A8
                    ESSID:""
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=90/100  Signal level=-41 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000007b8a711f4
          Cell 03 - Address: 00:15:E9:01:89:5A
                    ESSID:"Ben's Wireless"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=40/100  Signal level=-85 dBm  Noise level=-127 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000002533ca6e1af

---

### Post by chili555 on 2009-06-28
Well now we're getting somewhere! Let's make this permanent:```
sudo gedit /etc/modprobe.d/iwl3945.conf
```It will start a new, empty file. Type in:```
alias wlan0 iwl3945 
options iwl3945 disable_hw_scan=1
```Proofread twice, save and close gedit.

If you click the Network Manager icon, do you see the option to connect to a Hidden network, which is what "" is?

If you search this forum, there seems to be many opinions about whether Network Manager will even connect to a WPA network that doesn't broadcast it's ESSID. I don't know, I've never tried.

Would you consider broadcasting the ESSID? I realize it's a security issue, however, anyone who can crack your WPA can detect your network with, or without broadcast. If they cannot crack it, you are secure enough!

---

### Post by idoisler on 2009-06-28
I don't see the option of hidden network 
the thing is when I use xp/vista it dose recognize the network under the name of phoedo, so I don't see why it shouldn't recognize it on Linux, could it be because it uses wap2
so I don't mind broadcasting as I do it anyway

---

### Post by chili555 on 2009-06-28
From here: [https://help.ubuntu.com/8.10/internet/C/wireless-connecting.html](https://help.ubuntu.com/8.10/internet/C/wireless-connecting.html) :> Connecting to a hidden network

   1. Left click the Network Manager icon in the system tray.
   2. Click Connect to Hidden Wireless Network
   3. In the network name text box enter the ESSID you are connecting to.
   4. Select the type of security used from the drop down list.
   5. Click Connect.I believe it will be similar for any version of Ubuntu, not just 8.10.

---

### Post by idoisler on 2009-06-29
for some reason although I should see my network, I don't, I also tried doing it manually as you suggested but it didn't work

---

### Post by chili555 on 2009-06-30
> although I should see my network, I don'tThat's how hidden ESSID's are supposed to work. May I assume you tried to add a hidden network, as described above, put in the ESSID phoedo and could not connect?

The next thing to try is to go into the administration pages of the router or access point and change it so the ESSID is broadcast instead of hidden.

Next, may I assume you are conducting your tests with the ethernet connection detached? Network Manager is designed to not allow a wireless connection if a wired connection is available.

Lastly, quite a few here have better luck with Wicd than Network Manager. [http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)  You would need to remove Network Manager and then install Wicd.

---

### Post by idoisler on 2009-06-30
I have no Idea what I did but I can now see my network 
I played with the router , the essid was broadcasting but I refreshed it from the router and now I can see the network but still can't connect 
I have inserted the correct password and all but it's not connecting (0%)

When I look at it under edit wireless connection, instead of my password it gives me a different very long one but every time I change it back , it goes back to the long one ?

---

### Post by idoisler on 2009-06-30
now it isn'r recognizing , acting wierd 

I think I'll try later on the Wicd

---

### Post by idoisler on 2009-06-30
anyway just wanted to thank you chili555, you helped me a lot!!!

thanks to you my wireless is working (at least recognizing other networks)

Cheers

Ido

---

