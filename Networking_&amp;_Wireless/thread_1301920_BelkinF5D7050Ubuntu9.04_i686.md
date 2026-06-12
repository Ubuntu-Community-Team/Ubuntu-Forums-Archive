---
title: "BelkinF5D7050/Ubuntu9.04 i686/"
date: 2009-10-26
forum: Networking &amp; Wireless
---

### Post by SanLinux on 2009-10-26
I installed Ubuntu 9.04 server few days back and configured my USB wireless card which is Belkin F5D7050 v4000 and configured that to work with my WPA by using some hack from ubuntu forum. Later I installed GNOME on it to have a GUI exp. coz I am from windows world although a programmer but doesn't know much about Linux hacks.

Although it was working great until today when I started my PC, it hanged with a blank screen and I had to push the power off to restart the PC in recovery mode to go without X so I clicked command prompt with network enabled and it hanged there too with the error message

"**wmaster0: Unknow hardware address type 801**"

I was surprised and I pushed the power off and this time I started the PC again in recovery mode to show the command line but this time without network enabled and it worked.

But to my surprise when I pinged google.com, it worked that means my wireless was conneted to the network, so I restarted my machine with to enter the GUI mode but Ubuntu hangs and it hangs on the Command Prompt with Network Enabled too with the same error message.

I don't know what went wrong but I can't seem to start my machine in GUI mode, Please help and I completely new to Linux world and its command so please bear with me.

The last events that I can remember is that I installed Virtual Box and it was working pretty fine.

My Linux Kernel version is **2.6.28-16-server i686**

following are the results of the commands

>> ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4486 (4.4 KB)  TX bytes:4486 (4.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1c:df:e1:3c:67  
          inet addr:192.168.10.7  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:dfff:fee1:3c67/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:248 errors:0 dropped:0 overruns:0 frame:0
          TX packets:180 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:26346 (26.3 KB)  TX bytes:37913 (37.9 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1C-DF-E1-3C-67-63-36-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

----------------------------------------------------------------------

>>iwconfig
lo          no wireless extensions.
    
eth1          no wireless extensions.

eth0          no wireless extensions.

wmaster0          no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Sanju_Wireless"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:4D:4A:7C:38   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:719D-4511-D862-740A-9B69-DDF4-BEBC-567F-2333-9C18-9BCC-B857-356D-9B8A-2908-9B13 [2]   Security mode:open
          Power Management:off
          Link Quality=94/100  Signal level:32/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

--------------------------------------------------
>> cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.10.7
netmask 255.255.255.0
gateway 192.168.10.1
wpa-driver wext
wpa-ssid Sanju_Wireless
wpa-ap-scan 1
wpa-proto WPA
wpa-pairwise TKIP
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk bd5527d5168c6462b1553d3a21c713b2f81657a93d8085fa84a72ed414804887

-----------------------------------
>> lsusb
Bus 001 Device 003: ID 050d:705c Belkin Components F5D7050 v4000 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04f2:0111 Chicony Electronics Co., Ltd KU-9908 Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

----------------------------------------------------------

Please help me out
Thanks
San

---

