---
title: "Beginner (...) connected to router but not the internet?"
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by abo999 on 2009-02-18
I've been using Ubunto 8.10 on my laptop for a while now, but since it's only used for email and the internet I've not dived too far into the working of Ubuntu, as the thing just works :D

A few months ago I was given an old PC for my son to use in his room. It's an Athlon 1500XP with 1GB and a 40GB HD. It was running Windows and did what he needed until the hard drive died the other day. I had a spare drive so I replaced the faulty one, and since I have no Windows XP disk to install I put Ubuntu 8.10 on there.

All was working well yesterday; 8.10 installed with Edubuntu on top. He could go on the internet and access Playhouse Disney and Nick JR etc. (he's nearly 5), and play Tuxpaint etc.

TYhis morning we switched it on; Ubuntu reported connecting to my router via the wireless connection, but when opening Firefox, no website was presented ([www.bbc.co.uk/cbeebies](www.bbc.co.uk/cbeebies) is his homepage).

My router confirms that his PC is connected with a valid IP address. Clearly my router is passing internet traffic as it is working on this (Windows) PC on a wired connection, and my Ubuntu laptop works fine wirelessly.

I've tried pinging some websites from the console but it times out.

I'm pretty much at the limit of my knowledge here (I said beginner lol), can you please help me out and get my son on the internet again?

---

### Post by Hobgoblin on 2009-02-18
Sounds like it could be a DNS problem.

Ping a site from your (working) Windows system, then ping the IP address of that site from the non-working Ubuntu system.

(quick fix - probably) Reboot the router then reboot the non-working Ubuntu system.

---

### Post by abo999 on 2009-02-18
Reboots all round was the first thing I tried.

Saying the pings timed out was a slight mistake. Here is what the console reports (thank you flash drive lol):

freddie@freddie-desktop:~$ ping [www.google.co.uk](www.google.co.uk)
ping: unknown host [www.google.co.uk](www.google.co.uk)

freddie@freddie-desktop:~$ ping [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)

These both ping just fine from my other machines.

I've entered 'route' into the console, here is the result:

freddie@freddie-desktop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0

Pinging the router itself gives this:

freddie@freddie-desktop:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.3 icmp_seq=23 Destination Host Unreachable
From 192.168.0.3 icmp_seq=24 Destination Host Unreachable
From 192.168.0.3 icmp_seq=25 Destination Host Unreachable
From 192.168.0.3 icmp_seq=28 Destination Host Unreachable
From 192.168.0.3 icmp_seq=29 Destination Host Unreachable
From 192.168.0.3 icmp_seq=31 Destination Host Unreachable
From 192.168.0.3 icmp_seq=32 Destination Host Unreachable
From 192.168.0.3 icmp_seq=33 Destination Host Unreachable
From 192.168.0.3 icmp_seq=34 Destination Host Unreachable
From 192.168.0.3 icmp_seq=35 Destination Host Unreachable
From 192.168.0.3 icmp_seq=38 Destination Host Unreachable

And trying to connect to the router diagnostics from Firefox reports:

Failed to Connect
  

The connection was refused when attempting to contact 192.168.0.1.



Though the site seems valid, the browser was unable to establish a connection.


    *  Could the site be temporarily unavailable? Try again later.


    *  Are you unable to browse other sites?  Check the computer's network connection.


    *  Is your computer or network protected by a firewall or proxy? Incorrect settings can interfere with Web browsing.

---

### Post by prshah on 2009-02-18
> **abo999 said:**
> 
freddie@freddie-desktop:~$ ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.3 icmp_seq=23 Destination Host Unreachable


Ouch! Your networking hardware is down (Wired: check cable; wireless: check switch).

If you still find this a problem even after checking the hardware, give the following command and post their outputs for more clues:```

#for wired only
sudo mii-tool eth0
#for wireless only
iwconfig
#for both
ifconfig
cat /etc/network/interfaces

```

---

### Post by abo999 on 2009-02-18
More strangeness. One of the first things I tried was to unplug the wireless dongle from it's USB and try it in another. This had no effect. So I switched it to a third socket and bingo, internet is back. No other changes.

It is working more slowly than I'd expect though. Here is my iwconfig for completeness:

freddie@freddie-desktop:~$ iwconfig

lo        no wireless extensions.



eth0      no wireless extensions.



pan0      no wireless extensions.



wmaster0  no wireless extensions.



wlan0     IEEE 802.11bg  ESSID:"SKY82857"  

          Mode:Managed  Frequency:2.447 GHz  Access Point: 00:1B:2F:43:6F:DA   

          Bit Rate=54 Mb/s   Tx-Power=13 dBm   

          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   

          Power Management:off

          Link Quality=65/100  Signal level:-64 dBm  

          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



freddie@freddie-desktop:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:0a:cd:03:69:46  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

          Interrupt:11 Base address:0xbc00 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



wlan0     Link encap:Ethernet  HWaddr 00:21:27:ce:58:f3  

          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0

          inet6 addr: fe80::221:27ff:fece:58f3/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:12864 errors:0 dropped:0 overruns:0 frame:0

          TX packets:8933 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:17078314 (17.0 MB)  TX bytes:989481 (989.4 KB)



wmaster0  Link encap:UNSPEC  HWaddr 00-21-27-CE-58-F3-38-66-00-00-00-00-00-00-00-00  

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by Kevbert on 2009-02-18
The signal strength seems to be a little low (-64dBm). Can you improve this by moving the PC closer to the router or adjusting the aerial ?

---

### Post by abo999 on 2009-02-18
Yeah, that concerned me a bit. The wifi is just a dongle with a built in antenna so I'm going to try and find a USB extension and see if resiting the dongle helps. Moving the PC isn't an option unfortunately

---

