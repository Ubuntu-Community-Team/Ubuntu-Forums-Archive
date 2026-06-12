---
title: "Wireless network disabled on lenovo laptop"
date: 2011-09-27
forum: Networking &amp; Wireless
---

### Post by watdafuk on 2011-09-27
I have Ubuntu 11.04 installed on a USB drive to test it out before I fully install it on my laptop. My laptop is a lenovo ideapad z570. And for some reason in I can't get my wireless card to work in Ubuntu. When I click on the network icon in the top right corner it says "Wireless card disabled by hardware switch" (or something similar) and where it says "enable wireless" that is grayed out and I can't click on it. It seems like Ubuntu thinks that the wireless switch on my laptop is switched to off, but it definitely is on.

My wireless usually works fine when i am in windows 7. The only thing is, usually after I booted from ubuntu or any other linux, when i boot back into windows, my wireless won't work. Windows will do the same thing and act like the wireless switch is turned off. So I have to press fn + f5 and it brings up this Lenovo wireless menu where I can turn it back on.

I followed the Ubuntu documentation for troubleshooting wireless and it didn't help. Here are the results from the commands from that page. (I was connected to a wired network on my laptop when I did these):

```

ubuntu@ubuntu:~$ nm-tool

NetworkManager Tool

State: connected

- Device: eth1  [Auto eth1] ----------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        F0:DE:F1:48:31:F4

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.68
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254


[B]- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlagn
  State:             unavailable
  Default:           no
  HW Address:        8C:A9:82:96:3C:A4[/B]

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


ubuntu@ubuntu:~$ sudo lshw -C network
[B]  *-network DISABLED      
       description: Wireless interface
       product: Centrino Wireless-N 1000[/B]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 8c:a9:82:96:3c:a4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-8-generic firmware=128.50.3.1 build 13488 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:43 memory:d0500000-d0501fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 05
       serial: f0:de:f1:48:31:f4
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.68 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:40 ioport:2000(size=256) memory:d0404000-d0404fff memory:d0400000-d0403fff

```I also found this thread: [http://ubuntuforums.org/showpost.php?p=5024425&postcount=1](http://ubuntuforums.org/showpost.php?p=5024425&postcount=1)
and here are the results of the commands from that thread:


```

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 05)
02:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)

ubuntu@ubuntu:~$ lsusb
Bus 002 Device 004: ID 0bda:0139 Realtek Semiconductor Corp. 
Bus 002 Device 003: ID 154b:0048 PNY 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 5986:0292 Acer, Inc 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

ubuntu@ubuntu:~$ lshw -class network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Wireless interface
       product: Centrino Wireless-N 1000
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 8c:a9:82:96:3c:a4
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-8-generic firmware=128.50.3.1 build 13488 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:43 memory:d0500000-d0501fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 05
       serial: f0:de:f1:48:31:f4
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.68 latency=0 multicast=yes port=MII speed=100Mbit/s
       resources: irq:40 ioport:2000(size=256) memory:d0404000-d0404fff memory:d0400000-d0403fff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

ubuntu@ubuntu:~$ uname -a
Linux ubuntu 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux

ubuntu@ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 11.04
Release:    11.04
Codename:    natty

ubuntu@ubuntu:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr f0:de:f1:48:31:f4  
          inet addr:192.168.1.68  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::f2de:f1ff:fe48:31f4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3489 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2787 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3637817 (3.6 MB)  TX bytes:405724 (405.7 KB)
          Interrupt:40 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

[B]wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on[/B]
          
ubuntu@ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth1
ubuntu@ubuntu:~$ ping -c 3 208.67.219.101
PING 208.67.219.101 (208.67.219.101) 56(84) bytes of data.

--- 208.67.219.101 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2016ms

ubuntu@ubuntu:~$ ping -c 3 www.opendns.com
PING www.opendns.com (208.69.38.150) 56(84) bytes of data.
64 bytes from 208.69.38.150: icmp_req=1 ttl=53 time=41.0 ms
64 bytes from 208.69.38.150: icmp_req=2 ttl=53 time=37.5 ms
64 bytes from 208.69.38.150: icmp_req=3 ttl=53 time=39.0 ms

--- www.opendns.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 12239ms
rtt min/avg/max/mdev = 37.529/39.228/41.069/1.466 ms

```I should also mention, I have this same problem with every other linux distro that I try now. But when I first tried Linux Mint wireless worked fine but now it doesn't, and when I first tried Ubuntu 10 it worked but now it doesn't.

Any ideas on what the problems is and how I can fix it?
Thanks.

---

### Post by chili555 on 2011-09-27
May we also see:```
rfkill list all
```Please see here: [http://www.zyxware.com/articles/1694/wireless-disabled-by-hardware-switch-issue-on-the-thinkpad-z570-in-ubuntu-solution](http://www.zyxware.com/articles/1694/wireless-disabled-by-hardware-switch-issue-on-the-thinkpad-z570-in-ubuntu-solution)

---

### Post by docbop on 2011-09-27
Have you confirmed the wifi on the Lenovo is On.  On my Toshiba it can be off, but still appears in lists of interfaces.  If on then have you tried...

ifconfig wlan0 up       -- turn up the interface
iwconfig                -- to check if its up

After that should be able to use the GUI tools to connect an access point and get IP.

---

### Post by praseodym on 2011-09-27
> ```
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=[COLOR="Red"]off[/COLOR]   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
```
Your card is "off". Switch, key, key combination? Check your BIOS settings if it can be activated there, maybe resetting the BIOS to manufacturer settings?!

Please show

```
rfkill list all       # < as already asked for
lsmod
```

---

### Post by watdafuk on 2011-09-27
Thanks. I followed the directions in the link from the first reply (chili555) and it worked!!! Thank you very much!

---

