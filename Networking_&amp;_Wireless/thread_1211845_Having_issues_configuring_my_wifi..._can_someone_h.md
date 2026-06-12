---
title: "Having issues configuring my wifi... can someone help?"
date: 2009-07-13
forum: Networking &amp; Wireless
---

### Post by Silverdagger on 2009-07-13
Alright... im fairly new to Linux so please bear with me..... but i've used ubuntu before and everything worked fine... but i had to format my hdd and now... things are iffy haha but on to the problem...

when im in the terminal i attempt to bring my wireless card up using the ( ifconfig wlan0 up) command and it tells me no such file or directy....

So i looked that up on google and it says that the card hasnt been installed... havent quiet been able to figure out how to install it using the noob guides from google....

but what i find odd is if i use the command ( ifconfig wlan0) if tells me the card is their and everything... it just wont let me bring it online... is that because the drivers arent installed?....

 Also why do i have to manually install them this time... when last time ubuntu installed the drivers for me...

Any help would be appriciated...

---

### Post by superprash2003 on 2009-07-13
post output of the following commands from the terminal
1)lshw -C network
2)iwconfig

---

### Post by Silverdagger on 2009-07-13
mike@mike-laptop:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:ab:ee:99
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.1.101 latency=64 module=ssb multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 12:ca:a2:14:ec:7a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


mike@mike-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  Mode:Monitor  Frequency:2.412 GHz  Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

mike@mike-laptop:~$

---

### Post by superprash2003 on 2009-07-13
wifi cards come with a wirless switch which has an on/off button , make sure its ON..

for reference : [http://www.prash-babu.com/2009/05/how-to-fix-wireless-no-scan-results-in.html](http://www.prash-babu.com/2009/05/how-to-fix-wireless-no-scan-results-in.html)

---

### Post by Silverdagger on 2009-07-13
thats the the problem im having tho... my light on my keyboard says the wifi is on.... but the terminal command ifconfig says its not and when i try to turn it on threw the terminal is says:

root@mike-laptop:/home/mike# ifconfig wlan0 up
SIOCSIFFLAGS: No such file or directory

...but  this is what i get if i input ifconfig

root@mike-laptop:/home/mike# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:22:ab:ee:99  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:22ff:feab:ee99/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:948773 errors:2 dropped:1 overruns:0 frame:0
          TX packets:555968 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1310722789 (1.3 GB)  TX bytes:43704232 (43.7 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5403 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5403 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:284293 (284.2 KB)  TX bytes:284293 (284.2 KB)

and that is WITH the light on the keyboard saying its on.... the OS knows the card is thier because the iwconfig command gives me this:

root@mike-laptop:/home/mike# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  Mode:Monitor  Frequency:2.412 GHz  Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

...any thoughts?

---

