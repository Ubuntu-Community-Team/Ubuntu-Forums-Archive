---
title: "Overrun / Dropped packets from via-rhine network card"
date: 2010-10-15
forum: Networking &amp; Wireless
---

### Post by Jaytea21 on 2010-10-15
Hello,

My apologies for posting this if it is redundant or maybe already answered as I did STF several times to try and possibly find an answer to my issue and did not yield any answers for my issue.

I am running Ubuntu 8.0.4.4 Server 64 bit.  I have a Via-Rhine onboard network card.  When I view the network card from ifconfig I get the following output:

eth1      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx
          inet addr:xxx.xxx.x.xxx  Bcast:xxx.xxx.x.xxx  Mask:255.255.255.0
          inet6 addr: fe80::214:85ff:fefe:db9e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:201332704 [COLOR="Red"]errors:20 dropped:2245 overruns:20[/COLOR] frame:0
          TX packets:209031031 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:192790772570 (179.5 GB)  TX bytes:225221620518 (209.7 GB)
          Interrupt:23 Base address:0x8000

I'm concerned about the errors, dropped packets and overruns that the card has on RX.  I can't seem to find out what is causing this to happen and it is kind of driving me nuts.  This is a 10/100mbit card as well.

Output from lshw -C Network:

 *-network
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth1
       version: 78
       serial: 00:14:85:fe:db:9e
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full ip=xxx.xxx.x.xxx latency=64 link=yes maxlatency=8 mingnt=3 module=via_rhine multicast=yes port=MII speed=100MB/s

Kernel in use: 2.6.24-28-server

I don't see any errors regarding eth1 when I do a dmesg / review the /var/log/messages file.  I understand that TCP does do error correction and re-trasmits if the received data is not good, however I have a few other friends that are running Linux boxes (not Ubuntu) and they have 0 errors, 0 dropped packets, and 0 overruns.  The box has been barely up for a week since the last reboot.

I've tried switching network cables, ports on my switch... I'm at wits end.  Would upgrading to another release of Ubuntu solve my issue?  Could anyone recommend any troubleshooting methods to try and narrow this thing down further?

My Linux skills are not all the best but I do know the basics to get around pretty good.  Is there some other driver I can use for this card? Maybe this driver is buggy somehow?

Thanks in advance for any help on this issue it is really appreciated.

-Jaytea21

---

### Post by Jaytea21 on 2010-10-17
No one has any ideas? :-(  I guess my next move is to just try and upgrade to the next release or the newest release of Ubuntu.

I really like this distribution of Linux it just sucks that I have this kind of problem that I can't seem to nail down.

-Jaytea

---

