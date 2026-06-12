---
title: "Ubuntu 11.04 system drops inbound network packets every 5 seconds"
date: 2011-05-20
forum: Networking &amp; Wireless
---

### Post by nickswanjan on 2011-05-20
I have a system running 11.04 and it is dropping packets on the hardwired ethernet interface to other systems on the LAN, only in the inbound direction. It drops packets every 5 seconds. I verified this with iperf. Outbound packets pass with no problems.

The network card in this system is a Broadcom Corporation NetXtreme BCM5752

Any ideas how to diagnose and fix this?

---

### Post by nickswanjan on 2011-05-20
This loss problem appears to be caused by some Ubuntu specific system or driver event that is happening every 5 seconds, interrupting network receive?

I booted the same system into Fedora 14, and ran the same iperf test with no loss.

---

### Post by nickswanjan on 2011-05-20
Tried disabling various services, but no difference. What would happen every 5 seconds that might cause this problem? 11.04 seems to already include the latest Broadcom driver, so I don't think that is the problem.

---

### Post by nickswanjan on 2011-05-20
Any hints what to try next?

---

### Post by LinuxRocks on 2011-05-20
Just want to chime in with the same issue:

Just upgraded from 10.10 server to 11.04 server. Using KVM and hosting 4 web servers. 

Just after a reboot...

```

br0       Link encap:Ethernet  HWaddr 00:08:c7:aa:92:6c
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2394 errors:0 dropped:64 overruns:0 frame:0
          TX packets:1968 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:333466 (333.4 KB)  TX bytes:516016 (516.0 KB)

```

```

virbr0    Link encap:Ethernet  HWaddr 7e:fe:de:d0:52:e2
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:52 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

Hardware is:

```

Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 05)

2.6.38-8-server #42-Ubuntu SMP Mon Apr 11 03:49:04 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

System Information
        Manufacturer: Gigabyte Technology Co., Ltd.
        Product Name: GA-880GMA-UD2H

AMD Phenom(tm) II X6 1055T Processor (Six Core)

```

Again, after upgrading from 10.10 where there was NO issue, to 11.04 where this is being seeing.

Anyone file a bug report yet or have any ideas on how to fix the issue?

Thanks!
Joe

---

### Post by nickswanjan on 2011-05-20
I notice you have a different NIC, do you also see the cyclical loss every 5 seconds, or have you tested with a tool that might show this?

---

### Post by nickswanjan on 2011-05-20
I'll bet many other people have this same loss problem, but don't necessarily notice it - it would not show up in normal web browsing or other use. It drops 5-11% of your packets for a brief interval every 5 seconds.

It is most noticeable as intermittent pixelation if you try to view streaming real-time video (e.g. Mythtv/Mythbuntu).

---

### Post by laymans on 2011-05-20
I use to have this problem with a brand new Ubuntu 11.04 system.  I used it fine for a while and then a couple of weeks later the issue you describe started happening.  

I removed the Chromium Web Browser and the problem has not reoccurred yet.  Perhaps you have some other app that is battling Ubuntu for control of the NIC?


Other than that I have no idea...still learning Linux.


Sheridan

---

### Post by LinuxRocks on 2011-05-20
> **nickswanjan said:**
> I notice you have a different NIC, do you also see the cyclical loss every 5 seconds, or have you tested with a tool that might show this?

I have not noticed it being "Consistent" or any pattern, its just there and it bugs me. Its not allot of dropped packets, but the fact that the previous version didn't do it, it leads me to think there is a bug.

I have downgraded to the 10.10 kernel and it goes away. However, I have also upgraded to the ppa kernel and its still there, so it might be something in the driver. 

Have to check kernel change logs from the 10.10 kernel to the 11.04 kernel to see what may have changed to cause it.

Not sure what the issue could be, but its definitely there and needs to be looked at. 

Here is my netstat -s output:

```

netstat -s
Ip:
    52658 total packets received
    0 forwarded
    0 incoming packets discarded
    52565 incoming packets delivered
    48457 requests sent out
Icmp:
    0 ICMP messages received
    0 input ICMP message failed.
    ICMP input histogram:
    0 ICMP messages sent
    0 ICMP messages failed
    ICMP output histogram:
Tcp:
    7 active connections openings
    7 passive connection openings
    0 failed connection attempts
    0 connection resets received
    1 connections established
    52069 segments received
    49478 segments send out
    46 segments retransmited
    0 bad segments received.
    1 resets sent
Udp:
    326 packets received
    0 packets to unknown port received.
    0 packet receive errors
    326 packets sent
UdpLite:
TcpExt:
    7 TCP sockets finished time wait in fast timer
    1298 delayed acks sent
    Quick ack mode was activated 8 times
    3 packets directly queued to recvmsg prequeue.
    1448 bytes directly in process context from backlog
    3 bytes directly received in process context from prequeue
    32565 packet headers predicted
    1 packets header predicted and directly queued to user
    1492 acknowledgments not containing data payload received
    15650 predicted acknowledgments
    17 times recovered from packet loss by selective acknowledgements
    2 TCP data loss events
    5 timeouts after SACK recovery
    22 fast retransmits
    3 retransmits in slow start
    13 other TCP timeouts
    8 DSACKs sent for old packets
    1 DSACKs received
    TCPDSACKIgnoredOld: 1
    TCPSackShifted: 20
    TCPSackMerged: 27
    TCPSackShiftFallback: 66
IpExt:
    InMcastPkts: 85
    InBcastPkts: 85
    InOctets: 8612047
    OutOctets: 12624846
    InMcastOctets: 2720
    InBcastOctets: 12669

```

I see some data loss events and some retransmits. I'm not a network guy, but there does look like some issues with the driver.

Do any Devs look at this forum or should I put in a bug request?

Thanks!
Joe

---

### Post by nickswanjan on 2011-05-20
Ok, given that I am now running 11.04, how do I downgrade to the 10.10 kernel as a workaround? Is it a manual process or something I can do with apt?

---

### Post by LinuxRocks on 2011-05-20
> **nickswanjan said:**
> Ok, given that I am now running 11.04, how do I downgrade to the 10.10 kernel as a workaround? Is it a manual process or something I can do with apt?

What I did was enable backports and install linux-image-2.6.32-31-server

That is the one that was working for me.

Hope this helps!

Joe

---

### Post by LinuxRocks on 2011-05-23
Ok, I started a bug report for my issue...

Feel free to add to is if you having the same type of issue - [https://bugs.launchpad.net/ubuntu/+bug/787055](https://bugs.launchpad.net/ubuntu/+bug/787055)

Thanks!
Joe

---

