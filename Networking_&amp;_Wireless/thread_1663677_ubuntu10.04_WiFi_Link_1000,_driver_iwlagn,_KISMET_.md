---
title: "ubuntu10.04 WiFi Link 1000, driver iwlagn, KISMET DON'T WORK"
date: 2011-01-10
forum: Networking &amp; Wireless
---

### Post by georg.65 on 2011-01-10
Hello Ubuntu users,

I don't have much experience with ubuntu, have problem with kismet to work, here is my output:

sudo lshw -c network

  [PHP]*-network               
       description: Wireless interface
       product: WiFi Link 1000 Series
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:1e:64:22:b8:40
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes promiscuous=yes wireless=IEEE 802.11bgn
       resources: irq:30 memory:feafe000-feafffff
[/PHP]and here is my configuration from the /etc/kismet/kismet.conf

suiduser=georg
source=iwl4965, wlan0, Intel

when i start kismet this is the output
georg@georg-laptop:~$ sudo kismet

[PHP]Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 ( Intel): Enabling monitor mode for iwl4965 source interface  wlan0 channel 6...
FATAL: GetIFFlags: interface  wlan0: No such device
Done.[/PHP]Please help

---

### Post by chili555 on 2011-01-10
Just humor an old man who has been snowbound too long; please amend kismet.conf to show:```
source=iwl4965,wlan0,Intel
```That is, with no spaces in between item entries. Then run:```
ifconfig
```Is wlan0 up? Now do:```
sudo kismet
```Any improvement?

---

### Post by georg.65 on 2011-01-11
this is the output after modified the kismet.conf

georg@georg-laptop:~$ ifconfig

[PHP]eth0      Link encap:Ethernet  HWaddr 90:e6:ba:6a:b1:e7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:31 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2912 (2.9 KB)  TX bytes:2912 (2.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:64:22:b8:40  
          inet addr:192.168.2.116  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:64ff:fe22:b840/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1377 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:775236 (775.2 KB)  TX bytes:147510 (147.5 KB)[/PHP]georg@georg-laptop:~$ sudo ifconfig wlan0 down
georg@georg-laptop:~$ sudo iwconfig wlan0 mode monitor
georg@georg-laptop:~$ sudo ifconfig wlan0 up
georg@georg-laptop:~$ sudo kismet

[PHP]Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (Intel): Enabling monitor mode for iwl4965 source interface wlan0 channel 6...
Source 0 (Intel): Opening iwl4965 source interface wlan0...
Source 1 (addme): Opening none source interface none...
FATAL: Please configure at least one packet source.  Kismet will not function if no packet sources are defined in kismet.conf or on the command line.  Please read the README for more information about configuring Kismet.
WARNING: Error disabling monitor mode: Failed to set channel 0 22:Invalid argument
WARNING: Intel (wlan0) left in an unknown state.  You may need to manually
         restart or reconfigure it for normal operation.
WARNING: Sometimes cards don't always come out of monitor mode
         cleanly.  If your card is not fully working, you may need to
         restart or reconfigure it for normal operation.
Kismet exiting.
Done.[/PHP]what can be wrong now, thanks chili555

---

### Post by georg.65 on 2011-01-14
Anyone can't help me for bring KISMET to work

---

