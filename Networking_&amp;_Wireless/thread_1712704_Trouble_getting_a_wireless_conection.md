---
title: "Trouble getting a wireless conection"
date: 2011-03-23
forum: Networking &amp; Wireless
---

### Post by whimbrel on 2011-03-23
I installed Ubuntu 10.10(amd64) on a Toshiba-satellite-505D laptop. It works fine except the wireless can rarely connect (and wifi-radar tells me the signal is good).

The laptop has an RTL8187se wireless card and lsmod tells me the driver is an r8187se. When I do an ifconfig wlan0 shows up but 'rfkill list all' displays nothing and
'rfkill unblock all' doesn't help.

I also tried using ndiswrapper with the Windows driver I got from the Realtek site (ie, 8187SE_WindowsDriver_9109.1028.2009.zip etc.).
That didn't work either.

Thanks for any help. 
I've been stuck on this problem for a while.

Below is the output from some commands: 
```

dulcinea@dulcinea:~$ lshw  -c  network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: RTL8187SE Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 22
       serial: 00:26:b6:5d:1e:e2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=r8180 latency=0 multicast=yes wireless=802.11b/g
       resources: irq:16 ioport:7000(size=256) memory:d2100000-d2103fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:26:6c:33:38:0f
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
       resources: irq:43 ioport:6000(size=256) memory:d0010000-d0010fff memory:d0000000-d000ffff memory:d0020000-d003ffff
dulcinea@dulcinea:~$ 

```
```

dulcinea@dulcinea:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:6c:33:38:0f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:43 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:244 errors:0 dropped:0 overruns:0 frame:0
          TX packets:244 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18944 (18.9 KB)  TX bytes:18944 (18.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:26:b6:5d:1e:e2  
          inet6 addr: fe80::226:b6ff:fe5d:1ee2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:1 dropped:530 overruns:0 frame:0
          TX packets:2866 errors:3 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:177799 (177.7 KB)
Interrupt:16 Memory:ffffc900020a000ffffc900020a0100

```
```

dulcinea@dulcinea:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  ESSID:"2WIRE315"  
          Mode:Managed  Channel=162  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



root@dulcinea:~# ifconfig    wlan0   up
root@dulcinea:~# 

```

---

