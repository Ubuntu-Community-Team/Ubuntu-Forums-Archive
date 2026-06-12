---
title: "Unable to access Interent on Ubuntu 10.04"
date: 2012-12-13
forum: Networking &amp; Wireless
---

### Post by Sanju4 on 2012-12-13
Hello All, 

         I am a new user of Ubuntu. I am not able to connect to the internet on Ubuntu 10.04. I am connected to a LAN connection. I have 2 operating systems on my computer. One is WIndows XP and the other one is Ubuntu 10.04. I am able to connect to internet on Windows XP, However the same does not happen on Ubuntu. I have gone through some of the posts related to this on the forum and hence i would like to provide the following information. 

                                  
[LIST=1]
[*][COLOR=#000000][FONT=Liberation Serif][SIZE=3]**sudo     lshw -class network**[/SIZE][/FONT][/COLOR]
                   *-network[COLOR=#000000][FONT=Liberation Serif][SIZE=3]
description: Ethernet interface[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Liberation Serif][SIZE=3]
product: MCP73 Ethernet[/SIZE][/FONT][/COLOR]
[SIZE=3][FONT=Liberation Serif][/FONT][/SIZE]vendor: nVidia Corporation[COLOR=#000000][FONT=Liberation Serif][SIZE=3]
physical id: f [/SIZE][/FONT][/COLOR]                  [COLOR=#000000] [FONT=Liberation Serif][SIZE=3]                  bus info: pci@0000:00:0f.0 [/SIZE][/FONT][/COLOR]         [COLOR=#000000][FONT=Liberation Serif][SIZE=3]
logical name: eth0 [/SIZE][/FONT][/COLOR]
                            [COLOR=#000000] [FONT=Liberation Serif][SIZE=3]              version: a2 [/SIZE][/FONT][/COLOR]     
                         [COLOR=#000000][FONT=Liberation Serif][SIZE=3]serial: 00:22:68:62:5c:07 [/SIZE][/FONT][/COLOR]     
                             [COLOR=#000000] [FONT=Liberation Serif][SIZE=3]              size: 100MB/s [/SIZE][/FONT][/COLOR]     
                             [COLOR=#000000] [FONT=Liberation Serif][SIZE=3]              capacity: 100MB/s [/SIZE][/FONT][/COLOR]     
                             [COLOR=#000000] [FONT=Liberation Serif][SIZE=3]              width: 32 bits [/SIZE][/FONT][/COLOR]     
                             [COLOR=#000000] [FONT=Liberation Serif][SIZE=3]              clock: 66MHz [/SIZE][/FONT][/COLOR]     [COLOR=#000000][FONT=Liberation Serif][SIZE=3]
capabilities: pm msi bus_master cap_list ethernet physical      mii  10bt 10bt-fd 100bt                                      100bt-fd         autonegotiation [/SIZE][/FONT][/COLOR]                              [COLOR=#000000] [FONT=Liberation Serif][SIZE=3]              
configuration: autonegotiation=on broadcast=yes     driver=forcedeth                                                         driverversion=0.64 duplex=full latency=0 link=yes maxlatency=20                                                 mingnt=1 multicast=yes port=MII     speed=100MB/s [/SIZE][/FONT][/COLOR]     
                              [COLOR=#000000] [FONT=Liberation Serif][SIZE=3]              resources: irq:28 memory:efffd000-efffdfff ioport:f600(size=8)     memory:efffc000-                        efffc0ff memory:efffb000-efffb00f[/SIZE][/FONT][/COLOR]
[/LIST]
  
                          **[SIZE=3][FONT=Liberation Serif]2.   [/FONT][/SIZE]ifconfig**

       eth0                     Link encap:Ethernet  HWaddr 00:22:68:62:5c:07
[SIZE=3][FONT=Liberation Serif]               [/FONT][/SIZE]inet6 addr: fe80::222:68ff:fe62:5c07/64 Scope:Link
[SIZE=3][FONT=Liberation Serif]               [/FONT][/SIZE]UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
               [COLOR=#000000][FONT=Liberation Serif][SIZE=3]RX packets:111929 errors:0 dropped:0 overruns:0 frame:0 
               [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Liberation Serif][SIZE=3]TX packets:6 errors:0     dropped:0 overruns:0 carrier:0 
               [/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Liberation Serif][SIZE=3]collisions:0     txqueuelen:1000 [/SIZE][/FONT][/COLOR]     [COLOR=#000000][FONT=Liberation Serif][SIZE=3]
[SIZE=3]               [/SIZE]RX bytes:10051584     (10.0 MB)  TX bytes:492 (492.0 B) [/SIZE][/FONT][/COLOR]     [COLOR=#000000][FONT=Liberation Serif][SIZE=3]
[SIZE=3]               [/SIZE]Interrupt:28 Base     address:0xa000 [/SIZE][/FONT][/COLOR]     
[COLOR=#000000][FONT=Liberation Serif][SIZE=3]
[SIZE=3]      [/SIZE]lo                        Link             encap:Local Loopback[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Liberation Serif][SIZE=3]
[SIZE=3]          [/SIZE]inet addr:127.0.0.1      Mask:255.0.0.0 [/SIZE][/FONT][/COLOR]     [COLOR=#000000][FONT=Liberation Serif][SIZE=3]
[SIZE=3]          [/SIZE]inet6 addr: ::1/128     Scope:Host [/SIZE][/FONT][/COLOR]     [COLOR=#000000][FONT=Liberation Serif][SIZE=3]
[SIZE=3]          [/SIZE]UP LOOPBACK RUNNING      MTU:16436  Metric:1 [/SIZE][/FONT][/COLOR]     [COLOR=#000000][FONT=Liberation Serif][SIZE=3]
[SIZE=3]          [/SIZE]RX packets:84 errors:0     dropped:0 overruns:0 frame:0 [/SIZE][/FONT][/COLOR]     [COLOR=#000000][FONT=Liberation Serif][SIZE=3]
[SIZE=3]          [/SIZE]TX packets:84 errors:0     dropped:0 overruns:0 carrier:0 [/SIZE][/FONT][/COLOR]     [COLOR=#000000][FONT=Liberation Serif][SIZE=3]
[SIZE=3]          [/SIZE]collisions:0     txqueuelen:0 [/SIZE][/FONT][/COLOR]     [COLOR=#000000][FONT=Liberation Serif][SIZE=3]
[SIZE=3]          [/SIZE]RX bytes:6424 (6.4 KB)      TX bytes:6424 (6.4 KB) [/SIZE][/FONT][/COLOR]                             [COLOR=#000000][FONT=Liberation Serif][SIZE=3][B][SIZE=3]


3. [/SIZE]sudo     ifconfig eth0 _IPADDRESS_ netmask _[SIZE=3]MA[SIZE=3]SK[/SIZE][/SIZE]_ up ; ifconfig[/B][/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Liberation Serif][SIZE=3]

eth0          Link encap:Ethernet  HWaddr 00:22:68:62:5c:07[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Liberation Serif][SIZE=3]
        inet addr:172.18.5.67  Bcast:172.18.255.255  Mask:255.255.0.0[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Liberation Serif][SIZE=3]
        inet6 addr:     fe80::222:68ff:fe62:5c07/64 Scope:Link[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Liberation Serif][SIZE=3]
        UP BROADCAST RUNNING     MULTICAST  MTU:1500  Metric:1[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Liberation Serif][SIZE=3]
        RX packets:117589     errors:0 dropped:0 overruns:0 frame:0[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Liberation Serif][SIZE=3]
        TX packets:17 errors:0     dropped:0 overruns:0 carrier:0[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Liberation Serif][SIZE=3]
        collisions:0     txqueuelen:1000[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Liberation Serif][SIZE=3]
        RX bytes:10552130     (10.5 MB)  TX bytes:3263 (3.2 KB)[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Liberation Serif][SIZE=3]
        Interrupt:28 Base     address:0xa000[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Liberation Serif][SIZE=3]

lo        Link encap:Local Loopback[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Liberation Serif][SIZE=3]
    inet addr:127.0.0.1      Mask:255.0.0.0[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Liberation Serif][SIZE=3]
    inet6 addr: ::1/128     Scope:Host[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Liberation Serif][SIZE=3]
    UP LOOPBACK RUNNING      MTU:16436  Metric:1[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Liberation Serif][SIZE=3]
    RX packets:84 errors:0     dropped:0 overruns:0 frame:0[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Liberation Serif][SIZE=3]
    TX packets:84 errors:0     dropped:0 overruns:0 carrier:0[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Liberation Serif][SIZE=3]
    collisions:0     txqueuelen:0[/SIZE][/FONT][/COLOR][COLOR=#000000][FONT=Liberation Serif][SIZE=3]
    RX bytes:6424 (6.4 KB)      TX bytes:6424 (6.4 KB)

[SIZE=3][SIZE=3]I am still u[SIZE=3]nable to [SIZE=3]get [SIZE=3]connected to the internet. Any Hel[SIZE=3]p Appreciated. 

[SIZE=3]Regards

[SIZE=3]Sanju[/SIZE]
[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/FONT][/COLOR]

---

