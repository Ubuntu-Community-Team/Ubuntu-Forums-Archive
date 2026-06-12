---
title: "HP Pavilion does not recognize wired ethernet connection"
date: 2009-02-17
forum: Networking &amp; Wireless
---

### Post by bronxbomberz41 on 2009-02-17
I just purchased an HP Pavilion dv7-1240us laptop.  It came with Vista but I wanted to wipe it clean and install ubuntu on it.  I have a Hardy Heron CD that I used to install from.  Install went fine but now the computer does not detect the ethernet connection.  The router and modem are working fine because the laptop I'm using now works.  Also, it doesn't recognize the wireless network either.  So i have no way of currently connecting to the internet.  Here is some output I have from the terminal

```
brian@brian-laptop:~$ lspci 
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge 
00:01.0 PCI bridge: Hewlett-Packard Company Unknown device 9602 
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0) 
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1) 
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2) 
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3) 
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] 
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller 
00:12.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller 
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller 
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller 
00:13.1 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI1 Controller 
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller 
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a) 
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller 
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia 
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller 
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge 
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 11h HyperTransport Configuration (rev 40) 
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h Address Map 
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 11h DRAM Controller 
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 11h Miscellaneous Control 
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 11h Link Control 
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics] 
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller 
08:00.0 System peripheral: JMicron Technologies, Inc. Unknown device 2382 
08:00.2 SD Host controller: JMicron Technologies, Inc. Unknown device 2381 
08:00.3 System peripheral: JMicron Technologies, Inc. Unknown device 2383 
08:00.4 System peripheral: JMicron Technologies, Inc. Unknown device 2384 
09:00.0 Network controller: Atheros Communications Inc. Unknown device 002a (rev 01) 
0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02) 
brian@brian-laptop:~$ lshw -class network 
WARNING: you should run this program as super-user. 
  *-network UNCLAIMED     
       description: Network controller 
       product: Atheros Communications Inc. 
       vendor: Atheros Communications Inc. 
       physical id: 0 
       bus info: pci@0000:09:00.0 
       version: 01 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list 
       configuration: latency=0 
  *-network 
       description: Ethernet interface 
       product: RTL8101E PCI Express Fast Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:0a:00.0 
       logical name: eth0 
       version: 02 
       serial: 00:1e:ec:fe:e6:1c 
       width: 64 bits 
       clock: 33MHz 
       capabilities: bus_master cap_list ethernet physical 
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=0 module=r8169 multicast=yes 
brian@brian-laptop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:1e:ec:fe:e6:1c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:718979772 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:219 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:2242 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:2242 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:117048 (114.3 KB)  TX bytes:117048 (114.3 KB) 

```

Thanks for your help...

---

### Post by bronxbomberz41 on 2009-02-20
Still haven't figured this one out yet!  I tried removing the RLT8169 drivers and installing the RLT8101E/8102E drivers for my network card but I can't seem to get the new driver to install.  I keep getting an error in the terminal.  Would love some help!!

---

### Post by ussndmac on 2009-02-20
I have a different chipset so I'm no help.

Just curious, I have a similar issue and suspect it is my older WAP that is the cause, since it is only 802.11b.

What sort of WAP are you using?

Mac

---

### Post by superprash2003 on 2009-02-20
your wired connection should work.. plug in the cable and in the terminal type **sudo dhclient eth0**

---

### Post by bronxbomberz41 on 2009-02-21
I ran that command in the terminal and this is the output i got.  I still don't have a wired connection.

```
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:1e:ec:fe:e6:1c
Sending on   LPF/eth0/00:1e:ec:fe:e6:1c
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

I'm really at a loss for words here because I've never seen this before.  I've installed Ubuntu on about 6 machines now and I've never had this problem.

---

### Post by bronxbomberz41 on 2009-02-21
> **ussndmac said:**
> I have a different chipset so I'm no help.

Just curious, I have a similar issue and suspect it is my older WAP that is the cause, since it is only 802.11b.

What sort of WAP are you using?

Mac


OK so I don't know exactly what WAP is...i'm bad with acronyms.  However the strangest thing happened.  I was getting fed up with ubuntu so i was going to try a couple other distros, debian and then fedora 10, and Deb didn't work either but then I had a connection when I booted the LiveCD for F10.  However I had a kernel failure when I tried to install and upon rebooting I got a Grub Error 15.  So I reinstalled Ubuntu again and you wouldn't believe it but my wired connection works.  I have no Idea why but it does.

Thanks for looking and trying to help though.

---

### Post by superprash2003 on 2009-02-22
you may need to disable ipv6 cause i think ubuntu is looking for an ipv6 address which you dont have!![http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html](http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html)

---

