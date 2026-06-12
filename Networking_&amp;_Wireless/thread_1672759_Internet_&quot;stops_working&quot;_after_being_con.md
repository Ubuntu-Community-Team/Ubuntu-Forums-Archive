---
title: "Internet &quot;stops working&quot; after being connected for about a minute"
date: 2011-01-21
forum: Networking &amp; Wireless
---

### Post by pound_forthesound on 2011-01-21
Hi everyone,

my netbook (running 10.10) has recently decided to only work with my wireless for a short while after connecting.  After this time, it just won't load a page at all, but remains connected to the router.  Disconnecting then reconnecting to the network allows me to use the internet again, but only for a short while.  This is a recent problem, and the netbook used to "just work" with wireless.  Anyone have any idea what's gone wrong?

Harry

---

### Post by emarcelcom on 2011-01-21
Hi Mate,

how about other devices you've got connected to that router? Are they working properly or this is only one device you have?

let's try for the beginning the following:
run terminal and:
1. issue a command "ifconfig" paste results
2. issue a command "iwconfig" paste results
3. issue command "route" 
4. issue "ping google.com" command after you've lost connection and paste the results here.

Cheers!!

---

### Post by pound_forthesound on 2011-01-21
Hi,

I have a desktop connected via ethernet that is functioning fine (typing on it now).  Also a blackberry that is working fine over the wireless.  Here are the outputs you asked for:

1.

harry@harry-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:18:6e:5e:a3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:44 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:58 errors:0 dropped:0 overruns:0 frame:0
          TX packets:58 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5555 (5.5 KB)  TX bytes:5555 (5.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:25:d3:46:49:92  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::225:d3ff:fe46:4992/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:293 errors:0 dropped:0 overruns:0 frame:0
          TX packets:196 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:74337 (74.3 KB)  TX bytes:40025 (40.0 KB)

harry@harry-laptop:~$ 

2.

harry@harry-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"virginmedia2486695"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: C0:3F:0E:C0:27:A4   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=41/70  Signal level=-69 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

harry@harry-laptop:~$ 

3.

harry@harry-laptop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
harry@harry-laptop:~$ 

4.

harry@harry-laptop:~$ ping google.com
ping: unknown host google.com
harry@harry-laptop:~$ 


Thanks for the help :)

---

### Post by pound_forthesound on 2011-01-21
I just tried running a live USB of 10.10 on the netbook, and the same problem occurred... Does this imply some kind of hardware problem?

---

### Post by ravengangrel on 2011-01-23
Please, check this.

[http://ubuntuforums.org/showthread.p...7#post10388907]("http://ubuntuforums.org/showthread.php?p=10388907#post10388907")

If my workaround works for you, please, post your hardware config in my thread. I would like to know if this is related to some particular  hardware.

---

