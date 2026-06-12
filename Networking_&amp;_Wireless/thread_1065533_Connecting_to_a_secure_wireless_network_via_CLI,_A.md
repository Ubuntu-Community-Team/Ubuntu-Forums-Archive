---
title: "Connecting to a secure wireless network via CLI, ALMOST DONE PLEASE HELP!"
date: 2009-02-10
forum: Networking &amp; Wireless
---

### Post by philidox on 2009-02-10
After reading many forums and spending hours on the internet, I am almost complete with my quest to connect to a secure wireless network via cli.  Here is what I have done. 

First, I booted up ubuntu and before I even log in via GUI, I pressed **CTRL+ALT+F1**, to enter the command line prompt.  I entered my username and password like a good linux user.  I entered this command next, **lshw -c network**, and got the following

 *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0
       version: 10
       serial: 00:13:d3:af:42:3e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 9
       bus info: pci@0000:02:09.0
       logical name: eth1
       version: 05
       serial: 00:16:6f:b4:61:e6
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=192.168.1.66 latency=64 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 7a:8d:b7:2c:e4:c7
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

I did this to identify my wireless card logical name, which in my case is eth1.

Second, I entered **sudo ifconfig eth1 up**

Third, I entered **iwlist scanning** and got the following
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:1F:B3:57:19:89
                    ESSID:"ANGIE"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=89/100  Signal level=-40 dBm  
                    Extra: Last beacon: 668ms ago

pan0      Interface doesn't support scanning.

Note:The network I"m trying to connect to is called ANGIE

Lastly, I entered, **sudo iwconfig eth1 essid ANGIE key XXXX-XXXX-XX**
and then I get the error: **[   506.077310]  ipw2200: Failed to send SYSTEM_CONFIG: Already sending a command.**

Note:Were I have XXXX-XXXX-XX I have numbers for my wireless network
PLEASE HELP, what am I doing wrong I believe I am one step away.

---

### Post by kevdog on 2009-02-10
See the link in my signature about making a manual connection :)

---

