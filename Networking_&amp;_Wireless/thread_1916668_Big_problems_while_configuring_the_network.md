---
title: "Big problems while configuring the network"
date: 2012-01-28
forum: Networking &amp; Wireless
---

### Post by rienesl on 2012-01-28
Hi,
since the initial install, my system has only a wired connection witch works. I'm not able to configure neither the wired, nor the wireess in the network-manager. It says:
Error displaying connection information:
No valid active connections found!

ifconfig gave the following
eth0      Link encap:Ethernet  HWaddr 00:02:a5:ba:95:f4  
          inet addr:192.168.178.36  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: fe80::202:a5ff:feba:95f4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6402 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6676 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5157587 (5.1 MB)  TX bytes:1135706 (1.1 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:432 errors:0 dropped:0 overruns:0 frame:0
          TX packets:432 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:33760 (33.7 KB)  TX bytes:33760 (33.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0b:9d:00:b0:57  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

iwconfig gives out the following (i tried to set Mode and ESSID manually, after the next reboot, those settings will be gone again, so assume those settings are default)
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"Rienesl"  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:  Off   Fragment thr:  Off
          Power Management:  Off

my /etc/network/interfaces containes the following:
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

my /etc/NetworkManager/nm-system-settings.conf had been completely empty, I wrote the followin in it:
[main]
plugins=keyfile

[ifupdown]
managed=true

Any ideas, what that could be? I tried to get help on #nm and #xubuntu (I'm using xfce), but no answer :(
Greetings,
Martin

---

### Post by rienesl on 2012-02-05
OK, I got news in this:
After a lot of research, I found out, that the problem might be caused by slim. So I Installed LXDM, what solved the problem with the metwork-manager, but disallowed me to start XFCE. So I installed WDM, which seems to work fine with XFCE and the network-manager. But now I get an other Problem: it shows me a weak signal strength, which causes a lot of disconnects or no connect alt all (that Problem had been under LXDE, too). Using the same NIC in an other Notebook at the same Place gives me full signal strength. What can I do?

---

