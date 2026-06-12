---
title: "Samba slow reads, fast writes. Network or Samba problem? Or ?"
date: 2010-04-16
forum: Networking &amp; Wireless
---

### Post by BMWolf on 2010-04-16
I've recently setup a new server with the specs below:
MSI 785GM-E51 mobo with latest Realtek driver for the 8111 NIC installed
AMD PhenomII x4 945
4GB DDR3

Hard disks:
1x 120GB WD Blue [sda] /
Linux Software Raid 1 [md0] /home
  2x 1TB WD10EARS [sdb & sdc]

EDIT: All NICs and router are 1000Mb/sec 

When accessing my samba shares(on md0) from my Vista(business 64) machine(t61p) I can write at 30-50 MB/sec, but my reads are abysmally slow at 6-12 MB/sec. Why is the read slower than the write? Wireless is even slower as expected. If I am writing and reading at the same time the speed of the write is reduced to the same as the read.  Installing the latest Realtek driver increased speed by a factor of 2, but the read is still too slow IMO. 

hdparm -Tt shows this:```
$ sudo hdparm -Tt /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sda

/dev/md0:
 Timing cached reads:   5888 MB in  2.00 seconds = 2944.69 MB/sec
 Timing buffered disk reads:  324 MB in  3.00 seconds = 107.98 MB/sec

/dev/sdb1:
 Timing cached reads:   7954 MB in  2.00 seconds = 3978.69 MB/sec
 Timing buffered disk reads:  324 MB in  3.07 seconds = 105.63 MB/sec

/dev/sdc1:
 Timing cached reads:   7882 MB in  2.00 seconds = 3942.15 MB/sec
 Timing buffered disk reads:  314 MB in  3.01 seconds = 104.29 MB/sec

/dev/sda:
 Timing cached reads:   7882 MB in  2.00 seconds = 3942.99 MB/sec
 Timing buffered disk reads:  248 MB in  3.00 seconds =  82.66 MB/sec

```

I know I will never see close to the above, but I would like the reads to be reaching 30-50MB/sec like the writes.

Any Idea what's going on? How would I go about finding the source of the problem? Is it a network card issue, a samba issue, a Vista issue, or something else entirely? I don't think it's a samba issue because FTP(&SCP) results seem very similar.

Thanks!

---

### Post by BMWolf on 2010-04-16
I've ran iperf on all my networked pcs and the performance seems lower than I would like. I have to assume it's the NIC at this point and plan to try a different one ASAP. It could be the router, but this server is a replacement for one that's been running 24/7 for the last 3.5 years and it didn't have these problems. All the important cables were just replaced with cat6 with zero improvement, so I can also rule them out too. 

I'll update this post once I try out the new NIC, maybe someone else with the same mobo will run into the same problems.

---

### Post by BMWolf on 2010-04-17
Today I've came back to one of my Vista machines and both write and read are now magically running at 26-46 MB/sec. 1.58GB worth of images takes about 46 seconds. Woo Hoo! Maybe It was just a Vista problem all along.

I've also ordered 3 new Intel NICs, but they haven't arrived yet. I doubt there will be much difference, but since I've already paid for them, I'm gonna see how they compare. Maybe the on-board Realtek just needed to know she was about to be replaced before deciding to step up her game.

EDIT: I ran this command on the Vista machine:
```
C:\Users\bryan\Desktop>iperf -c NAS -t30 -f 080716_t*
------------------------------------------------------------
Client connecting to NAS, TCP port 5001
TCP window size: 65.5 Kbit (default)
------------------------------------------------------------
[396] local 127.0.0.1 port 54631 connected with 192.168.80.5 port 5001
[ ID] Interval       Transfer     Bandwidth
[396]  0.0-30.0 sec  12.2 Gbits   406 Mbits/sec

```

...and then this on the Ubuntu server:
```
bryan@NAS:~$ iperf -c 192.168.80.25 -t30 -f 080716_T*
------------------------------------------------------------
Client connecting to 192.168.80.5, TCP port 5001
TCP window size:   131 Kbit (default)
------------------------------------------------------------
[  3] local 192.168.80.5  connected with 192.168.80.25
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-30.0 sec  14.8 Gbits    494 Mbits/sec

```

The file used was a 500MB .tif image, since I regularly work with .tifs in the 100-1000MB range. So Samba looses quite a bit of performance, but I think this is pretty good speed for the onboard NIC on a $79.00 motherboard and the cpu running in Cool and Quiet mode at 800mhz.:)

---

### Post by BMWolf on 2010-04-27
I've installed the new Intel NICs and saw a 25-50% increase in performance on the Ubuntu machine, but only 5-10% on the vista machine. Iperf shows ~700-750Mb/sec on the Linux machine and 400-500Mb/sec on the Vista workstation. I'll be trying jumbo frames later, but I've come to conclude that my Vista install has mediocre network performance, and there's just not much that I can do about it. I had to move the Linux box over to CentOS because of some 3rd party software that won't run on Ubuntu, and I'm seeing similar performance there as well; as expected. 

The new NICs are these if anyone is interested: [Intel Gigabit CT PCI-E]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833106033")

**EDIT:** I'm beginning to feel like I'm talking to myself! :P Anyway, I may have spoke too soon. It seems that on Vista, samba transfer speed increase dramatically after a few days. I don't know why exactly, perhaps it quits indexing the mapped drive? I am now regularly getting in excess of 700 MB/sec in both directions. If I do multiple transfers the total is over 900 Mb/sec. I couldn't be happier!

---

