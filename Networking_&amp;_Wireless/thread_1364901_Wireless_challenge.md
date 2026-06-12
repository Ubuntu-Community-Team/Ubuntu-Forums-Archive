---
title: "Wireless challenge"
date: 2009-12-26
forum: Networking &amp; Wireless
---

### Post by Reddoug on 2009-12-26
Hi



  I am having trouble getting my wireless connection to work. My laptop is setup for dual boot with Vista. I can get a wired connection. Tried using help in Unbutu. Some commands I used were; sudo lshw -C network   iwconfig and ifconfig. I turned off my security and still no connection. Wireless works in Vista. I copied the output from commands and will attach it. Do not get CLAIMED, UNCLAIMED, ENABLED OR DISABLED as stated in help. 

I will attached output.

  What is NDISWrapper?


doug@doug-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:5a:39:67:74  
          inet6 addr: fe80::223:5aff:fe39:6774/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:968 errors:0 dropped:0 overruns:0 frame:0
          TX packets:784 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:988106 (988.1 KB)  TX bytes:94830 (94.8 KB)
          Interrupt:29 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:24:2b:e2:6e:64  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-24-2B-E2-6E-64-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

doug@doug-laptop:~$ sudo lshw -C network
[sudo] password for doug: 
  *-network               
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: wmaster0
       version: 01
       serial: 00:24:2b:e2:6e:64
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:18 memory:d1100000-d110ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0a:00.0
       logical name: eth0
       version: 02
       serial: 00:23:5a:39:67:74
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:29 ioport:2000(size=256) memory:d1010000-d1010fff(prefetchable) memory:d1000000-d100ffff(prefetchable) memory:d1020000-d103ffff(prefetchable)
doug@doug-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

doug@doug-laptop:~$ 



Thanks, Doug

---

### Post by bkratz on 2009-12-26
You are using the AR928X  


description: Wireless interface
product: AR928X Wireless Network Adapter (PCI-Express)
vendor: Atheros Communications Inc.
physical id: 0
bus info: pci@0000:09:00.0
logical name: wmaster0
version: 01
serial: 00:24:2b:e2:6e:64
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=ath9k latency=0 multicast=yes wireless=IEEE 802.11abgn



with ath9k driver


See this thread, especially post 5

[http://ubuntuforums.org/showthread.php?t=1309605&highlight=AR928X](http://ubuntuforums.org/showthread.php?t=1309605&highlight=AR928X)


by the way ndiswrapper is used to allow use of windows drivers, no need.

---

### Post by Reddoug on 2009-12-27
Hi
I typed in echo ath9k | sudo tee -a /etc/modules and it came up with ath9k. I have not done much programming and I am unsure of the next step in step 5. Do I just type (linux-backports-modules-karmic and linux-backports-modules-wireless-karmic-generic) and hit enter?

Thanks, Doug

---

### Post by andlinux on 2009-12-28
> **Reddoug said:**
> Hi
I typed in echo ath9k | sudo tee -a /etc/modules and it came up with ath9k. I have not done much programming and I am unsure of the next step in step 5. Do I just type (linux-backports-modules-karmic and linux-backports-modules-wireless-karmic-generic) and hit enter?

Thanks, Doug
You just have to install them, you can do that with " sudo apt-get install linux-backports-modules-karmic" + "sudo apt-get install linux-backports-modules-wireless-karmic-generic". (that's for the console)

Or you can install it with Synaptic, that's maybe easier.

---

### Post by bryonak on 2009-12-28
One small hint: don't reboot. Turn off the computer completely, so the wlan adapter gets completely powered off.
A friend of mine with a WinXP/Ubuntu dual-boot can reliably reproduce this:
Booting Ubuntu or XP -> wireless works fine.
Rebooting from Ubuntu to XP -> wireless works fine.
Rebooting from XP to XP  or Ubuntu to Ubuntu -> wireless works fine.
Rebooting from XP to Ubuntu -> wireless doesn't work.
Possibly when restarting, Windows leaves the adapter in such a state that it's unusable by Ubuntu.

As for installing the modules... just open System -> Administration -> Synaptic and type "linux modules" into the search box, then chose the appropriate packages.

---

### Post by Reddoug on 2009-12-28
Hi 
   I installed package modules linux-backports-modules-karmic-generic and linux-backports-modules-wireless-karmic-generic. Both ver 2.6.31.16.29
When I iwconfig it says not associated with access point and I can not access any websites. I turned off my security on my DSL modem to see if that was the problem. I had tried to set it in network connections. What is the difference between karmic-generic and karmic-generic-pae?

Thanks, Doug

---

### Post by bkratz on 2009-12-28
googled and found this

[https://launchpad.net/ubuntu/karmic/+package/linux-backports-modules-wireless-karmic-generic-pae](https://launchpad.net/ubuntu/karmic/+package/linux-backports-modules-wireless-karmic-generic-pae)

It seems to make it so kernel updates don't cause problems (if I understand it correctly)


I don't understand the difference either, the other says the same thing!
[https://launchpad.net/ubuntu/karmic/i386/linux-backports-modules-karmic-generic](https://launchpad.net/ubuntu/karmic/i386/linux-backports-modules-karmic-generic)

---

### Post by Reddoug on 2010-01-03
Hi
Still can not get my wireless to work. How can I tell if the drivers are installed correctly? Wired works with no problem.

Thanks, Doug

---

