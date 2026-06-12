---
title: "[SOLVED] Internet Intermitent"
date: 2008-12-08
forum: Networking &amp; Wireless
---

### Post by MGaddict2000 on 2008-12-08
I have a Gateway M275 tablet PC with Ubuntu 8.04. I'm new to ubuntu but have used other Linux and Unix OSes mildly. I had Ubuntu running pretty well on this laptop until I tried to do something which asked for root privileges and I ended screwing it up, so I decided to start from scratch, reformat, reinstall. That went well but now my internet is acting funny. It runs for a few seconds, or maybe a few minutes, then just stops, no errors, system still acts like its connected to the internet, but nothing will download unless I disconnect and reconnect the LAN cable. If I try using wireless, I have to disable and re enable the connection. If I just leave it for 5-10 minutes it will keep going but after 10 - 20 seconds just quits again. I noticed it immediately when I tried to do the updates after the install. I figured it was just the server I was downloading from but I've come to discover its the entire internet. I didn't have this problem before, I'm thinking I'll try reformatting and reinstalling again, but I'm trying to learn the intricacies of Linux and would rather fix it.

This thread is also listed in Hardware Laptops. I originally meant to put it here, but O well.

---

### Post by pytheas22 on 2008-12-08
The next time the connection drops, please immediately open a terminal and run the following commands:
```

lshw -C Network
lspci -nn
ifconfig
dmesg | tail -50
```

and post the output here.  That will provide some diagnostic information that we can use to troubleshoot the problem.

Also, does the connection only break when you're download a file at high speed or when you're using certain services (e.g. ftp or ssh), or can it happen just when you're browsing normal web pages?  And to be clear: it happens whether you're using wired or wireless, correct?

---

### Post by MGaddict2000 on 2008-12-09
Yes, it happens on wireless or LAN and even if I'm just using web sites. Here is the information you were asking for...... I know what ifconfig is, but what am I looking at on these other commands?

lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:bd:95:31
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=unassociated
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 83
       serial: 00:e0:b8:a7:24:68
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A ip=210.216.57.196 latency=66 maxlatency=56 mingnt=8 module=e100 multicast=yes

lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3580] (rev 02)
00:00.1 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3584] (rev 02)
00:00.3 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3585] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
00:02.1 Display controller [0380]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 83)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 03)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 03)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 03)
02:04.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG Network Connection [8086:4220] (rev 05)
02:05.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev ac)
02:05.1 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev ac)
02:05.2 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C552 IEEE 1394 Controller [1180:0552] (rev 04)
02:08.0 Ethernet controller [0200]: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller [8086:103d] (rev 83)

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:b8:a7:24:68  
          inet addr:210.216.57.196  Bcast:255.255.255.255  Mask:255.255.255.128
          inet6 addr: fe80::2e0:b8ff:fea7:2468/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1629 errors:0 dropped:0 overruns:0 frame:0
          TX packets:88 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:140944 (137.6 KB)  TX bytes:9446 (9.2 KB)

eth1      Link encap:Ethernet  HWaddr 00:12:f0:bd:95:31  
          inet6 addr: fe80::212:f0ff:febd:9531/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:201245 errors:0 dropped:0 overruns:0 frame:0
          TX packets:394799 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:10 Base address:0xa000 Memory:e0600000-e0600fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3603 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3603 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:182269 (177.9 KB)  TX bytes:182269 (177.9 KB)

dmesg |tail -50
[   29.919941] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a channels)
[   29.919991] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[   29.920010] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[   30.035678] cs: IO port probe 0x100-0x3af: clean.
[   30.037256] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   30.037933] cs: IO port probe 0x820-0x8ff: clean.
[   30.038494] cs: IO port probe 0xc00-0xcf7: clean.
[   30.071708] cs: IO port probe 0x100-0x3af: clean.
[   30.073282] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   30.073959] cs: IO port probe 0x820-0x8ff: clean.
[   30.074519] cs: IO port probe 0xc00-0xcf7: clean.
[   30.115193] cs: IO port probe 0xa00-0xaff: clean.
[   30.116443] cs: IO port probe 0xa00-0xaff: clean.
[   30.221251] intel8x0_measure_ac97_clock: measured 55294 usecs
[   30.221254] intel8x0: clocking to 48000
[   30.471272] lp: driver loaded but no devices found
[   30.667077] Adding 1646620k swap on /dev/sda5.  Priority:-1 extents:1 across:1646620k
[   31.120972] EXT3 FS on sda1, internal journal
[   32.035562] ip_tables: (C) 2000-2006 Netfilter Core Team
[   32.490219] ACPI: Error installing notify handler
[   32.490252] No dock devices found.
[   34.062601] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[   34.062606] apm: overridden by ACPI.
[   34.239885] ppdev: user-space parallel port driver
[   34.555968] audit(1228706387.821:2): type=1503 operation="inode_permission" requested_mask="a::" denied_mask="a::" name="/dev/tty" pid=4792 profile="/usr/sbin/cupsd" namespace="default"
[   98.512017] Marking TSC unstable due to: cpufreq changes.
[   50.913740] Bluetooth: Core ver 2.11
[   50.914455] NET: Registered protocol family 31
[   50.914460] Bluetooth: HCI device and connection manager initialized
[   50.914464] Bluetooth: HCI socket layer initialized
[   35.991785] Bluetooth: L2CAP ver 2.9
[   35.991790] Bluetooth: L2CAP socket layer initialized
[   36.045279] Bluetooth: RFCOMM socket layer initialized
[   36.045475] Bluetooth: RFCOMM TTY layer initialized
[   36.045478] Bluetooth: RFCOMM ver 1.8
[   38.513748] [drm] Initialized drm 1.1.0 20060810
[   38.517937] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[   38.517945] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   38.518012] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   38.518021] PCI: Setting latency timer of device 0000:00:02.1 to 64
[   38.518065] [drm] Initialized i915 1.6.0 20060119 on minor 1
[  123.872786] NET: Registered protocol family 10
[  123.873755] lo: Disabled Privacy Extensions
[  123.875123] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  137.890404] eth1: no IPv6 routers present
[ 6644.957250] sr0: CDROM not ready.  Make sure there is a disc in the drive.
[61201.667207] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[61201.671423] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[21593.280678] NET: Registered protocol family 17
[61211.657838] eth0: no IPv6 routers present

---

### Post by pytheas22 on 2008-12-09
> I know what ifconfig is, but what am I looking at on these other commands?

lspci, lshw and lsusb print information about your hardware.  dmesg prints messages from the kernel, which can be very useful for figuring out why something went wrong.

Unfortunately, however, I don't see anything in dmesg that sounds relevant to the crash.  You ran those commands after it had crashed, right?

When it crashes and you're using the ethernet, does it resolve the problem to type:
```

sudo rmmod e100
sudo modprobe e100
sudo ifconfig eth0 up
sudo dhclient eth0
```

Also, what happens if you reboot your computer, then run these commands:
```

sudo killall NetworkManager
sudo ifconfig eth0 up
sudo dhclient eth0
```

That should get you connected on the ethernet interface manually, instead of via Network Manager.  Do you still lose the connection if you connect this way?  I ask because it's possible that NM is causing the crash.

---

### Post by MGaddict2000 on 2008-12-10
The first set of code does seem to work like I unplugged and reconnected the ethernet cord. Its starts runnign again but only for a few more seconds. The second set of code doesn't seem to make a difference at all.

I'm not usre if I mentioned, to use ethernet, I'm using the exact same cable and port that my desktop is plugged into, just unplugging it and moving it over to the laptop. This eliminates the possibility that its a problem with the ISP or cable becuase the desktop functions fine.

---

### Post by pytheas22 on 2008-12-11
I tried to do some research on this but came up dry--I can't find anyone else whose connection crashes after a few minutes on your hardware.

Since you say that it happens with both wireless and wired, however, I'm still inclined to believe that it may be Network Manager's fault.  In that case, it may help to install wicd, which you can do by running these commands (you will need to be online for them to work, but it should only take a minute):
```

echo 'deb http://apt.wicd.net intrepid extras' | sudo tee -a /etc/apt/sources.list
wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install wicd
```

Then launch wicd from the Applications>Internet menu.  Do you have better luck connecting under wicd?

N.B.: wicd will uninstall Network Manager.  If you ever want NM back, type 'sudo apt-get install network-manager-gnome'.

Also, is it possible to take this computer to another location and connect to a different network?  I'm wondering if for some reason your strange behavior is caused by some obscure disagreement between your router and Ubuntu.

---

### Post by MGaddict2000 on 2008-12-13
Thank you so much. That seems to have worked perfectly. My internet is now running the way it should. Do You suppose if I reinstalled Network Manager, it might work? Could something have simply been currupt when it installed that would still allow it to run?

This is my first thread, how do I mark it as solved?

---

### Post by pytheas22 on 2008-12-13
> Thank you so much. That seems to have worked perfectly. My internet is now running the way it should. Do You suppose if I reinstalled Network Manager, it might work? Could something have simply been currupt when it installed that would still allow it to run?

Maybe, but it's hard to say really since there was nothing in the logs that pointed to the exact source of the problem--installing wicd as a solution was sort of just a lucky guess.  But it's easy enough to try NM again by typing:
```

sudo apt-get install network-manager-gnome
```

If it's still broken then and you want to go back to wicd, you just need to type:
```

sudo apt-get install wicd
```

I'm glad it's fixed.

---

