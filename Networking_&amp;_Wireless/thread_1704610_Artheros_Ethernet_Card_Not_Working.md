---
title: "Artheros Ethernet Card Not Working"
date: 2011-03-10
forum: Networking &amp; Wireless
---

### Post by cnote8 on 2011-03-10
I'm very new to Ubuntu, have only had it for about 2 days.  I've scoured the net and the forums trying to find a solution, but nothing has worked for me so far.  So now onto my problem...

I have an Artheros Ethernet Card, one that requires the special download.  I downloaded it, and tried the following commands
1.  tar -zvxf AR81Family-linux-v1.0.1.14.tar.gz
2.  cd src
3.  sudo apt-get install linux-headers-generic build-essential make
4.  sudo make install
then I get 
Makefile:105:***Linux kernel source not configured - missing autoconf.h.  Stop.

I'm stuck at this point, and not sure what to do.  Do I need to put the above file in a certain folder?  I tried doing a symlink to another autoconf.h from /usr/src/linux-headers-2.6.35-22-generic/include/generated/autoconf.h and received a Permission Denied error.  I've tried uninstalling Ubuntu and reinstalling using my wired connection using Wubi, and the ethernet card still wasn't recognized.

I ran the ifconfig -a and got this:
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

wlan0     Link encap:Ethernet  HWaddr 90:00:4e:15:87:b7  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::9200:4eff:fe15:87b7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4275 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3218 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3962871 (3.9 MB)  TX bytes:703987 (703.9 KB)

I am dual-booting with Windows 7, and can connect with the ethernet card in Windows, so I know it works.  I just can't get it to work in Ubuntu 10.10.  Any help would be greatly appreciated.

---

### Post by zenwalker on 2011-03-10
Is the driver for your Atheros Chip not supported by default? i belive it should. Atheros does support drivers for linux. In that case, i see no use of compiling for yourself.

---

### Post by cnote8 on 2011-03-11
> **numinous said:**
> From your ifconfig information we know you have a network interface.

Now as root do this

iwconfig

so you know if your network interface has wireless capability
So here's what I got when I ran iwconfig
wlan0     IEEE 802.11bgn  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:66: D7:E3:AA   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Encryption key: off
          Power Management: off
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

