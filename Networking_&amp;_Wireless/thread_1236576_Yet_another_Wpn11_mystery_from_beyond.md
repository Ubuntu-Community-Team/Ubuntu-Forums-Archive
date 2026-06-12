---
title: "Yet another Wpn11 mystery from beyond"
date: 2009-08-10
forum: Networking &amp; Wireless
---

### Post by sgelsot on 2009-08-10
Was working fine in  8.10 updated to 9.04 now . Have had problems in past installing but have followed more than one user guide and allways got it going. Not this time. The one thing I think I need to do is put the netgear "extracted" drivers  in the ndiswrapper location folder. Having problem's finding idiot guide. One more question which network manager should I be using? Ive tried a few. thanks Some output

@ubuntu-desktop:~$ dmesg | grep -e ndis -e wlan
[   13.307317] ndiswrapper version 1.53 loaded (smp=yes, preempt=no)
[   14.791755] ndiswrapper: driver netwpn11 (NETGEAR,09/26/2005,1.5.0.2102) loaded
[   14.793263] ndiswrapper (ZwQueryValueKey:2330): not fully implemented (yet)
[   29.897286] ndiswrapper (NdisWriteErrorLogEntry:190): log: C0001389, count: 4, return_address: f01cebbb
[   29.897293] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0xece7dc00
[   29.897297] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x28
[   29.897300] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0xf02a7000
[   29.897303] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0xf02a7000
[   29.897383] ndiswrapper (mp_init:219): couldn't initialize device: C0000001
[   29.897389] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
[   29.897403] ndiswrapper (mp_halt:262): device ee0e5500 is not initialized - not halting
[   29.897406] ndiswrapper: device eth%d removed
[   29.897422] ndiswrapper: probe of 1-6:1.0 failed with error -22
[   29.897453] usbcore: registered new interface driver ndiswrapper
[ 1073.349052] ndiswrapper (NdisWriteErrorLogEntry:190): log: C0001391, count: 4, return_address: f01cce8c
[ 1073.349058] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0xef3b0e00
[ 1073.349061] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x1
[ 1073.349064] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x0
[ 1073.349067] ndiswrapper (NdisWriteErrorLogEntry:193): code: 0x0
[ 1073.349070] ndiswrapper (mp_init:219): couldn't initialize device: C0000001
[ 1073.349075] ndiswrapper (pnp_start_device:435): Windows driver couldn't initialize the device (C0000001)
[ 1073.349083] ndiswrapper (mp_halt:262): device edaf5500 is not initialized - not halting
[ 1073.349086] ndiswrapper: device eth%d removed
[ 1073.349112] ndiswrapper: probe of 1-5:1.0 failed with error -22
@ubuntu-desktop:~$ $ iwconfig wlan0
bash: $: command not found
@ubuntu-desktop:~$ iwconfig wlan0
wlan0     No such device


and

@ubuntu-desktop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c504 Logitech, Inc. Cordless Mouse+Keyboard Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 1385:5f01 Netgear, Inc WPN111 (no firmware)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
@ubuntu-desktop:~$ 

and


@ubuntu-desktop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: c
       bus info: pci@0000:01:0c.0
       logical name: eth0
       version: 02
       serial: 00:0b:db:cd:0c:ec
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.21-k3-NAPI firmware=N/A ip=192.168.0.5 latency=64 mingnt=255 module=e1000 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 46:d9:ea:cb:4d:5a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

and

@ubuntu-desktop:~$ sudo iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.
and anything else needed 


If you got this far thank you.

---

### Post by RedSingularity on 2009-08-10
Have you tried WICD?  Thats what i use as a default on all my systems.  Personally i dont like the Gnome Network Manager.

---

### Post by sgelsot on 2009-08-13
As happens once again my wireless is working and I don't know why or how. I have installed and removed just about every network manager available(including Wicd) no I'm back to the basic applet that does't recongise my connection, in fact its say's I have no active connections. So to everyone having problems some times you just have to restart your computer and open up a browser . Thanks to to the forums and to the people who do know what their doing, up I don't have to come back.

---

