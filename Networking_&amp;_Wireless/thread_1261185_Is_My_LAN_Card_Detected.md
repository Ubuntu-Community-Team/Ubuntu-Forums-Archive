---
title: "Is My LAN Card Detected ?"
date: 2009-09-08
forum: Networking &amp; Wireless
---

### Post by Dragon6 on 2009-09-08
Hi
I have ubuntu 8.10 installed on my laptop dell vostro 1510 which has Realtek RTL-8100C Ethernet LAN , I already used those commands to see the problem but still didn't know what the real problem is :
by the way , I'm using DHCP

harith@harith-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
06:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
08:05.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
08:05.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
08:05.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
harith@harith-laptop:~$ 

is my lan card detected ? however i don't think so coz i don't see anything about it , if it's not , can anyone help me how to resolve the problem ? because i can't connect to the internet through this LAN card . thanks

---

### Post by i.r.id10t on 2009-09-08
ifconfig -a

the lspci command you used just shows hardware on the bus, not whether or not it has support, etc. in the kernel for it.

---

### Post by Dragon6 on 2009-09-08
Thanks for responding ...
The result of ifconfig -a is as following :

harith@harith-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1f:e1:1b:37:c4  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:e1ff:fe1b:37c4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:100547 errors:0 dropped:0 overruns:0 frame:417993
          TX packets:117032 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:72644246 (72.6 MB)  TX bytes:42633866 (42.6 MB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:268 errors:0 dropped:0 overruns:0 frame:0
          TX packets:268 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:17008 (17.0 KB)  TX bytes:17008 (17.0 KB)

pan0      Link encap:Ethernet  HWaddr 26:5d:34:19:75:58  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

harith@harith-laptop:~$ 

By the way , i'm now using wireless connection , so i suppose that eth0 and its ip address is for the wireless card ..

---

### Post by Iowan on 2009-09-08
Another helpful command is **lshw -C network**

---

### Post by Dragon6 on 2009-09-08
the result of this command is as following :

harith@harith-laptop:~$ sudo lshw -C network
[sudo] password for harith: 
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:1f:e1:1b:37:c4
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl ip=192.168.0.100 latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 26:5d:34:19:75:58
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
harith@harith-laptop:~$ 

Thanks.

---

### Post by ductiletoaster on 2009-09-08
I know this isnt answer to you question however, when i upgraded from 7.04 to 8.10 i had alot of network problems. Even when i reinstalled i to did what u are doin and noticed that it seemed like my lan card was being detected. Now i do remb i found a work around but i dont remb what i did so i would recommend installing 9.04. In the end thats what i did. Sorry i couldnt be of much more help.

if you are set on keeping 8.10 then, though im not sure, i believe that my work around involved disabling the network manager. Ill look it up and post back if i find it

---

### Post by ductiletoaster on 2009-09-08
[http://ubuntuforums.org/showthread.php?t=527365](http://ubuntuforums.org/showthread.php?t=527365)

Try this thread. This sounds like what i did.... the last guy also has a point sense the manager will be removed u will have to manual enter etho. Also if ur not comfortable just removing it straight up then try disabling it first i think its mentioned in the first couple posts. Good luck -- or just switch to 9.04 lol

---

