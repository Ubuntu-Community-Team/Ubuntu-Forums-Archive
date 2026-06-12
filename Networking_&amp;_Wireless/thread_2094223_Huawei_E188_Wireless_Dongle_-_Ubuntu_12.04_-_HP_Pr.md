---
title: "Huawei E188 Wireless Dongle - Ubuntu 12.04 - HP ProBook 4730s"
date: 2012-12-13
forum: Networking &amp; Wireless
---

### Post by Andrew F in Australia on 2012-12-13
HI All,

This Huawei E188 USB wireless dongle did work flawlessly on Ubuntu.

Set up as per: [http://ubuntuforums.org/showthread.php?t=1994588](http://ubuntuforums.org/showthread.php?t=1994588)

After a kernel upgrade, it stopped working in USB3 ports
Then, after another kernel upgrade, the device hasn't worked since (still works in Windows 7 flawlessly however.)

It registers momentarily ("you are now connected to the home network",) then flashes up "Modem Network Disconnected."  As I said, still works in Windows 7 flawlessly.

Does anybody have any clues as to how to re-enable this modem? (relevant details below.)  It looks as though it's back to registering as a USB stick instead of a modem as it comes up in Nautilus as a drive.

Thanks in advance,

Andrew F

-----------------------------
Detected as a USB in lsusb
Bus 002 Device 006: ID 12d1:1c07 Huawei Technologies Co., Ltd. 


Not detected in ifconfig, iwconfig
```

horace@horace-HP-ProBook-4730s:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr e4:11:5b:3f:e2:b3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:56 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1398 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1398 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:121311 (121.3 KB)  TX bytes:121311 (121.3 KB)

ra0       Link encap:Ethernet  HWaddr 74:de:2b:fe:78:c7  
          inet addr:192.168.1.68  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::76de:2bff:fefe:78c7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26769 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4488 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15021311 (15.0 MB)  TX bytes:1566481 (1.5 MB)
          Interrupt:19 

horace@horace-HP-ProBook-4730s:~$ iwconfig
lo        no wireless extensions.

ra0       Ralink STA  ESSID:"ThomsonAB5420"  Nickname:"RT3562STA"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:26:44:40:32:41   
          Bit Rate=18 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=73/100  Signal level:-88 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

```Network adapter not detected in ifconfig, iwconfig, lsmod, dmesg, lshw, 

Kernel Architecture
```
uname -mr
3.2.0-34-generic-pae i686

```Restart
```
sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...
```

---

