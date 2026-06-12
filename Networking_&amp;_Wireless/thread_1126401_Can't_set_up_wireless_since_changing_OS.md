---
title: "Can't set up wireless since changing OS"
date: 2009-04-15
forum: Networking &amp; Wireless
---

### Post by norm.h on 2009-04-15
Since changing from Fedora 9 to Ubuntu 7.1, I can't set up my laptop wireless connection.
My desktop is hardwired and works OK in Fedora 10
This is what I'm getting:

compaq@compaq-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"V1_n0rm"  Nickname:"HERMES I"
          Mode:Managed  Frequency:2.417 GHz  Access Point: 00:02:CF:72:0F:C6   
          Bit Rate:11 Mb/s   Sensitivity:1/3  
          Retry limit:4   RTS thr:off   Fragment thr:off
          Encryption key:3537-5653-50   Security mode:open
          Power Management:off
          Link Quality=38/92  Signal level=-59 dBm  Noise level=-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:3  Rx invalid frag:1
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

compaq@compaq-laptop:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:D0:59:93:4A:CE  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

eth1      Link encap:Ethernet  HWaddr 00:02:2D:00:55:66  
          inet addr:192.168.1.35  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:2dff:fe00:5566/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1296 (1.2 KB)  TX bytes:7864 (7.6 KB)
          Interrupt:3 Base address:0x180 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:704 (704.0 b)  TX bytes:704 (704.0 b)


compaq@compaq-laptop:~$ sudo gedit /etc/network/interfaces

auto lo
iface lo inet loopback

iface eth1 inet static
address 192.168.1.35
netmask 255.255.255.0
gateway 192.168.1.1
wireless-key 57VSP
wireless-essid V1_n0rm

auto eth1

Pings:

compaq@compaq-laptop:~$ sudo ping -c 4 192.168.1.35 (My device)
PING 192.168.1.35 (192.168.1.35) 56(84) bytes of data.
64 bytes from 192.168.1.35: icmp_seq=1 ttl=64 time=0.074 ms
64 bytes from 192.168.1.35: icmp_seq=2 ttl=64 time=0.054 ms
64 bytes from 192.168.1.35: icmp_seq=3 ttl=64 time=0.057 ms
64 bytes from 192.168.1.35: icmp_seq=4 ttl=64 time=0.057 ms

--- 192.168.1.35 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2998ms
rtt min/avg/max/mdev = 0.054/0.060/0.074/0.011 ms


compaq@compaq-laptop:~$ sudo ping -c 4 127.0.0.1 (Loopback)
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.076 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.058 ms
64 bytes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.054 ms
64 bytes from 127.0.0.1: icmp_seq=4 ttl=64 time=0.053 ms

--- 127.0.0.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 0.053/0.060/0.076/0.010 ms


compaq@compaq-laptop:~$ sudo ping -c 4 192.168.1.1 (My router)
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=2 ttl=254 time=2.68 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=254 time=2.55 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=254 time=2.70 ms

--- 192.168.1.1 ping statistics ---
4 packets transmitted, 3 received, 25% packet loss, time 3008ms
rtt min/avg/max/mdev = 2.552/2.648/2.706/0.090 ms
compaq@compaq-laptop:~$ 

Can't ping beyond this.
Can anyone interpret these results and point me in the right direction, please?
norm

---

### Post by RedSingularity on 2009-04-15
Why dont you try the latest release of Ubuntu?  8.10

---

### Post by chili555 on 2009-04-15
Please open a terminal and try:```
echo "nameserver 192.168.1.1" | sudo tee /etc/resolv.conf
ping -c3 www.google.com
```Please let us know.

---

### Post by norm.h on 2009-04-15
> **chili555 said:**
> Please open a terminal and try:```
echo "nameserver 192.168.1.1" | sudo tee /etc/resolv.conf
ping -c3 www.google.com
```Please let us know.


compaq@compaq-laptop:~$  echo "nameserver 192.168.1.1" | sudo tee /etc/resolv.conf
nameserver 192.168.1.1

compaq@compaq-laptop:~$ ping -c3 [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (209.85.227.147) 56(84) bytes of data.
64 bytes from wy-in-f147.google.com (209.85.227.147): icmp_seq=1 ttl=237 time=30.4 ms
64 bytes from wy-in-f147.google.com (209.85.227.147): icmp_seq=2 ttl=237 time=30.2 ms
64 bytes from wy-in-f147.google.com (209.85.227.147): icmp_seq=3 ttl=237 time=31.3 ms

--- [www.l.google.com](www.l.google.com) ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 30.219/30.651/31.311/0.494 ms

Thanks for your interest. Now where?
norm

---

### Post by norm.h on 2009-04-15
"Thanks for your interest. Now where?
norm[/QUOTE]

All working OK, but don't understand what I've done!!!
Once again, many thanks
norm

---

### Post by chili555 on 2009-04-15
You are very welcome. What you did was populate your */etc/resolv.conf *file. This file tells your system where to get translations from names, [www.google.com](www.google.com), for example, to numbers, such as 209.85.227.147.

If your computer uses DHCP, when it gets an IP address from the router or other access point, it also gets DNS nameservers. However, if you set up a static IP address, you, not the router, are expected to provide DNS details. All we did, in this case, was tell your computer to use the router for DNS information. I just used a shortcut, 'sudo tee' etc., rather than write to the file, proofread, save and close a text editor.

I am glad your system is working well now.

---

### Post by Take0n on 2009-09-20
Hello

I know there has been a while since this topic was made but I have installed Ubuntu 9.04 two days ago and have a similar problem with my wireless network.

I am not able to see the wireless network at home.. I am able to see it through my mobile phone or my fathers computer which runs windows vista but not from ubuntu.. It has WEP protection (128bit) and DHCP enabled.

Could you people pls help me find why it won't see the wireless network?

Thanks in advance

---

### Post by chili555 on 2009-09-20
> **Take0n said:**
> Hello

I know there has been a while since this topic was made but I have installed Ubuntu 9.04 two days ago and have a similar problem with my wireless network.

I am not able to see the wireless network at home.. I am able to see it through my mobile phone or my fathers computer which runs windows vista but not from ubuntu.. It has WEP protection (128bit) and DHCP enabled.

Could you people pls help me find why it won't see the wireless network?

Thanks in advancePlease start a new thread and post the result of these terminal commands:```
sudo lshw -C network
iwconfig
```

---

### Post by pintalgado on 2009-09-21
Can you help mke with this please?
 
[EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL] sudo iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
wmaster0  no wireless extensions.
wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.432 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
pan0      no wireless extensions.
[EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL]

---

### Post by chili555 on 2009-09-21
Please start a new thread.

---

