---
title: "upgraded to 9.10, wireless stopped working"
date: 2010-01-19
forum: Networking &amp; Wireless
---

### Post by B-80 on 2010-01-19
I upgraded from 9.04 to 9.10 a little bit ago, and ubuntu no longer recognized my D-link card, so I put in my encore ENLWI-N card which I had laying around. My card is now recognized, 
my lshw:
>       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:1f:d0:83:62:42
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:28 ioport:d000(size=256) memory:e9120000-e9120fff(prefetchable) memory:e9100000-e910ffff(prefetchable) memory:e9110000-e911ffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       product: RT2800 802.11n PCI
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: ra0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 latency=32 maxlatency=4 mingnt=2 multicast=yes wireless=RT2860 Wireless
       resources: irq:20 memory:e8000000-e800ffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes



but I don't see any wireless networks when I click on the network icon on the top panel.

any ideas here?

---

### Post by adam814 on 2010-01-19
Do you get any output from "iwlist ra0 scan" in the terminal?

---

### Post by B-80 on 2010-01-19
"ra0     No scan results"

---

### Post by adam814 on 2010-01-19
Maybe you have another interface for it?  Do any other wireless interfaces show up if you run "iwconfig"?

---

### Post by B-80 on 2010-01-19
> **adam814 said:**
> Maybe you have another interface for it?  Do any other wireless interfaces show up if you run "iwconfig"?

I'm really a noob here, running iwconfig gives me 4 results

lo -> no wireless extensions.

eth0 -> no wireless extensions.

ra0 -> whole bunch of stuff

vboxnet0 -> no wireless extensions.

---

### Post by adam814 on 2010-01-19
Ok, so "ra0" is your only wireless interface.  I'm not that familiar with RaLink wireless chipsets/drivers so I just wanted to check if it was one of the drivers that uses a raw interface as well.  It looks like it isn't.

Could you post the output of "dmesg"?  There might be a hint about what's going on there.

---

### Post by B-80 on 2010-01-19
> **adam814 said:**
> Ok, so "ra0" is your only wireless interface.  I'm not that familiar with RaLink wireless chipsets/drivers so I just wanted to check if it was one of the drivers that uses a raw interface as well.  It looks like it isn't.

Could you post the output of "dmesg"?  There might be a hint about what's going on there.

scanning through real quick, this seems to be the only part that has to do with the card
> [   44.317679] rt2860sta: module is from the staging directory, the quality is unknown, you have been warned.
[   44.319295]   alloc irq_desc for 20 on node -1
[   44.319297]   alloc kstat_irqs on node -1
[   44.319302] rt2860 0000:05:00.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   44.319350] 
[   44.319351] 
[   44.319351] === pAd = f8392000, size = 580808 ===
[   44.319351] 
[   44.319353] <-- RTMPAllocAdapterBlock, Status=0
[   44.353690]   alloc irq_desc for 22 on node -1
[   44.353692]   alloc kstat_irqs on node -1
[   44.353697] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   44.353718] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   44.409496] EXT3 FS on sdb5, internal journal
[   44.421556] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input6
[   44.638395] __ratelimit: 3 callbacks suppressed
[   44.638397] type=1505 audit(1263910825.375:13): operation="profile_replace" pid=1136 name=/usr/share/gdm/guest-session/Xsession
[   44.639347] type=1505 audit(1263910825.375:14): operation="profile_replace" pid=1137 name=/sbin/dhclient3
[   44.639770] type=1505 audit(1263910825.375:15): operation="profile_replace" pid=1137 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   44.640001] type=1505 audit(1263910825.375:16): operation="profile_replace" pid=1137 name=/usr/lib/connman/scripts/dhclient-script
[   44.642152] type=1505 audit(1263910825.379:17): operation="profile_replace" pid=1138 name=/usr/bin/evince
[   44.648914] type=1505 audit(1263910825.387:18): operation="profile_replace" pid=1138 name=/usr/bin/evince-previewer
[   44.652924] type=1505 audit(1263910825.391:19): operation="profile_replace" pid=1138 name=/usr/bin/evince-thumbnailer
[   44.658437] type=1505 audit(1263910825.395:20): operation="profile_replace" pid=1140 name=/usr/lib/cups/backend/cups-pdf
[   44.658931] type=1505 audit(1263910825.395:21): operation="profile_replace" pid=1140 name=/usr/sbin/cupsd
[   44.660316] type=1505 audit(1263910825.399:22): operation="profile_replace" pid=1141 name=/usr/sbin/mysqld-akonadi
[   44.831817] r8169: eth0: link down
[   44.831934] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   45.831392] NICLoadFirmware: MCU is not ready
[   45.831394] 
[   45.831395] 
[   45.831396] ERROR!!! NICLoadFirmware failed, Status[=0x00000001]
[   45.831403] !!! RT2860 Initialized fail !!!
[   47.237207] NICLoadFirmware: MCU is not ready
[   47.237208] 
[   47.237209] 
[   47.237210] ERROR!!! NICLoadFirmware failed, Status[=0x00000001]
[   47.237218] !!! RT2860 Initialized fail !!!



I can post the whole thing if youd like

thanks a bunch for the help btw

---

### Post by hsartoris on 2010-01-19
I'm running 9.10 and having something of the same problem. When I run iwlist scan, it just says 'interface doesn't support scanning'. No proprietary drivers are showig up in hardware drivers, and i can't get any wireless networks. Please help!

---

### Post by bkratz on 2010-01-19
> **hsartoris said:**
> I'm running 9.10 and having something of the same problem. When I run iwlist scan, it just says 'interface doesn't support scanning'. No proprietary drivers are showig up in hardware drivers, and i can't get any wireless networks. Please help!

You really should start a new thread and post the output of lspci (that is LSPCI in lowercase) as a starting point.

---

### Post by adam814 on 2010-01-19
That clarifies the problem a bit more.  You're using (likely unintentionally) a driver from staging.  This means it hasn't been tested enough to be in the stable kernel.   Also it's unable to load firmware for your chipset.  Without the firmware it definitely won't work.

Let's see if it's failing to load because the firmware file is missing or if it's another reason.  Type this in a terminal to see if the file is there:
```
find /lib/firmware -name rt2860.bin
```
If not try installing the "linux-firmware" and "linux-firmware-nonfree" packages.

---

### Post by B-80 on 2010-01-19
yeah, it's there. I am unable to connect a harline, so I cant download any packages.

---

### Post by adam814 on 2010-01-19
Well, if it's there you probably don't need to worry about installing those packages (although you could always download the .debs from packages.ubuntu.com on the machine you're posting from and transfer with a USB drive).

You might give this a try to see if it helps:
[http://ubuntuforums.org/showthread.php?t=1045703](http://ubuntuforums.org/showthread.php?t=1045703)

---

### Post by B-80 on 2010-01-19
getting an error when I try to make that file in the link, same with the .deb
> DKMS make.log for rt2860-1.8.0.0 for kernel 2.6.31-17-generic (i686)
Tue Jan 19 18:33:40 EST 2010
make -C tools
make[1]: Entering directory `/var/lib/dkms/rt2860/1.8.0.0/build/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/var/lib/dkms/rt2860/1.8.0.0/build/tools'
/var/lib/dkms/rt2860/1.8.0.0/build/tools/bin2h
cp -f os/linux/Makefile.6 /var/lib/dkms/rt2860/1.8.0.0/build/os/linux/Makefile
make  -C  /lib/modules/2.6.31-17-generic/build SUBDIRS=/var/lib/dkms/rt2860/1.8.0.0/build/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-17-generic'
  CC [M]  /var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../common/md5.o
  CC [M]  /var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../common/mlme.o
/var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../common/mlme.c: In function &#8216;BssTableSortByRssi&#8217;:
/var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../common/mlme.c:4261: warning: the frame size of 1572 bytes is larger than 1024 bytes
  CC [M]  /var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../common/rtmp_wep.o
  CC [M]  /var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../common/action.o
  CC [M]  /var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../common/cmm_data.o
/var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../common/cmm_data.c: In function &#8216;RTMP_FillTxBlkInfo&#8217;:
/var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../common/cmm_data.c:947: warning: label &#8216;FillTxBlkErr&#8217; defined but not used
  CC [M]  /var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../common/rtmp_init.o
  CC [M]  /var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../common/rtmp_tkip.o
  CC [M]  /var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../common/cmm_sync.o
  CC [M]  /var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../common/eeprom.o
  CC [M]  /var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../common/cmm_sanity.o
  CC [M]  /var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../common/cmm_info.o
  CC [M]  /var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../common/cmm_wpa.o
/var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../common/cmm_wpa.c: In function &#8216;AES_GTK_KEY_WRAP&#8217;:
/var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../common/cmm_wpa.c:798: warning: the frame size of 1092 bytes is larger than 1024 bytes
  CC [M]  /var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../common/dfs.o
  CC [M]  /var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../common/spectrum.o
  CC [M]  /var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../sta/assoc.o
  CC [M]  /var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../sta/aironet.o
  CC [M]  /var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../sta/auth.o
  CC [M]  /var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../sta/auth_rsp.o
  CC [M]  /var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../sta/sync.o
/var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../sta/sync.c: In function &#8216;PeerBeacon&#8217;:
/var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../sta/sync.c:1303: warning: unused variable &#8216;ByteValue&#8217;
/var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../sta/sync.c:1601: warning: the frame size of 1320 bytes is larger than 1024 bytes
/var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../sta/sync.c: In function &#8216;PeerBeaconAtJoinAction&#8217;:
/var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../sta/sync.c:983: warning: the frame size of 1252 bytes is larger than 1024 bytes
/var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../sta/sync.c: In function &#8216;PeerBeaconAtScanAction&#8217;:
/var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../sta/sync.c:724: warning: the frame size of 1256 bytes is larger than 1024 bytes
/var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../sta/sync.c: In function &#8216;MlmeStartReqAction&#8217;:
/var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../sta/sync.c:584: warning: the frame size of 1064 bytes is larger than 1024 bytes
  CC [M]  /var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../sta/sanity.o
  CC [M]  /var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../sta/rtmp_data.o
  CC [M]  /var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../sta/connect.o
/var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../sta/connect.c: In function &#8216;CntlOidScanProc&#8217;:
/var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../sta/connect.c:321: warning: the frame size of 1600 bytes is larger than 1024 bytes
  CC [M]  /var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../sta/wpa.o
/var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../sta/wpa.c: In function &#8216;CCKMPRF&#8217;:
/var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../sta/wpa.c:1838: warning: the frame size of 1044 bytes is larger than 1024 bytes
  CC [M]  /var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../os/linux/rt_linux.o
/var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../os/linux/rt_linux.c: In function &#8216;send_monitor_packets&#8217;:
/var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../os/linux/rt_linux.c:1002: warning: the frame size of 1084 bytes is larger than 1024 bytes
  CC [M]  /var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../os/linux/rt_profile.o
/var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../os/linux/rt_profile.c: In function &#8216;RTMPReadParametersHook&#8217;:
/var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../os/linux/rt_profile.c:928: error: &#8216;struct task_struct&#8217; has no member named &#8216;fsuid&#8217;
/var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../os/linux/rt_profile.c:929: error: &#8216;struct task_struct&#8217; has no member named &#8216;fsgid&#8217;
/var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../os/linux/rt_profile.c:930: error: &#8216;struct task_struct&#8217; has no member named &#8216;fsuid&#8217;
/var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../os/linux/rt_profile.c:930: error: &#8216;struct task_struct&#8217; has no member named &#8216;fsgid&#8217;
/var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../os/linux/rt_profile.c:1554: error: &#8216;struct task_struct&#8217; has no member named &#8216;fsuid&#8217;
/var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../os/linux/rt_profile.c:1555: error: &#8216;struct task_struct&#8217; has no member named &#8216;fsgid&#8217;
make[2]: *** [/var/lib/dkms/rt2860/1.8.0.0/build/os/linux/../../os/linux/rt_profile.o] Error 1
make[1]: *** [_module_/var/lib/dkms/rt2860/1.8.0.0/build/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-17-generic'
make: *** [LINUX] Error 2


---

### Post by B-80 on 2010-01-19
well, just as a follow up. I tried putting my old card back in and using ndiswrapper. Didn't work. put the ENLWI-N back in, loaded up and it worked... I restarted a thousand times with this card in. I guess my advice to anyone having the problem is to boot up w/o the card in and the shut down properly and boot back in.
Also I installed Wicd and removed network manager...

Hope this helps anyone who has the same problem, and I hope this doesn't stop working tomorrow or something

---

