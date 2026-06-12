---
title: "Wired Internet Connection Problem with Ubuntu Studio 10.04 on Inspiron 1545 Laptop"
date: 2010-08-24
forum: Networking &amp; Wireless
---

### Post by sightsoundsoul on 2010-08-24
I'm a complete beginner with Linux systems and really hoping to get away from Windows.
Ubuntu Studio 10.04 64-bit was preinstalled on my Inspiron 1545.

I cannot connect to the Internet at all.
In this thread, I hope to be able to find a solution for the wired connection.


I'm using the post below as a template to inquire for help with connecting to the Internet:
  [http://ubuntuforums.org/showpost.php?p=5024425&postcount=1](http://ubuntuforums.org/showpost.php?p=5024425&postcount=1)
   
  **Can't connect to internet?** 
         There are plenty of people who have this as their first question regarding Ubuntu? Why? It is a primary role for computers in the modern day.

Unfortunately, merely telling people that it doesn't work won't help them to resolve the issue. So - in the words of Tom Cruise, "Help me, help you."

This guide from aysiu is useful reading regarding getting generic help: [http://ubuntucat.wordpress.com/2007/...-linux-forums/]("http://ubuntucat.wordpress.com/2007/08/06/getting-the-best-help-on-linux-forums/")

For internet-related help, make sure you include the following details:

1. How were you trying to get online? e.g. dial-up, USB-wired ADSL modem, ethernet-wired ADSL modem, ethernet-wired ADSL modem-router, wireless router / modem-router, 3G-mobile internet etc.

  
   
  [COLOR=blue]Answer: I&#8217;m trying to get online through Ethernet-wired ADSL modem.[/COLOR]
   
   
  2. What hardware are you using? The brand & model number (perhaps with a link to an online manual) for your adapters, modems, routers etc. You can generally identify external components from their labelling, and internal components from within an Operating System already installed (e.g. Windows or Ubuntu).
  Code:
  lspci
lsusb
lshw -class network
   
  [SIZE=2][COLOR=blue]Answer (Output):[/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][lspci output][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)[/FONT][/COLOR][/SIZE][SIZE=2]

[/SIZE]      [SIZE=2][COLOR=blue][lsusb output][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]Bus 002 Device 002: ID 0513:0726 digital-X, Inc. [/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]Bus 001 Device 003: ID 0c45:63ee Microdia [/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT][/COLOR][/SIZE][SIZE=2]

[/SIZE]      [SIZE=2][COLOR=blue][lshw output][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]WARNING: you should run this program as super-user.[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]  *-network UNCLAIMED     [/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]       description: Network controller[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]       product: BCM4312 802.11b/g[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]       vendor: Broadcom Corporation[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]       physical id: 0[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]       bus info: pci@0000:0c:00.0[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]       version: 01[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]       width: 64 bits[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]       clock: 33MHz[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]       capabilities: bus_master cap_list[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]       configuration: latency=0[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]       resources: memory:f69fc000-f69fffff[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]  *-network[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]       description: Ethernet interface[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]       product: 88E8040 PCI-E Fast Ethernet Controller[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]       vendor: Marvell Technology Group Ltd.[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]       physical id: 0[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]       bus info: pci@0000:09:00.0[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]       logical name: eth0[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]       version: 13[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]       serial: a4:ba:db:b1:c5:0d[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]       width: 64 bits[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]       clock: 33MHz[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]       capabilities: bus_master cap_list ethernet physical[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]       configuration: broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A latency=0 multicast=yes[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]       resources: irq:29 memory:f68fc000-f68fffff ioport:de00(size=256)[/FONT][/COLOR][/SIZE]
   
   
  3. Who is your Internet Service Provider (and in which country)?
 
 
  [COLOR=blue]Answer: Cox is my Internet Service Provider. I live in the USA.[/COLOR]
   
  
4. Which version of Ubuntu are you using? e.g. Ubuntu 8.04, Xubuntu 7.10 etc and 32- vs 64-bit.
  Code:
  uname -a
lsb_release -a
   
  [SIZE=2][COLOR=Blue]Answer (Output):[/COLOR][/SIZE][SIZE=2][COLOR=Blue]
[/COLOR][/SIZE]   [SIZE=2][COLOR=Blue][uname output][/COLOR][/SIZE][SIZE=2][COLOR=Blue]
  Linux linuxlaptop 2.6.32-22-preempt #36-Ubuntu SMP PREEMPT Thu Jun 3 21:45:07 UTC 2010 x86_64 GNU/Linux

[/COLOR][/SIZE]       [SIZE=2][COLOR=Blue][lsb output][/COLOR][/SIZE][SIZE=2][COLOR=Blue]
[/COLOR][/SIZE]   [SIZE=2][COLOR=Blue][FONT=&quot]No LSB modules are available.[/FONT][/COLOR][/SIZE][SIZE=2][COLOR=Blue]
[/COLOR][/SIZE]   [SIZE=2][COLOR=Blue][FONT=&quot]Distributor ID:   Ubuntu[/FONT][/COLOR][/SIZE][SIZE=2][COLOR=Blue]
[/COLOR][/SIZE]   [SIZE=2][COLOR=Blue][FONT=&quot]Description:      Ubuntu 10.04 LTS[/FONT][/COLOR][/SIZE][SIZE=2][COLOR=Blue]
[/COLOR][/SIZE]   [SIZE=2][COLOR=Blue][FONT=&quot]Release:    10.04[/FONT][/COLOR][/SIZE][SIZE=2][COLOR=Blue]
[/COLOR][/SIZE]   [SIZE=2][COLOR=Blue][FONT=&quot]Codename:   lucid[/FONT][/COLOR][/SIZE]
   
  5. Can you get online with any other method? e.g. if you have a wifi problem, can you connect with ethernet?
  
  [COLOR=blue]Answer: No. I cannot connect with any method so far.[/COLOR]
   
  6. How are you getting online to post on this forum?
  
  [COLOR=blue]Answer: I use a separate Windows XP desktop computer to post on the forum.[/COLOR]
  
7. Include the **output** from the following commands from Terminal (all **case sensitive**). They help identify your hardware, so provide further detail to potential helpers. If necessary, just copy and paste the text into a text file and upload from a different computer.
  Code:
  ifconfig
iwconfig
route -n
ping -c 3 208.67.219.101
ping -c 3 [www.opendns.com]("http://www.opendns.com")
   
  [SIZE=2][COLOR=blue]Answer (Output):[/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][ifconfig output][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]eth0      Link encap:Ethernet  HWaddr a4:ba:db:b1:c5:0d  [/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]          UP BROADCAST MULTICAST  MTU:1500  Metric:1[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]          RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]          collisions:0 txqueuelen:1000 [/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]          Interrupt:18 [/FONT][/COLOR][/SIZE][SIZE=2]

[/SIZE]      [SIZE=2][COLOR=blue][FONT=&quot]eth0:avahi Link encap:Ethernet  HWaddr a4:ba:db:b1:c5:0d  [/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]          inet addr:169.254.8.217  Bcast:169.254.255.255  Mask:255.255.0.0[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]          UP BROADCAST MULTICAST  MTU:1500  Metric:1[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]          Interrupt:18 [/FONT][/COLOR][/SIZE][SIZE=2]

[/SIZE]      [SIZE=2][COLOR=blue][FONT=&quot]lo        Link encap:Local Loopback  [/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]          inet addr:127.0.0.1  Mask:255.0.0.0[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]          inet6 addr: ::1/128 Scope:Host[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]          UP LOOPBACK RUNNING  MTU:16436  Metric:1[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]          RX packets:12 errors:0 dropped:0 overruns:0 frame:0[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]          collisions:0 txqueuelen:0 [/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)[/FONT][/COLOR][/SIZE][SIZE=2]

[/SIZE]      [SIZE=2][COLOR=blue][iwconfig output][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]lo        no wireless extensions.[/FONT][/COLOR][/SIZE][SIZE=2]

[/SIZE]      [SIZE=2][COLOR=blue][FONT=&quot]eth0      no wireless extensions.[/FONT][/COLOR][/SIZE][SIZE=2]

[/SIZE]      [SIZE=2][COLOR=blue][route output][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]Kernel IP routing table[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]Destination     Gateway         Genmask         Flags Metric Ref    Use Iface[/FONT][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0[/FONT][/COLOR][/SIZE][SIZE=2]

[/SIZE]      [SIZE=2][COLOR=blue][ping &#8211;c 3 208.67.219.101][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]connect: Network is unreachable[/FONT][/COLOR][/SIZE][SIZE=2]

[/SIZE]      [SIZE=2][COLOR=blue][ping &#8211;c 3 [www.opendns.com]("http://www.opendns.com/")][/COLOR][/SIZE][SIZE=2]
[/SIZE]   [SIZE=2][COLOR=blue][FONT=&quot]ping: unknown host [www.opendns.com]("http://www.opendns.com")[/FONT][/COLOR][/SIZE]
   
  8. For wifi - what encryption are you using? Have you tried an open network? What wifi channel do you use?

[SIZE=2][COLOR=blue]Answer: N/A[/COLOR][/SIZE]
   
  9. Do you dual-boot with Windows?
   
  [COLOR=blue][FONT=&quot][SIZE=2]Answer: Nope.[/SIZE]
[SIZE=3][COLOR=Black]
So far, [/COLOR][/SIZE][/FONT][/COLOR][SIZE=3]**cchhrriiss121212 **[/SIZE][COLOR=blue][FONT=&quot][SIZE=3][COLOR=Black]tried to help me in this thread:
[http://ubuntuforums.org/showthread.php?p=9605407#post9605407](http://ubuntuforums.org/showthread.php?p=9605407#post9605407)
(Thanks, cchhrriiss121212.)

Please let me know if I need to provide more information. Thank you.[/COLOR][/SIZE]
[/FONT][/COLOR]

---

