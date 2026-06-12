---
title: "Sharing internet connection with computer already wired to router"
date: 2009-12-22
forum: Networking &amp; Wireless
---

### Post by Nibbos on 2009-12-22
Hi,
I have a Linksys Wireless router which I used WIRED to my Ubuntu machine (9.10) which sits in my loft. Next to that I have another (older) machine also running 9.10. I'd like to connect the two together with a crossover cable (which I already have) because the router sits downstairs so I can't connect the older machine directly to it.
Please can someone describe, simply, how I set up my network cards to allow the older machine to connect to internet/route (and hence the NAS box and other storage) via the newer machine with the crossover cable.

eth0 is the LAN card, eth1 connects to the router.
Here are the current settings I have, having fiddled with nothing.
ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:02:e3:16:8a:c6  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::202:e3ff:fe16:8ac6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6102 (6.1 KB)  TX bytes:2520 (2.5 KB)
          Interrupt:17 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:11:09:c2:f3:dc  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:9ff:fec2:f3dc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17739 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15268 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15923555 (15.9 MB)  TX bytes:2880161 (2.8 MB)
          Interrupt:20 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:74 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8023 (8.0 KB)  TX bytes:8023 (8.0 



Thanks in advance.

Nibbos

---

### Post by spd106 on 2009-12-22
Please follow the instructions on this wiki page first.

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)


If you have any problems then post back here and we'll try to help.

---

### Post by Nibbos on 2009-12-22
OK thanks.
I'll head over there first.
Regards
Nibbos

---

### Post by Nibbos on 2009-12-23
OK,
so I tried _Ubuntu 9.10 Method_ - nothing worked. In fact I lost my Internet connection from the host computer when i changed settings to 'Share this connection with another computer'

So I tried the next method _Ubuntu Internet Gateway Method (iptables_) - but when I came to edit various files, the existing ones were blank, so I couldn't find the lines to edit! In particular, on the client computer, the following was impossible because the file was blank:

Open /etc/dhcp3/dhclient.conf with your favorite text editor: 

sudo nano /etc/dhcp3/dhclient.conf

after that, next set-ups seem way too complicated.
I had hoped that this would be a -plug'n'play' experience, and the first instruction suggests that it should.

Does it make a difference that the host computer isn't directly connected to the Internet but to my router?

So currently I am stuck!

More advice needed, if possible.

Thanks in advance

Nibbos

---

### Post by Iowan on 2009-12-23
Some things don't seem right - others just... different.

Karmic apparently has some options Jaunty either doesn't have - or I just haven't seen/used. Are you saying */etc/dhcp3/dhclient.conf* is blank? (That part doesn't seem right.)

It shouldn't matter "that the host computer isn't directly connected to the Internet but to my router". The host computer will just share it's "internet" (actually the connection to the router).  There are a couple more threads around on ICS. One of them had a pretty simple way to enable forwarding... I'll need to see if I can find it again.

Found it [here]("http://ubuntuforums.org/showthread.php?t=1361407"). Hope it helps!

---

### Post by Nibbos on 2009-12-23
tried most of the suggested fixes, but nothing seems to work.
Can anyone describe *in words* what the principle/process is, please?
Thanks
in advance
Nibbos

---

### Post by rocketero on 2010-01-02
> **Nibbos said:**
> OK,
so I tried _Ubuntu 9.10 Method_ - nothing worked. In fact I lost my Internet connection from the host computer when i changed settings to 'Share this connection with another computer'

So I tried the next method _Ubuntu Internet Gateway Method (iptables_) - but when I came to edit various files, the existing ones were blank, so I couldn't find the lines to edit! In particular, on the client computer, the following was impossible because the file was blank:

Open /etc/dhcp3/dhclient.conf with your favorite text editor: 

sudo nano /etc/dhcp3/dhclient.conf

after that, next set-ups seem way too complicated.
I had hoped that this would be a -plug'n'play' experience, and the first instruction suggests that it should.

Does it make a difference that the host computer isn't directly connected to the Internet but to my router?

So currently I am stuck!

More advice needed, if possible.

Thanks in advance

Nibbos


I also lost connection to the Internet when following the first part of that article where it says to configure ipv4 on the "Auto eth0" interface as "Share with Other Computers" (instead of automatic dhcp)

I think the onw who wrote that was not in his right mind when he post that.

the "auto eth0" is usually the Interface directly connected to the ISP Internet.

So after that I was also following the second part " Ubuntu Internet Gateway Method (iptables)" with not much luck.

as a matter of fact after doing all what it says there, and rebooting the ubuntu 9.10 computer there was not internet connection. I have to run the command "dhclient" in order to connect to ISP and browse the Internet.

I opened the /etc/network/interfaces 
there was one line for "auto lo" and a second line "iface lo inet loopback"


Help here would be appreciated,

---

