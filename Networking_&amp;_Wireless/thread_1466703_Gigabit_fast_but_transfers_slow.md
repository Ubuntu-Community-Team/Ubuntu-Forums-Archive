---
title: "Gigabit fast but transfers slow"
date: 2010-04-30
forum: Networking &amp; Wireless
---

### Post by blacksunseven on 2010-04-30
Hi all, I've recently gotten some new equipment for my home network and now everything is connected via gigabit to an unmanaged switch. I use SFTP mostly between my client computers and my server and find that the transfers are still 100Mbps speeds, usually topping out at 9MBps or so. I spent some time researching it and found iperf and used it to benchmark the speed between my server and desktop computer.
```
blacksunseven:~$ iperf -s
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
[  4] local 192.168.1.149 port 5001 connected with 192.168.1.124 port 63861
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-10.0 sec  1.08 GBytes    928 Mbits/sec
[  5] local 192.168.1.149 port 5001 connected with 192.168.1.124 port 63964
[  5]  0.0- 0.5 sec  50.0 MBytes    920 Mbits/sec
[  4] local 192.168.1.149 port 5001 connected with 192.168.1.124 port 63965
[  4]  0.0-45.2 sec  4.88 GBytes    929 Mbits/sec

```
```
blacksunseven:~$ iperf -c 192.168.1.124 -n 5000MB
------------------------------------------------------------
Client connecting to 192.168.1.124, TCP port 5001
TCP window size: 1.16 MByte (default)
------------------------------------------------------------
[  3] local 192.168.1.149 port 49446 connected with 192.168.1.124 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-44.7 sec  4.88 GBytes    939 Mbits/sec
```

As you can see, the gigabit is running at a very good speed according to iperf but I can't see this speed anywhere. Below you can see what my network adapter, a RTL8111DL, looks like in ifconfig:

```
blacksunseven:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:25:22:25:06:1d  
          inet addr:192.168.1.149  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::225:22ff:fe25:61d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11900309 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9709074 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11354463576 (11.3 GB)  TX bytes:6418446259 (6.4 GB)
          Interrupt:25 Base address:0xe000 
```

It's worth mentioning that everything else on my network is set up for 9K jumbo frames while my server isn't. I tried installing the latest Linux drivers for it from Realtek's website [here]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false") and installed them seemingly succesfully. After installing them, I was able to run
```
sudo ifconfig eth0 mtu 9000
```
without encountering my usual error
```
blacksunseven:~$ sudo ifconfig eth0 mtu 9000
SIOCSIFMTU: Invalid argument

```
but could not get any network connections to work via LAN/Internet. I rebooted and all was well again but I'm unable to set the mtu to 9K anymore - I have no idea if the driver is even still in use.

So I'd say I've got a bit of a networking fiasco but I'm looking for any and all help here. Thanks in advance.

---

### Post by psusi on 2010-04-30
As for the jumbo frames, you might try poking around with ethtool.  As for the limited speed with sftp, it is probably just a limitation of that program.  Especially if iperf between the two same machines shows much better performance.

---

### Post by blacksunseven on 2010-04-30
> **psusi said:**
> As for the jumbo frames, you might try poking around with ethtool.  As for the limited speed with sftp, it is probably just a limitation of that program.  Especially if iperf between the two same machines shows much better performance.

```
ethtool -G ethX [rx N] [rx-mini N] [rx-jumbo N] [tx N]
ethtool -G eth0 rx-jumbo 9000
```

Would this be the correct command youd suggest using in conjuction with ethtool?

---

### Post by psusi on 2010-04-30
The second line does not appear to follow the synopsis you show on the first line.  You need to give it actual numbers for each type of frame to tell it how many to hold, though you should not need to change those values.

---

