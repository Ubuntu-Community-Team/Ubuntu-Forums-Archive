---
title: "wireless dissappeared"
date: 2009-08-31
forum: Networking &amp; Wireless
---

### Post by sculleywr on 2009-08-31
I installed ubuntu 8.0.1 (I think) and updated to Jaunty Jackalope. Now, I purposely let the battery die to see if I could recalibrate it. Before I let it die, the wireless was detected on the display in the top toolbar next to the battery meter.

Here's the sitch:

Before it died, the computer was running VERY sluggishly (Facebook text boxes specifically presented a big problem, taking three or four times more time to enter the text as it took me to type it), but the wireless was working fine, after having installed madwifi.

Now, post battery death, the computer is running very smoothly, but the wireless has dissappeared from the toolbar button. It doesn't even have a spot for wireless connections.

I ran a few tests in the terminal from snippets here and there on my computer, but so far, I am no closer to having wireless. Hardware drivers show the madwifi driver is installed.

I have no windows partition as my computer got data-bombed by someone. The restore partition died as well as the main c: drive. I had no choice but to let ubuntu wipe the whole drive. I downloaded the driver onto a cd, but don't know how to get the driver install to run on linux. 

anyways, here are the results of the checks I ran on the terminal. I also ran two apt-gets (update and something to check for firmware). They ran but I am having no luck with it.

> billy@billy-laptop:~$ sudo # lspci -vv
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...
billy@billy-laptop:~$ sudo # ispci -vv
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...
billy@billy-laptop:~$ sudo #ispci -vv
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...
billy@billy-laptop:~$ sudo ispci -vv
sudo: ispci: command not found
billy@billy-laptop:~$ sudo hwinfo
sudo: hwinfo: command not found
billy@billy-laptop:~$ sudo update-pciids
Downloaded daily snapshot dated     2009-08-18 03:15:02
billy@billy-laptop:~$ lspci |grep Ethernet
00:0a.0 Ethernet controller: nVidia Corporation MCP77 Ethernet (rev a2)
07:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
billy@billy-laptop:~$ sudo ethtool eth0
Settings for eth0:
    Supported ports: [ MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 1
    Transceiver: external
    Auto-negotiation: on
    Supports Wake-on: g
    Wake-on: d
    Link detected: yes
billy@billy-laptop:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:72:6f:aa:25  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:72ff:fe6f:aa25/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11300 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7598 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14076006 (14.0 MB)  TX bytes:822951 (822.9 KB)
          Interrupt:253 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

billy@billy-laptop:~$ sudo cat /var/log/messages | grep switch
Aug 31 02:24:54 billy-laptop kernel: [    0.440039] ACPI: EC: non-query interrupt received, switching to interrupt mode
Aug 31 02:24:19 billy-laptop pulseaudio[3488]: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume.
Aug 31 20:32:40 billy-laptop kernel: [    0.440039] ACPI: EC: non-query interrupt received, switching to interrupt mode
Aug 31 20:33:36 billy-laptop pulseaudio[3292]: alsa-util.c: Cannot find fallback mixer control "Mic" or mixer control is no combination of switch/volume.
if anyone knows what is up, let me know.

Also, unrelated, there is a buzzing sound after sending im's on Pidgin, kind of underlaying the sending tone. Anyone know why this one tone does the buzzy sound?

---

### Post by jwrede on 2009-09-01
What do you get when you run the following?
```
iwconfig
sudo ifconfig
```

---

### Post by sculleywr on 2009-09-01
> billy@billy-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

billy@billy-laptop:~$ sudo ifconfig
[sudo] password for billy: 
eth0      Link encap:Ethernet  HWaddr 00:1d:72:6f:aa:25  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:72ff:fe6f:aa25/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:298989 errors:0 dropped:0 overruns:0 frame:0
          TX packets:173846 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:402602020 (402.6 MB)  TX bytes:13585934 (13.5 MB)
          Interrupt:253 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

billy@billy-laptop:~$ 

That is pretty much nonsense to me.

---

