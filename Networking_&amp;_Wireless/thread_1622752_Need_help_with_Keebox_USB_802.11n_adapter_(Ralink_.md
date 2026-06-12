---
title: "Need help with Keebox USB 802.11n adapter (Ralink chipset)"
date: 2010-11-15
forum: Networking &amp; Wireless
---

### Post by abyssius on 2010-11-15
I bought a new Acer laptop which refuses to toggle its antenna on under Ubuntu so I gave up trying and I bought a Keebox Wireless N USB adapter, which uses the supposedly Linux-compatible Ralink rt2870 chipset - but I can't get it to work!. OS installed is Ubuntu 10.4.1 LTS

The device appears when lsusb is issued:
```

lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 1bcf:053e Sunplus Innovation Technology Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 002 Device 002: ID 0402:9665 ALi Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
**Bus 001 Device 003: ID 14b2:3c2c Ralink Technology, Corp.** 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I'm able to load the windows driver using ndiswrapper, which shows driver loaded and hardware present:
```

ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/options, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
rt2870 : driver installed
	device (14B2:3C2C) present

```

However, No wireless device, and dmesg shows the following error:

```

dmesg
[ 1167.938043] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[ 1168.068268] usb 1-3: reset high speed USB device using ehci_hcd and address 3
[ 1168.220355] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'MmGetSystemRoutineAddress'
[ 1168.220737] ndiswrapper (load_sys_files:206): couldn't prepare driver 'rt2870'
[ 1168.221880] ndiswrapper (load_wrap_driver:108): couldn't load driver rt2870; check system log for messages from 'loadndisdriver'
[ 1168.221951] usbcore: registered new interface driver ndiswrapper

```
 
lshw output:
```

lshw -C network
  *-network               
       description: Ethernet interface
       product: NetLink BCM57780 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 1c:75:08:00:f1:68
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=half firmware=sb latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:27 memory:d1100000-d110ffff
  *-network UNCLAIMED
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d1000000-d1003fff

```

ifconfig output:
```

ifconfig
eth0      Link encap:Ethernet  HWaddr 1c:75:08:00:f1:68  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

```

After I googled a little bit, I found a linux driver for the device from Ralink and I think I installed it correctly according to their instructions:

```

make
make -C tools
make[1]: Entering directory `/home/wherehouse/Downloads/wireless/3070/2010_0831_RT3070_Linux_STA_v2.3.0.0_DPO/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/wherehouse/Downloads/wireless/3070/2010_0831_RT3070_Linux_STA_v2.3.0.0_DPO/tools'
/home/wherehouse/Downloads/wireless/3070/2010_0831_RT3070_Linux_STA_v2.3.0.0_DPO/tools/bin2h
cp -f os/linux/Makefile.6 /home/wherehouse/Downloads/wireless/3070/2010_0831_RT3070_Linux_STA_v2.3.0.0_DPO/os/linux/Makefile
make -C /lib/modules/2.6.32-24-generic/build SUBDIRS=/home/wherehouse/Downloads/wireless/3070/2010_0831_RT3070_Linux_STA_v2.3.0.0_DPO/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic'
  CC [M]  /home/wherehouse/Downloads/wireless/3070/2010_0831_RT3070_Linux_STA_v2.3.0.0_DPO/os/linux/../../common/rtmp_mcu.o
  LD [M]  /home/wherehouse/Downloads/wireless/3070/2010_0831_RT3070_Linux_STA_v2.3.0.0_DPO/os/linux/rt3370sta.o
  Building modules, stage 2.
  MODPOST 1 modules
  LD [M]  /home/wherehouse/Downloads/wireless/3070/2010_0831_RT3070_Linux_STA_v2.3.0.0_DPO/os/linux/rt3370sta.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'
cp -f /home/wherehouse/Downloads/wireless/3070/2010_0831_RT3070_Linux_STA_v2.3.0.0_DPO/os/linux/rt3370sta.ko /tftpboot

```

I issued modprobe rt2870sta, then checked with lsmod;
```

lsmod
Module                  Size  Used by
**rt2870sta             461811  0 **
nls_utf8                1069  1 
isofs                  29250  1 
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_atihdmi     2367  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
etc...

```

It still doesn't work. I know I'm missing something, or some installation steps. but I don't know what to do next. I have another USB adapter, which I'm using to communicate right now. It works fine using ndiswrapper, but it sticks out too far and I'm afraid to break it off of my laptop. The new adapter is tiny and safer to use - except that I can't get it to ****ing work!

---

