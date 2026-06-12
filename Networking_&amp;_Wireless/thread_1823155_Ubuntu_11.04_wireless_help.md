---
title: "Ubuntu 11.04 wireless help"
date: 2011-08-11
forum: Networking &amp; Wireless
---

### Post by erych on 2011-08-11
I am running a dual boot dell laptop insperion 15** with windows 7 and Ubuntu 11.04. I am already aware of the problems with the dell wireless broadcom cards and have already done all the updates and driver install. It says that the driver is installed and active but I can not figure out how to scan for a wireless network. It has been over 5 years since I have used linux and I love the new feel but would really like to get my wireless working. Please any advice would be very helpful.

---

### Post by pytheas22 on 2011-08-11
In most cases Broadcom is actually not that bad these days.  The open-source drivers for it have come a long way over the last couple years.  If you could please open a terminal, run the following commands and post the output here, that should provide the precise information we'd need to know why it's not working for you:
```

lspci -nn
uname -rm
sudo iwlist scan
lshw -C Network
dmesg | grep -e bcm -e b43 -e ssb -e wlan
```

---

### Post by erych on 2011-08-11
eric@eric-Inspiron-1520:~$ lspci -nn 
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c) 
00:01.0 PCI bridge [0604]: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port [8086:2a01] (rev 0c) 
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02) 
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02) 
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02) 
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02) 
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02) 
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02) 
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 02) 
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02) 
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02) 
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02) 
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02) 
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2) 
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 02) 
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02) 
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 02) 
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02) 
01:00.0 VGA compatible controller [0300]: nVidia Corporation G86 [GeForce 8400M GS] [10de:0427] (rev a1) 
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02) 
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05) 
03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22) 
03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12) 
03:01.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12) 
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01) 
 
eric@eric-Inspiron-1520:~$ uname -rm 
2.6.38-10-generic i686 
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3][/SIZE][/FONT][/SIZE][/FONT]eric@eric-Inspiron-1520:~$ sudo iwlist scan 
[sudo] password for eric: 
lo Interface doesn't support scanning. 
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3][/SIZE][/FONT][/SIZE][/FONT]eth0 Interface doesn't support scanning. 
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3]&#12288;
[/SIZE][/FONT][/SIZE][/FONT]eric@eric-Inspiron-1520:~$ lshw -C Network 
WARNING: you should run this program as super-user. 
*-network 
description: Network controller 
product: BCM4311 802.11b/g WLAN 
vendor: Broadcom Corporation 
physical id: 0 
bus info: pci@0000:0c:00.0 
version: 01 
width: 32 bits 
clock: 33MHz 
capabilities: bus_master cap_list 
configuration: driver=b43-pci-bridge latency=0 
resources: irq:17 memory:f9ffc000-f9ffffff 
*-network 
description: Ethernet interface 
product: BCM4401-B0 100Base-TX 
vendor: Broadcom Corporation 
physical id: 0 
bus info: pci@0000:03:00.0 
logical name: eth0 
version: 02 
serial: 00:1c:23:9b:a6:ab 
size: 10Mbit/s 
capacity: 100Mbit/s 
width: 32 bits 
clock: 33MHz 
capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 multicast=yes port=twisted pair speed=10Mbit/s 
resources: irq:17 memory:f9bfe000-f9bfffff 
WARNING: output may be incomplete or inaccurate, you should run this program as super-user. 
[FONT=Calibri][SIZE=3][FONT=Calibri][SIZE=3][/SIZE][/FONT][/SIZE][/FONT]eric@eric-Inspiron-1520:~$ dmesg | grep -e bcm -e ssb -e wlan 
[ 19.864128] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243) 
[ 19.864146] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243) 
[ 19.864161] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243) 
[ 19.864177] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243) 
[ 19.969293] ssb: Sonics Silicon Backplane found on PCI device 0000:0c:00.0 
[ 20.040063] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243) 
[ 20.040074] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243) 
[ 20.040083] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243) 
[ 20.168707] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0 
[ 20.208424] b44 ssb1:0: eth0: Broadcom 44xx/47xx 10/100BaseT Ethernet 00:1c:23:9b:a6:ab

---

### Post by erych on 2011-08-11
sorry took so long to get back worked later then normal.

---

### Post by erych on 2011-08-11
just an update if anyone can help. I read a few threads on some of the other posts and tried these with no results.```
lspci -nn | grep 0280
```with the result of```
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

``````
sudo apt-get install b43-fwcutter firmware-b43-installer
```   with the result of completing upgrade reboot and still no wireless.

---

### Post by pytheas22 on 2011-08-12
hmmm, there's something strange going on there.  The b43 driver is claiming the device but doesn't seem to be bringing it up fully, as no wireless interface exists.  Yet dmesg doesn't seem to mention any errors regarding b43.

What output do you get from these commands (some of them may have no output, which is fine):
```

sudo rmmod b43
sudo rmmod ssb
sudo modprobe b43
dmesg | tail -50
iwconfig
ifconfig -a
```

---

### Post by erych on 2011-08-12
sudo rmmod b43  no result
sudo rmmod ssb ```
eric@eric-Inspiron-1520:~$ sudo rmmod ssb
ERROR: Module ssb is in use by b43,b44
```sudo modprobe b43 no result
dmesg | tail -50```
eric@eric-Inspiron-1520:~$ dmesg | tail -50
[ 3732.960455] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 3732.960461] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 3732.960468] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 3732.960474] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 3732.960482] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 3732.960488] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[ 3732.960495] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 3732.975965] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[ 3732.977121] Registered led device: b43-phy0::tx
[ 3732.977161] Registered led device: b43-phy0::rx
[ 3732.977203] Registered led device: b43-phy0::radio
[ 3732.977231] Broadcom 43xx driver loaded [ Features: PNL, Firmware-ID: FW13 ]
[ 3733.244074] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 3733.337472] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 4084.751641] b43-phy1: Broadcom 4311 WLAN found (core revision 10)
[ 4084.816195] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 4084.816200] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 4084.816204] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 4084.816208] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 4084.816212] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 4084.816216] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 4084.816219] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 4084.816223] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 4084.816227] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 4084.816231] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 4084.816234] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 4084.816238] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 4084.816241] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 4084.816245] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 4084.816249] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 4084.816253] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 4084.816256] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 4084.816260] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 4084.816263] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 4084.816267] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 4084.816270] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 4084.816274] cfg80211: 2402000 KHz - 2472000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 4084.816278] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 4084.816282] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 4084.816285] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 4084.816289] cfg80211: 2457000 KHz - 2482000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 4084.816292] cfg80211: Updating information on frequency 2484 MHz for a 20 MHz width channel with regulatory rule:
[ 4084.816296] cfg80211: 2474000 KHz - 2494000 KHz @  KHz), (300 mBi, 2000 mBm)
[ 4084.816510] ieee80211 phy1: Selected rate control algorithm 'minstrel_ht'
[ 4084.819093] Registered led device: b43-phy1::tx
[ 4084.819133] Registered led device: b43-phy1::rx
[ 4084.819176] Registered led device: b43-phy1::radio
[ 4084.819204] Broadcom 43xx driver loaded [ Features: PNL, Firmware-ID: FW13 ]
[ 4085.028073] b43-phy1: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 4085.104783] ADDRCONF(NETDEV_UP): wlan0: link is not ready
```iwconfig ```
eric@eric-Inspiron-1520:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```ifconfig -a ```
eric@eric-Inspiron-1520:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1c:23:9b:a6:ab  
          inet addr:70.112.106.198  Bcast:70.112.111.255  Mask:255.255.240.0
          inet6 addr: fe80::21c:23ff:fe9b:a6ab/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:100406 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24357 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:44199778 (44.1 MB)  TX bytes:2664014 (2.6 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:188 errors:0 dropped:0 overruns:0 frame:0
          TX packets:188 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13952 (13.9 KB)  TX bytes:13952 (13.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1d:d9:6c:57:1f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```looks like it sees my wireless card but it is not active

---

### Post by erych on 2011-08-12
not sure what those last codes you had me run did but my wireless is now working!! time for some much need sleep thank you for your help.:popcorn:

---

### Post by pytheas22 on 2011-08-12
Glad to hear that made it work.  Let me know if it works after a reboot as well; if not you may need to write a boot script to reinsert the b43 module automatically after you reboot.

---

### Post by erych on 2011-08-14
Sorry been really busy the last few days.  Didnt reboot my computer for awhile just did now and its not working again.  Not sure what to do going ot try those codes again just for now but would like to find a fix.  Thanks again

---

### Post by erych on 2011-08-14
So it seems like ```
dmesg | tail -50
``` is the code that is turning on the wireless card.

---

### Post by pytheas22 on 2011-08-14
dmesg only reports information; it doesn't change anything on your system.  So I doubt that command is the trick that's making it work.  I suspect instead that removing and reinserting the b43 and/or ssb modules is the solution, for whatever reason.

You can write a script to run these commands automatically whenever your computer boots, which will hopefully take care of the issue.  To do that, first type:

```
sudo gedit /etc/init.d/wireless-fix.sh
```

A blank text file will open.  Paste these lines into it:

```
rmmod b43
rmmod ssb
modprobe b43
```

Now save and close the file, and then run these commands to make it executable and run automatically at boot:
```

cd /etc/init.d
sudo chmod +x wireless-fix.sh
sudo update-rc.d wireless-fix.sh defaults
```

Now reboot and with any luck your wireless will work on its own.  Let me know if not.

---

### Post by nm_geo on 2011-08-14
[ 3732.977231] Broadcom 43xx driver loaded [ Features: PNL, Firmware-ID: FW13 ] 
[ 3733.244074] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)

Possible driver conflict? The command below might give us something too.

```
lsmod
```

---

### Post by pytheas22 on 2011-08-14
The output you posted is actually normal.  I don't see anything out of the ordinary there.  "lsmod" will list which modules are currently activated and I'm not sure that would be helpful just now.

Could you try running all the commands from post #6 again, but space them two minutes apart, and see after which command the wireless comes back on?  Leaving space between them will ensure that we know exactly which command it is that does the trick.  (For some of the commands it may take a little while after running them before they actually take effect; that's why a long interval of two minutes seems appropriate.)

---

