---
title: "Wireless is really screwed up!!!"
date: 2009-09-28
forum: Networking &amp; Wireless
---

### Post by barnes334 on 2009-09-28
hey, so i tried to install the netbook remix for ubuntu (which i hated and can NOT remove) but somehow totally screwed up my wireless card
my network manager doesnt detect a wireless connection anymore
I need help badly
here is some information:

scotty@scotty:~$ sudo iwlist scanning
[sudo] password for scotty: 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

scotty@scotty:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth0 ----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        00:24:E8:95:2C:03

  Capabilities:
    Supported:       yes
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Settings

  IPv4 Settings:
    Address:         192.168.1.8
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


scotty@scotty:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

scotty@scotty:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:e8:95:2c:03  
          inet addr:192.168.1.8  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:e8ff:fe95:2c03/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9574 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9472 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9221278 (8.7 MB)  TX bytes:1762505 (1.6 MB)
          Interrupt:223 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2486 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2486 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:124300 (121.3 KB)  TX bytes:124300 (121.3 KB)

scotty@scotty:~$ lspci-nn
bash: lspci-nn: command not found
scotty@scotty:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation System Controller Hub (SCH Poulsbo) [8086:8100] (rev 07)
00:02.0 VGA compatible controller [0300]: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller [8086:8108] (rev 07)
00:1b.0 Audio device [0403]: Intel Corporation System Controller Hub (SCH Poulsbo) HD Audio Controller [8086:811b] (rev 07)
00:1c.0 PCI bridge [0604]: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 1 [8086:8110] (rev 07)
00:1c.1 PCI bridge [0604]: Intel Corporation System Controller Hub (SCH Poulsbo) PCI Express Port 2 [8086:8112] (rev 07)
00:1d.0 USB Controller [0c03]: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #1 [8086:8114] (rev 07)
00:1d.1 USB Controller [0c03]: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #2 [8086:8115] (rev 07)
00:1d.2 USB Controller [0c03]: Intel Corporation System Controller Hub (SCH Poulsbo) USB UHCI #3 [8086:8116] (rev 07)
00:1d.7 USB Controller [0c03]: Intel Corporation System Controller Hub (SCH Poulsbo) USB EHCI #1 [8086:8117] (rev 07)
00:1f.0 ISA bridge [0601]: Intel Corporation System Controller Hub (SCH Poulsbo) LPC Bridge [8086:8119] (rev 07)
00:1f.1 IDE interface [0101]: Intel Corporation System Controller Hub (SCH Poulsbo) IDE Controller [8086:811a] (rev 07)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
scotty@scotty:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 413c:02b0 Dell Computer Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 064e:a118 Suyin Corp. 
scotty@scotty:~$ uname-a
bash: uname-a: command not found
scotty@scotty:~$ uname -a
Linux scotty 2.6.24-24-lpia #1 SMP Wed May 6 17:43:36 UTC 2009 i686 GNU/Linux
scotty@scotty:~$ dmesg|grep ound
[    0.000000] found SMP MP-table at 000f7df0
[   10.864515] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   11.130457] No dock devices found.
[   11.224831] pnp: PnP ACPI: found 10 devices
[   12.632802] hub 1-0:1.0: USB hub found
[   12.735626] hub 2-0:1.0: USB hub found
[   12.839495] hub 3-0:1.0: USB hub found
[   15.336910] hub 4-0:1.0: USB hub found
[   16.490173] usb-storage: device found at 4
scotty@scotty:~$ dmesg|grep illswitch
scotty@scotty:~$

---

### Post by Iowan on 2009-09-29
Anything in */etc/network/interfaces* (besides the two "lo" configuration lines)?

---

