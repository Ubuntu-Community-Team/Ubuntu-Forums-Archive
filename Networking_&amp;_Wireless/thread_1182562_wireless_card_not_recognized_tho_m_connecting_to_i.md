---
title: "wireless card not recognized tho m connecting to internet"
date: 2009-06-09
forum: Networking &amp; Wireless
---

### Post by mexxican on 2009-06-09
Hi , 

I seem to have a strange problem where I am able to connect to the internet and the driver seems to work fine but the wireless interface won't show up either in ettercap or wireshark when I run them as root.

I have a linksys WUSB54GC and am using patched drivers from aircrack-ng and the interface shows up in iwconfig as rausb0. The following output from iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

rausb0    RT73 WLAN  ESSID:"9RLM6"  
          Mode:Managed  Frequency=2.452 GHz  Access Point: 00:18:01:A9:DD:A8   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=89/100  Signal level:-34 dBm  Noise level:-143 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


```
It use to work fine earlier when I was using default drivers installed in ubuntu 9.04 and it used to show up as wlan0. But now when my aircrack-ng is working fine and I am able to inject, it fails to show up in ettercap or wireshark. I can go to system->Network Tools and select my wireless card rausb0 there as unknown device (rausb0). 

THe output from ifconfig
```

eth0      Link encap:Ethernet  HWaddr aa:00:04:00:0a:04  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:232 errors:0 dropped:0 overruns:0 frame:0
          TX packets:232 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9332 (9.3 KB)  TX bytes:9332 (9.3 KB)

rausb0    Link encap:Ethernet  HWaddr 00:21:29:dd:b0:e5  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:29ff:fedd:b0e5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24647 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6656 errors:0 dropped:22 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4862272 (4.8 MB)  TX bytes:831442 (831.4 KB)

```
ALso, I am using RTutilt as my network manager as it was mentioned in aircrack-ng web page. Another problem that I often seem to find is that this utility doesn't let me make a wired ethernet connection sometimes as obviously it is a wireless lan utility. WHat is the workaround for that? ALso, the output for lshw -C network is:
```

  *-network               
       description: Network controller
       product: BCM4328 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: aa:00:04:00:0a:04
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 latency=0 module=tg3 multicast=yes
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: rausb0
       serial: 00:21:29:dd:b0:e5
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.64 multicast=yes wireless=RT73 WLAN
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 12:a5:ba:cf:63:49
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```
THanks for the help in advance. THis is my first question here as I alwyas tried to sort things out myself. Also, I have just started using linux, so please pardon me iif this is just another senseless question.

MexX

---

### Post by mexxican on 2009-06-09
A small update to the problem: I tried to run ettercap from the command line and this is the error am getting

```


Listening on rausb0... 
ERROR : 16, Device or resource busy
[ec_capture.c:capture_init:146]

 pcap_open: Can't get USB bus index from rausb0


```

I am searching for a solution but if anyone can help, It'll be great !

Thanks

---

### Post by regala on 2009-06-09
> **mexxican said:**
> 
```


Listening on rausb0... 
ERROR : 16, Device or resource busy
[ec_capture.c:capture_init:146]

 pcap_open: Can't get USB bus index from rausb0


```

I am searching for a solution but if anyone can help, It'll be great !

Thanks

short explanation: a driver is a software written in C, that contains sets of functions or procedures, each related to the subsystems the driver need to support, here usb, nic and wifi. As your driver is "out-of-tree", I guess it is not completely ready and doesn't support fully and properly all is needed to be fully "integrated" in a Linux environment.

wait some time and try to update your driver as soon as some new versions are released. 

br, mathieu

---

### Post by mexxican on 2009-06-10
Hi, 

Thanks for the reply. I understand what you are trying to say but am sure there would be so many people using this card with aircrack patched drivers on Ubuntu and if anyone ever encountered this problem and if there was a workaround. 

Thanks

---

### Post by HunterThomson on 2009-06-29
I wrote this how to for installing the enhanced rt73 drivers.

[http://ubuntuforums.org/showthread.php?t=1178790](http://ubuntuforums.org/showthread.php?t=1178790)

It sounds like you need to install the rt73-k2wrlz-3.0.2 diver. What version do you have installed right now?

---

