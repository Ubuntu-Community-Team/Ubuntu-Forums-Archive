---
title: "my wireless connection is not working, please help!"
date: 2009-05-31
forum: Networking &amp; Wireless
---

### Post by unknown23 on 2009-05-31
hello,

first i just like to say, i am completely new to linux. I have no experience using this OS. I am just not ever going to use windows again, so i would like to learn how to use linux.

so, i installed xubuntu 9.04, i am having a problem connecting to the wireless network that is available.

in the hardware devices, it says that my Broadcom B43 wireless is activated and currently in use.

in the top right corner there is the icon that shows my wireless connection, it says i am connected, yet there is 0 per cent signal strength.

is there a way i can get this to run properly?

is there some codes i can copy and paste in the terminal to get this to work properly.

i really need the help, i have to be online wirelessy in order to work.

please help

---

### Post by unknown23 on 2009-05-31
shadowcast@shadowcast-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:75:80:ef
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.199.105 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@0000:02:06.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:b7:0c:b3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=10.42.43.1 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 02:2f:19:98:1d:4a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
shadowcast@shadowcast-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"k9-freipunk.net"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: 5A:B3:52:B8:D9:7D   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

shadowcast@shadowcast-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:75:80:ef  
          inet addr:192.168.199.105  Bcast:192.168.199.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fe75:80ef/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9174 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9530 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10251731 (10.2 MB)  TX bytes:1357170 (1.3 MB)
          Interrupt:16 Base address:0x3000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:48 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3360 (3.3 KB)  TX bytes:3360 (3.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:90:4b:b7:0c:b3  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::290:4bff:feb7:cb3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:3659 (3.6 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-90-4B-B7-0C-B3-63-62-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

shadowcast@shadowcast-laptop:~$

---

### Post by Adampell on 2009-05-31
Dont mean to intrude on this thread, but im having the exact same problem as above. Using the latest Ubuntu.

This problem persists using the Live CD and while using Wubi.

---

### Post by Ayuthia on 2009-05-31
> **unknown23 said:**
> 
wlan0     IEEE 802.11bg  ESSID:"k9-freipunk.net"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: 5A:B3:52:B8:D9:7D   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Are you trying to connect via ad-hoc?  This is probably not the correct technical way of saying it, but it looks like you are trying to use your wireless connection to share the internet or else you are trying to connect to another computer (instead of a router).

If that is not the case, can you try the following:
```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode Managed
sudo ifconfig wlan0 up
sudo iwlist scan
```Does it produce any wireless sites?

---

### Post by Adampell on 2009-06-02
> **Ayuthia said:**
> Are you trying to connect via ad-hoc?  This is probably not the correct technical way of saying it, but it looks like you are trying to use your wireless connection to share the internet or else you are trying to connect to another computer (instead of a router).

If that is not the case, can you try the following:
```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode Managed
sudo ifconfig wlan0 up
sudo iwlist scan
```Does it produce any wireless sites?

At work at the moment so will try them commands when I get in.

It seems I personaly was using Adhoc instead of inferstructure(sp?). I corrected this setting in the wireless manager now it keeps asking me for the wep key. I keep putting it in but it still keeps asking for it as if its not correct. I know the key is correct because it works in my windows install. Any ideas?

Again sorry for thread hijack. Bollock me if you must lol.

---

### Post by unknown23 on 2009-06-03
this is my output

adowcast@shadowcast-laptop:~$ 
shadowcast@shadowcast-laptop:~$ sudo ifconfig wlan0 down
shadowcast@shadowcast-laptop:~$ sudo iwconfig wlan0 mode Managed
shadowcast@shadowcast-laptop:~$ sudo ifconfig wlan0 up
shadowcast@shadowcast-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.


now what?

---

