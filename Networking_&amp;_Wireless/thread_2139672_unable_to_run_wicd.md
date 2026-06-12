---
title: "unable to run wicd"
date: 2013-04-27
forum: Networking &amp; Wireless
---

### Post by icu12345 on 2013-04-27
So I have been struggling to replace the network manager in ubuntu 13.04  with wicd. I am new to ubuntu and I have been having some wireless  issues with my iwl3945 driver... Tried a lot of stuff but according to  most forum posts my issue is very likely to be resolved if I get wicd to  replace the network manager.

So here´s what´s going on. When I  install wicd I get the following error on startup: ```
Could not connect to  wicd's D-Bus interface. Check the wicd log for error messages.
``` I hit OK  and then I get another error message: ```
Error connecting to wicd service via D-Bus.Please ensure the wicd service is running.
``` I thought I would be able to start it manually with: ```
sudo service wicd start
```. As a result I got this: ```
* Starting Network connection manager wicd [fail]

```
So what can I do? I saw a similar thread where the following solution was proposed:
```

sudo dpkg-reconfigure wicd
sudo update-rc.d wicd defaults
```

However, all this brought was ubuntu starting with a completely frozen screen where nothing works - had to go to recovery mode to fix it. I´m with freshly installed completely stock ubuntu with unity 

Any ideas how to get it working? Any advice is very welcome and highly appreciated ;)

---

### Post by gordintoronto on 2013-04-27
Don't believe everything you read. You can solve your wireless problem without resorting to Wicd.

What wireless adapter? Have you ever set up a wireless connection in Ubuntu? The second time you do it is dead simple, but the first time can be a challenge.

---

### Post by icu12345 on 2013-04-28
[COLOR=#222222][FONT=Verdana]Thank you for your post. The wireless adapter is intel [/FONT][/COLOR]PRO/Wireless 3945ABG [Golan]. Here´s the output of lshw -C network:
```
icefire@Toshiba:~$ sudo lshw -C network
[sudo] password for icefire: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:5d:46:ab
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:44 ioport:4000(size=256) memory:d0010000-d0010fff memory:d0000000-d000ffff
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 00:1f:3c:ae:d0:ea
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=3.8.0-19-generic firmware=15.32.2.9 ip=192.168.1.20 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:46 memory:d4200000-d4200fff


```
[COLOR=#222222][FONT=Verdana]
The  problem is that wireless performance is not so good. I can connect to  any wireless network without difficulty but the transfer speed is way  worse than it should be. Testing on [speedtest.net]("http://speedtest.net")  I get about half of the speed I used to get with the same laptop in  windows environment (FYI the laptop had windows7 until last week and  used to connect to the very same wireless network). Moreover, when  copying files across the LAN the speed is also far from good - again,  about twice as slow as it used to be. As a result, playing a video file  that is stored on another computer or device on the network is  impossible.

I tried disabling hardware scan:
[/FONT][/COLOR]```

modprobe -r iwl3945 
modprobe iwl3945 disable_hw_scan=1
```[COLOR=#222222][FONT=Verdana]
 but this didn´t work so I didn´t bother making it permanent.
[/FONT][/COLOR]
Here´s what iwconfig outputs:
```
icefire@Toshiba:~$ iwconfig
wlan0     IEEE 802.11abg  ESSID:"dd-wrt"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:26:5A:B1:62:EE   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:6  Invalid misc:224   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.


```
and ifconfig:
```
icefire@Toshiba:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:33:5d:46:ab  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:554 errors:0 dropped:0 overruns:0 frame:0
          TX packets:554 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:63267 (63.2 KB)  TX bytes:63267 (63.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:ae:d0:ea  
          inet addr:192.168.1.20  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3cff:feae:d0ea/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9773 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6310 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10377083 (10.3 MB)  TX bytes:1143412 (1.1 MB)


```

So.. what do you think the problem might be? My goal is to get the wireless connection to work properly, with or without wicd... Please help...

---

### Post by nachwaal3ab on 2013-04-28
[COLOR=#000000]Don't believe everything you read. You can solve your wireless problem without resorting to Wicd.[/COLOR]

[COLOR=#000000]What wireless adapter? Have you ever set up a wireless connection in Ubuntu? The second time you do it is dead simple, but the first time can be a challenge.[/COLOR]

---

### Post by icu12345 on 2013-04-28
Could you please be more specific? Copying and pasting the same forum post isn't really helping me.. There is a wireless connection (see output of iwconfig in the first post).. What do you mean?

---

### Post by alcarola on 2013-12-03
See here: [http://askubuntu.com/questions/366531/wicd-network-manager-doesnt-work-in-13-10](http://askubuntu.com/questions/366531/wicd-network-manager-doesnt-work-in-13-10)

---

