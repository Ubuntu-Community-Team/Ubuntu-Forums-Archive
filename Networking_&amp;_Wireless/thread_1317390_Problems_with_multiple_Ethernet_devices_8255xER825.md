---
title: "Problems with multiple Ethernet devices 8255xER/82551IT and 82546GB"
date: 2009-11-06
forum: Networking &amp; Wireless
---

### Post by robert77546 on 2009-11-06
Hi,

I have a problem with a single board computer with an external quad Ethernet card. The SBC natively has 4 Ethernet ports, they are all Intel 82546GB Gigabit contolers while the ones on the external PMC card are Intel 8255xER/82551IT Fast Ethernet Controller.

I can see the Gigabit devices but not the Fast ones.

Here is the lspci result:
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 6300ESB 64-bit PCI-X Bridge (rev 02)
00:1d.0 USB Controller: Intel Corporation 6300ESB USB Universal Host Controller (rev 02)
00:1d.1 USB Controller: Intel Corporation 6300ESB USB Universal Host Controller (rev 02)
00:1d.4 System peripheral: Intel Corporation 6300ESB Watchdog Timer (rev 02)
00:1d.5 PIC: Intel Corporation 6300ESB I/O Advanced Programmable Interrupt Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 0a)
00:1f.0 ISA bridge: Intel Corporation 6300ESB LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 6300ESB PATA Storage Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 6300ESB SMBus Controller (rev 02)
02:01.0 Ethernet controller: Intel Corporation 82546GB Gigabit Ethernet Controller (rev 03)
02:01.1 Ethernet controller: Intel Corporation 82546GB Gigabit Ethernet Controller (rev 03)
02:08.0 PCI bridge: Hint Corp HiNT HB4 PCI-PCI Bridge (PCI6150) (rev 04)
02:0c.0 PCI bridge: Hint Corp HB2 PCI-PCI Bridge (rev 04)
03:04.0 Ethernet controller: Intel Corporation 8255xER/82551IT Fast Ethernet Controller (rev 10)
03:05.0 Ethernet controller: Intel Corporation 8255xER/82551IT Fast Ethernet Controller (rev 10)
03:06.0 Ethernet controller: Intel Corporation 8255xER/82551IT Fast Ethernet Controller (rev 10)
03:07.0 Ethernet controller: Intel Corporation 8255xER/82551IT Fast Ethernet Controller (rev 10)
05:01.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)
05:02.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)


here is the ifconfig:eth0      Link encap:Ethernet  HWaddr 00:40:9e:00:9d:b2
          inet addr:172.21.9.136  Bcast:172.21.255.255  Mask:255.255.0.0
          inet6 addr: fe80::240:9eff:fe00:9db2/64 Scope:Link
          IPX/Ethernet 802.2 addr:00000001:00409E009DB2
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2460623 errors:0 dropped:0 overruns:0 frame:0
          TX packets:465826 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:231927919 (221.1 MiB)  TX bytes:283061287 (269.9 MiB)

eth2      Link encap:Ethernet  HWaddr 00:40:9e:00:9d:b0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth3      Link encap:Ethernet  HWaddr 00:40:9e:00:9d:b1
          IPX/Ethernet 802.2 addr:00409E009DB1
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:658488 errors:0 dropped:0 overruns:0 frame:0
          TX packets:658488 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:274844034 (262.1 MiB)  TX bytes:274844034 (262.1 MiB)

and finally the output from lshw -C network
  *-network:0
       description: Ethernet interface
       product: 82546GB Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 03
       serial: 00:40:9e:00:9d:b2
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k3-NAPI duplex=full firmware=N/A ip=172.21.9.136 latency=52 link=yes mingnt=255 module=e1000 multicast=yes port=twisted pair speed=100MB/s
  *-network:1 DISABLED
       description: Ethernet interface
       product: 82546GB Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 1.1
       bus info: pci@0000:02:01.1
       logical name: eth2_rename_ren
       version: 03
       serial: 00:40:9e:00:9d:b3
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k3-NAPI firmware=N/A latency=52 link=no mingnt=255 module=e1000 multicast=yes port=twisted pair
  *-network:0 DISABLED
       description: Ethernet interface
       product: 8255xER/82551IT Fast Ethernet Controller
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:03:04.0
       logical name: eth0_rename_ren
       version: 10
       serial: 00:10:73:01:40:f4
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI duplex=half firmware=N/A latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  *-network:1 DISABLED
       description: Ethernet interface
       product: 8255xER/82551IT Fast Ethernet Controller
       vendor: Intel Corporation
       physical id: 5
       bus info: pci@0000:03:05.0
       logical name: eth1
       version: 10
       serial: 00:10:73:01:40:f5
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  *-network:2 DISABLED
       description: Ethernet interface
       product: 8255xER/82551IT Fast Ethernet Controller
       vendor: Intel Corporation
       physical id: 6
       bus info: pci@0000:03:06.0
       logical name: eth4
       version: 10
       serial: 00:10:73:01:40:f6
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  *-network:3 DISABLED
       description: Ethernet interface
       product: 8255xER/82551IT Fast Ethernet Controller
       vendor: Intel Corporation
       physical id: 7
       bus info: pci@0000:03:07.0
       logical name: eth5
       version: 10
       serial: 00:10:73:01:40:f7
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k6-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  *-network:0
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:05:01.0
       logical name: eth2
       version: 02
       serial: 00:40:9e:00:9d:b0
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k3-NAPI firmware=N/A latency=52 link=no mingnt=255 module=e1000 multicast=yes port=twisted pair
  *-network:1
       description: Ethernet interface
       product: 82540EM Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:05:02.0
       logical name: eth3
       version: 02
       serial: 00:40:9e:00:9d:b1
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm pcix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000 driverversion=7.3.21-k3-NAPI firmware=N/A latency=52 link=no mingnt=255 module=e1000 multicast=yes port=twisted pair

and really finally from dmesg | grep e100
[    0.736362] pci 0000:03:04.0: Firmware left e100 interrupts enabled; disabling
[    0.736383] pci 0000:03:05.0: Firmware left e100 interrupts enabled; disabling
[    0.736399] pci 0000:03:06.0: Firmware left e100 interrupts enabled; disabling
[    0.736414] pci 0000:03:07.0: Firmware left e100 interrupts enabled; disabling
[    2.162142] e1000: 0000:02:01.0: e1000_probe: (PCI:66MHz:64-bit) 00:40:9e:00:9d:b2
[    2.210330] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k6-NAPI
[    2.210335] e100: Copyright(c) 1999-2006 Intel Corporation
[    2.236424] e100 0000:03:04.0: PME# disabled
[    2.236763] e100: eth0: e100_probe: addr 0xfe600000, irq 11, MAC addr 00:10:73:01:40:f4
[    2.262739] e100 0000:03:05.0: PME# disabled
[    2.263043] e100: eth1: e100_probe: addr 0xfe601000, irq 11, MAC addr 00:10:73:01:40:f5
[    2.289021] e100 0000:03:06.0: PME# disabled
[    2.289348] e100: eth2: e100_probe: addr 0xfe602000, irq 10, MAC addr 00:10:73:01:40:f6
[    2.315321] e100 0000:03:07.0: PME# disabled
[    2.315666] e100: eth3: e100_probe: addr 0xfe603000, irq 10, MAC addr 00:10:73:01:40:f7
[    2.349590] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[    2.602174] e1000: 0000:02:01.1: e1000_probe: (PCI:66MHz:64-bit) 00:40:9e:00:9d:b3
[    2.637571] e1000: eth2: e1000_probe: Intel(R) PRO/1000 Network Connection
[    2.637595] e1000 0000:05:01.0: found PCI INT A -> IRQ 11
[    2.889829] e1000: 0000:05:01.0: e1000_probe: (PCI:33MHz:32-bit) 00:40:9e:00:9d:b0
[    2.925624] e1000: eth3: e1000_probe: Intel(R) PRO/1000 Network Connection
[    3.177876] e1000: 0000:05:02.0: e1000_probe: (PCI:33MHz:32-bit) 00:40:9e:00:9d:b1
[    3.213686] e1000: eth6: e1000_probe: Intel(R) PRO/1000 Network Connection
[   73.439403] e1000: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
[697450.486325] e100 0000:03:06.0: firmware: requesting e100/d102e_ucode.bin
[697450.857962] e100: eth4: e100_request_firmware: Failed to load firmware "e100/d102e_ucode.bin": -2
[697668.166927] e100 0000:03:05.0: firmware: requesting e100/d102e_ucode.bin
[697668.178328] e100: eth1: e100_request_firmware: Failed to load firmware "e100/d102e_ucode.bin": -2
[697677.255250] e100 0000:03:05.0: firmware: requesting e100/d102e_ucode.bin
[697677.269736] e100: eth1: e100_request_firmware: Failed to load firmware "e100/d102e_ucode.bin": -2
[697743.163842] e100 0000:03:07.0: firmware: requesting e100/d102e_ucode.bin
[697743.178601] e100: eth5: e100_request_firmware: Failed to load firmware "e100/d102e_ucode.bin": -2


Any help or insight would be much appreciated.

I am trying to set up the Fast Ethernet devices to communicate with an old legacy system using IPX so any sample code for setting up IPX would also be appreciated.
 
Robert

---

### Post by chili555 on 2009-11-06
> firmware: requesting e100/[COLOR="Red"]d102e_ucode.bin[/COLOR]Is this in your system? Is it readable/writable by root? Find out with:```
ls -al /lib/firmware/`uname -r`/e100/
```May we also see:```
dmesg | grep -i eeprom
```Thanks.

---

### Post by robert77546 on 2009-11-10
thanks for the help! The output looks like:

ls -al /lib/firmware/`uname -r`/e100/
total 20
drwxr-xr-x  2 root root 4096 2009-09-01 08:27 .
drwxr-xr-x 17 root root 4096 2009-09-01 08:27 ..
-rw-r--r--  1 root root  539 2009-09-01 07:34 d101m_ucode.bin
-rw-r--r--  1 root root  539 2009-09-01 07:34 d101s_ucode.bin
-rw-r--r--  1 root root  539 2009-09-01 07:34 d102e_ucode.bin

and 

dmesg | grep -i eeprom 

is empty,

now what?

---

### Post by robert77546 on 2009-11-10
Chilli555,

Thanks for your help, I solved by making a link from/lib/fimware/`uname -r`/e100 to /lib/firmware/e100

The driver now loads correctly but when I bring it up ifconfig eth5 up I get the following 

[1040064.893226] handlers:
[1040064.893226] [<f8168bf2>] (e100_intr+0x0/0x8b [e100])
[1040065.524719] irq 10: nobody cared (try booting with the "irqpoll" option)
[1040065.525261] Pid: 0, comm: swapper Not tainted 2.6.29.6-rt23-rev03 #1
[1040065.525261] Call Trace:
[1040065.525261]  [<c0160917>] ? __report_bad_irq+0x24/0x69
[1040065.525261]  [<c016091e>] ? __report_bad_irq+0x2b/0x69
[1040065.525261]  [<c0160b58>] ? note_interrupt+0x1fc/0x24c
[1040065.525261]  [<c0161198>] ? handle_level_irq+0x95/0xc5
[1040065.525261]  [<c0104e63>] ? handle_irq+0x17/0x1b
[1040065.525261]  [<c0104883>] ? do_IRQ+0x38/0x76
[1040065.525261]  [<c0103589>] ? common_interrupt+0x29/0x30
[1040065.525261]  [<c02fd109>] ? __spin_unlock_irqrestore+0x10/0x17
[1040065.525261]  [<f823bc98>] ? smi_timeout+0x3c/0xb7 [ipmi_si]
[1040065.525261]  [<f823bc5c>] ? smi_timeout+0x0/0xb7 [ipmi_si]
[1040065.525261]  [<c0131b7d>] ? run_timer_softirq+0x14b/0x1dc
[1040065.525261]  [<f823bc5c>] ? smi_timeout+0x0/0xb7 [ipmi_si]
[1040065.525261]  [<c012ead3>] ? __do_softirq+0x85/0x123
[1040065.525261]  [<c012eb9f>] ? do_softirq+0x2e/0x38
[1040065.525261]  [<c012ebcf>] ? irq_exit+0x26/0x53
[1040065.525261]  [<c01048b0>] ? do_IRQ+0x65/0x76
[1040065.525261]  [<c0103589>] ? common_interrupt+0x29/0x30
[1040065.525261]  [<c0118ab8>] ? native_safe_halt+0x2/0x3
[1040065.525261]  [<c0108866>] ? default_idle+0x5f/0xa2
[1040065.525261]  [<c01021d2>] ? cpu_idle+0x46/0x6c
[1040065.525261]  [<c03f178e>] ? start_kernel+0x2cc/0x2cf
[1040065.525261] handlers:
[1040065.525261] [<f8168bf2>] (e100_intr+0x0/0x8b [e100])

This repeats and eventually the machine crashes.

Thanks for the help

---

### Post by chili555 on 2009-11-10
> irq 10: nobody cared (try booting with the "irqpoll" option)We could try this, but it may have other issues. We may not know until we try. Please do:```
sudo gedit /boot/grub/menu.lst
```Where you find the first, highest in the list, kernel listing, like this:

title           Ubuntu 9.10, kernel 2.6.31-14-generic
uuid            c2667fe5-c412-4d68-bbf0-43c81363d405
kernel          /boot/vmlinuz-2.6.31-14-generic root=UUID=c2667fe5-c412-4d68-bbf0-43c81363d405 ro quiet splash 
initrd          /boot/initrd.img-2.6.31-14-generic
quiet

You will edit it to add 'irqpoll' like this:

title           Ubuntu 9.10, kernel 2.6.31-14-generic
uuid            c2667fe5-c412-4d68-bbf0-43c81363d405
kernel          /boot/vmlinuz-2.6.31-14-generic root=UUID=c2667fe5-c412-4d68-bbf0-43c81363d405 ro [COLOR="Red"]irqpoll[/COLOR] quiet splash 
initrd          /boot/initrd.img-2.6.31-14-generic
quiet

Your uuid numbers and other details may differ. Proofread, save and close gedit. Reboot and check the logs after starting eth5. Please let us know.

---

