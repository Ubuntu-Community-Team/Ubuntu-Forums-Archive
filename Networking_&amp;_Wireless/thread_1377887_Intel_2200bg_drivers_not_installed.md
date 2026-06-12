---
title: "Intel 2200bg drivers not installed"
date: 2010-01-10
forum: Networking &amp; Wireless
---

### Post by stratcat250 on 2010-01-10
I just installed 9.10 desktop on a Dell Inspiron 6000 with the Intel Pro/Wireless 2200bg network card. 
the device shows in lspci but nowhere in iwconfig. All I show is eth0 which is my ethernet adapter. From what I see in the forums this device should install out of the box. I have downloaded the drivers from the Intel website but I will wait for an answer here to install them. Thanx 

BTW The wireless adapter works on my windows partition so I know it's not disabled.

---

### Post by chili555 on 2010-01-10
They *are* installed! Please open a terminal and do:```
sudo modprobe ipw2200
```If that doesn't kick your wireless device to life, then please post:```
sudo lshw -C network
dmesg | grep ipw
```Thanks.

---

### Post by stratcat250 on 2010-01-10
Thanks, no result with sudo modprobe ipw2200


> user@user-laptop:~$ sudo modprobe ipw2200
[sudo] password for user: 
user@user-laptop:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:ee:fc:ad
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.0.184 latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:18 memory:dfcfe000-dfcfffff
  *-network:1 UNCLAIMED
       description: Network controller
       product: PRO/Wireless 2200BG [Calexico2] Network Connection


> user@user-laptop:~$ dmesg | grep ipw
[   19.387633] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   19.387638] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   19.473580] ipw2200 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   19.473638] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   19.473680] ipw2200 0000:03:03.0: firmware: requesting ipw2200-bss.fw
[   19.747397] ipw2200: Unable to load ucode: -62
[   19.747419] ipw2200: Unable to load firmware: -62
[   19.747423] ipw2200: failed to register network device
[   20.072385] ipw2200 0000:03:03.0: PCI INT A disabled
[   20.072408] ipw2200: probe of 0000:03:03.0 failed with error -5
user@user-laptop:~$ 


---

### Post by chili555 on 2010-01-10
> ipw2200: Unable to load firmware: -62That's the problem. Please post:```
ls -al /lib/firmware | grep ipw
```We'll see if the firmware is there and readable.

---

### Post by stratcat250 on 2010-01-10
Ok, here it is;

> user@user-laptop:~$ ls -al /lib/firmware | grep ipw
-rw-r--r--  1 root root  209190 2009-11-10 05:21 ipw2100-1.3.fw
-rw-r--r--  1 root root  201138 2009-11-10 05:21 ipw2100-1.3-i.fw
-rw-r--r--  1 root root  196458 2009-11-10 05:21 ipw2100-1.3-p.fw
-rw-r--r--  1 root root  191154 2009-11-10 05:21 ipw2200-bss.fw
-rw-r--r--  1 root root  185428 2009-11-10 05:21 ipw2200-ibss.fw
-rw-r--r--  1 root root  187836 2009-11-10 05:21 ipw2200-sniffer.fw
user@user-laptop:~$

---

### Post by chili555 on 2010-01-10
I have two suggestions. First, please do:```
sudo apt-get install linux-backports-modules-karmic-generic
```It evidently contains a newer ipw2200 module. Next, let's unload and reload the newer module:```
sudo rmmod -f ipw2200
sudo modprobe ipw2200
```Any new wireless joy??

---

### Post by stratcat250 on 2010-01-10
No joy yet

> user@user-laptop:~$ sudo rmmod -f ipw2200
user@user-laptop:~$ sudo modprobe ipw2200
FATAL: Error inserting ipw2200 (/lib/modules/2.6.31-17-generic/updates/cw/ipw2200.ko): Unknown symbol in module, or unknown parameter (see dmesg)
user@user-laptop:~$ sudo modprobe ipw2200
FATAL: Error inserting ipw2200 (/lib/modules/2.6.31-17-generic/updates/cw/ipw2200.ko): Unknown symbol in module, or unknown parameter (see dmesg)


---

### Post by chili555 on 2010-01-10
> Unknown symbol in module, or unknown parameter (see dmesg) Does dmesg tell us anything new?```
dmesg | grep ipw
```I am running out of ammo.

---

### Post by stratcat250 on 2010-01-10
here is dmesg

> user@user-laptop:~$ dmesg |grep ipw 
[   19.387633] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   19.387638] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   19.473580] ipw2200 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   19.473638] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   19.473680] ipw2200 0000:03:03.0: firmware: requesting ipw2200-bss.fw
[   19.747397] ipw2200: Unable to load ucode: -62
[   19.747419] ipw2200: Unable to load firmware: -62
[   19.747423] ipw2200: failed to register network device
[   20.072385] ipw2200 0000:03:03.0: PCI INT A disabled
[   20.072408] ipw2200: probe of 0000:03:03.0 failed with error -5
[ 6425.155298] ipw2200: Unknown symbol libipw_change_mtu
[ 6425.155443] ipw2200: Unknown symbol libipw_rx_mgt
[ 6425.156428] ipw2200: Unknown symbol libipw_is_valid_channel
[ 6425.156996] ipw2200: Unknown symbol libipw_xmit
[ 6425.157351] ipw2200: Unknown symbol libipw_freq_to_channel
[ 6425.157494] ipw2200: Unknown symbol libipw_networks_age
[ 6425.158186] ipw2200: Unknown symbol libipw_get_geo
[ 6425.159070] ipw2200: Unknown symbol libipw_rx
[ 6425.159747] ipw2200: Unknown symbol libipw_wx_get_encodeext
[ 6425.159890] ipw2200: Unknown symbol libipw_wx_get_encode
[ 6425.160238] ipw2200: Unknown symbol libipw_wx_set_encode
[ 6425.160481] ipw2200: Unknown symbol libipw_txb_free
[ 6425.160787] ipw2200: disagrees about version of symbol free_ieee80211
[ 6425.160790] ipw2200: Unknown symbol free_ieee80211
[ 6425.161388] ipw2200: Unknown symbol libipw_channel_to_index
[ 6425.161540] ipw2200: Unknown symbol libipw_wx_set_encodeext
[ 6425.161831] ipw2200: Unknown symbol libipw_wx_get_scan
[ 6425.162055] ipw2200: Unknown symbol libipw_set_geo
[ 6425.162184] ipw2200: disagrees about version of symbol alloc_ieee80211
[ 6425.162187] ipw2200: Unknown symbol alloc_ieee80211
[ 6467.259434] ipw2200: Unknown symbol libipw_change_mtu
[ 6467.259581] ipw2200: Unknown symbol libipw_rx_mgt
[ 6467.260782] ipw2200: Unknown symbol libipw_is_valid_channel
[ 6467.266999] ipw2200: Unknown symbol libipw_xmit
[ 6467.267373] ipw2200: Unknown symbol libipw_freq_to_channel
[ 6467.267517] ipw2200: Unknown symbol libipw_networks_age
[ 6467.268263] ipw2200: Unknown symbol libipw_get_geo
[ 6467.269148] ipw2200: Unknown symbol libipw_rx
[ 6467.269826] ipw2200: Unknown symbol libipw_wx_get_encodeext
[ 6467.269969] ipw2200: Unknown symbol libipw_wx_get_encode
[ 6467.270302] ipw2200: Unknown symbol libipw_wx_set_encode
[ 6467.270545] ipw2200: Unknown symbol libipw_txb_free
[ 6467.270851] ipw2200: disagrees about version of symbol free_ieee80211
[ 6467.270854] ipw2200: Unknown symbol free_ieee80211
[ 6467.271452] ipw2200: Unknown symbol libipw_channel_to_index
[ 6467.271604] ipw2200: Unknown symbol libipw_wx_set_encodeext
[ 6467.271896] ipw2200: Unknown symbol libipw_wx_get_scan
[ 6467.272131] ipw2200: Unknown symbol libipw_set_geo
[ 6467.272261] ipw2200: disagrees about version of symbol alloc_ieee80211
[ 6467.272264] ipw2200: Unknown symbol alloc_ieee80211
user@user-laptop:~$ 


---

### Post by chili555 on 2010-01-10
Wow! I guess *backports* is not for us (although it works fine on my laptop, on which I am answering this post). Let's backtrack:```
sudo apt-get remove linux-backports-modules*
```Then can you try reinstalling your kernel as described here? [http://ubuntuforums.org/showthread.php?t=847055&page=2](http://ubuntuforums.org/showthread.php?t=847055&page=2)

Of course, you will try to reinstall your latest kernel, 2.6.31-17-generic, perhaps, after you boot into x-16.

I love when I search for a solution and run into myself!

---

### Post by stratcat250 on 2010-01-10
Here's the new dmesg;

> user@user-laptop:~$ dmesg | grep ipw
[   19.675214] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   19.675219] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   19.761524] ipw2200 0000:03:03.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   19.761576] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   19.761617] ipw2200 0000:03:03.0: firmware: requesting ipw2200-bss.fw
[   20.003147] ipw2200: Unable to load ucode: -62
[   20.003159] ipw2200: Unable to load firmware: -62
[   20.003163] ipw2200: failed to register network device
[   20.003934] ipw2200 0000:03:03.0: PCI INT A disabled
[   20.003951] ipw2200: probe of 0000:03:03.0 failed with error -5
user@user-laptop:~$ 














---

### Post by chili555 on 2010-01-11
So, we are just exactly where we started! Please confirm that you reinstalled your kernel as discussed. Second, please show us:```
lsmod | grep ipw
sudo su
echo 100 > /sys/class/firmware/timeout
exit
sudo rmmod -f ipw2200
sudo modprobe ipw2200
iwconfig
```Any wireless joy? If not, also post:```
dmesg | grep 03:03
```Thanks.

---

### Post by stratcat250 on 2010-01-11
yeehaa, I am replying to this thread via wireless!!!!!

Thank you very much chile555. You've been a great help. I never would have figured this out myself. :D


> user@user-laptop:~$ lsmod | grep ipw
ipw2200               140292  0 
libipw                 43148  1 ipw2200
lib80211                6432  2 ipw2200,libipw
user@user-laptop:~$ sudo su
[sudo] password for user: 
root@user-laptop:/home/user# echo 100 > /sys/class/firmware/timeout
root@user-laptop:/home/user# 
root@user-laptop:/home/user# exit
exit
user@user-laptop:~$ sudo rmmod -f ipw2200
user@user-laptop:~$ sudo modprobe ipw2200
user@user-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      unassociated  ESSID:off/any  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

second iwconfig;

eth2      IEEE 802.11g  ESSID:"BOBSNET"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 
00:1E:58:FB:EA:B3   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=95/100  Signal level=-31 dBm  Noise level=-89 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0




---

### Post by chili555 on 2010-01-11
Great! In order to make this permanent, you will need to edit */etc/rc.local* to add these three lines above 'exit 0'```
echo 100 > /sys/class/firmware/timeout
rmmod -f ipw2200
modprobe ipw2200
```Post back if you need additional guidance.

Have fun!

---

### Post by stratcat250 on 2010-01-11
> **chili555 said:**
> Great! In order to make this permanent, you will need to edit */etc/rc.local* to add these three lines above 'exit 0'```
echo 100 > /sys/class/firmware/timeout
rmmod -f ipw2200
modprobe ipw2200
```Post back if you need additional guidance.

Have fun!


Lines are added. If there is any problem I will surely post back. 
Thank you again. I thought it was toast when I couldn't get it running with either a previous kernel or running the Live Ubuntu. Now on to finishing the installation software.

---

### Post by zamolxis on 2010-12-09
2200BG is not showing up on my Maverick install either. But what I'd really like to know is if I could install the patched drivers..

---

### Post by SBFree on 2012-02-04
> **chili555 said:**
> That's the problem. Please post:```
ls -al /lib/firmware | grep ipw
```We'll see if the firmware is there and readable.

Hi:
I hope you can help with a similar problem. I am trying to get wireless working in BT5 and from my understanding it is drived from Ubuntu.

I get the the following:
root@bt:~# dmesg | grep ipw
[   11.048640] libipw: 802.11 data/management/control stack, git-1.1.13
[   11.048646] libipw: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   11.205325] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   11.205331] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   11.205475] ipw2200 0000:06:06.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   11.205511] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   11.500939] ipw2200: ipw2200-bss.fw request_firmware failed: Reason -2
[   11.500948] ipw2200: Unable to load firmware: -2
[   11.500953] ipw2200: failed to register network device
[   11.501003] ipw2200 0000:06:06.0: PCI INT A disabled
[   11.501062] ipw2200: probe of 0000:06:06.0 failed with error -5

Thanks in advance for any suggestions.
Scott

---

