---
title: "Weird file transfer problem"
date: 2013-01-09
forum: Networking &amp; Wireless
---

### Post by welshside on 2013-01-09
Hi,
I'm having problems with real slow file transfers across a network.

I have 2 pc's running windows 7 and an ubuntu server attached to a Netgear gigabit switch (GS605) which is linked to a BT home hub router.

When the ubuntu server is plugged into the switch I get real slow speeds for file transfers from windows pcs across the network of about 150KB/sec.

If I unplug the cable from the switch and plug it into the BT home hub and do a file transfer it will work at a rate of about 10MB/sec.

From windows to windows pc it seems a lot faster through the switch, over 25MB/sec.

Has anyone got any idea why the Ubuntu server is so slow when attached to the switch and what I can look at to fix it.

All the lights show as yellow on the switch to signify 1Gbps connection and the server has a new cat 6, 3m long cable.

---

### Post by welshside on 2013-01-10
I ran iperf (iperf -c 192.168.1.50 -w 1024k -i 2 -t 20) and got the results below if that helps at all.


------------------------------------------------------------
Client connecting to 192.168.1.50, TCP port 5001
TCP window size: 1.00 MByte
------------------------------------------------------------
[  3] local 192.168.1.70 port 58555 connected with 192.168.1.50 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0- 2.0 sec  1.50 MBytes  6.29 Mbits/sec
[  3]  2.0- 4.0 sec   512 KBytes  2.10 Mbits/sec
[  3]  4.0- 6.0 sec   512 KBytes  2.10 Mbits/sec
[  3]  6.0- 8.0 sec   640 KBytes  2.62 Mbits/sec
[  3]  8.0-10.0 sec   768 KBytes  3.15 Mbits/sec
[  3] 10.0-12.0 sec   768 KBytes  3.15 Mbits/sec
[  3] 12.0-14.0 sec   256 KBytes  1.05 Mbits/sec
[  3] 14.0-16.0 sec   768 KBytes  3.15 Mbits/sec
[  3] 16.0-18.0 sec   512 KBytes  2.10 Mbits/sec
[  3] 18.0-20.0 sec   640 KBytes  2.62 Mbits/sec
[  3]  0.0-20.0 sec  6.88 MBytes  2.88 Mbits/sec

---

### Post by welshside on 2013-01-12
...also when the server is plugged into the router the network activity light only flashes about once every 3 seconds when idle. When it's plugged into the switch it constantly flashes.

---

### Post by Rsxhawk on 2013-01-16
Can you verify the speed/duplex of the Ubuntu server's NIC?  

ifconfig eth0

Or download ethtool and run that via command line.

---

### Post by tgalati4 on 2013-01-16
Check for kinks in the cable and that the crimps are done properly.  Those speeds are poor.

---

