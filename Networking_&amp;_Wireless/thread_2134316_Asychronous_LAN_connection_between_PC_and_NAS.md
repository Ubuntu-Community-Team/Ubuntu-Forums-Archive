---
title: "Asychronous LAN connection between PC and NAS"
date: 2013-04-10
forum: Networking &amp; Wireless
---

### Post by RandyN on 2013-04-10
Hello! I've been trying to figure out why my Ubuntu 12.1 desktop (Core2 @ 2.1GHz & 4GB RAM & onboard Gigabit Intel) transfers a 512 MB test file to my NAS4Free machine at ~10 MB/s but in the other direction I get a much more reasonable 35MB/s. The only device between them is a Trendlink 8 port Gigabit switch and I'm using Cat5e cables (about 2 feet long). 

Why does the Ubuntu PC transfer to the NAS4Free server so slow compared to the reverse? I also noticed that the transfer to the NAS is very inconsistent dropping down to 3MB/s and up to maybe 12 MB/s. Coming from the NAS server to Ubuntu it is a solid transfer rate.

Any thoughts as to what may be going on here?

TIA,
Randy

---

### Post by papibe on 2013-04-10
Hi RandyN.

I would start by testing raw speed transfers on both directions using iperf.

First, install it on the Ubuntu box:
```
sudo apt-get install iperf
```
I believe it comes preinstalled on FreeNAS.

You run it on one machine as a server:
```
iperf -s
```
And the other one as the client:
```
iperf -c 192.168.1.1
```
where that example ip (192.168.1.1) is the ip of the machine running iperf as a server (the first machine).

Hope it helps. Let us know how it goes.
Regards.

---

### Post by RandyN on 2013-04-11
Hi papibe.

I ran the tests several times and the results were pretty consistent in both directions ~560MBytes/s 

There was a difference in the TCP window size though - if that makes a difference. With NAS4Free running as server the TCP window size was 256KByte whereas the Ubuntu 12.1 PC the window size was only 85.3 KByte

Back to you

---

### Post by papibe on 2013-04-13
By any chance did you setup an ZFS partition on your NAS? I've read that sometimes you get very asymmetric speeds on read and write if not setup properly. That is, if you copy your data to an incomplete array, and then add more disks/partitions.

For lack of resources, most people do that and face this kind of problems. I read that the recommended procedure is to create the whole array first, and then copy your data so that can be spread across evenly.

Just a thought.
Regards.

---

### Post by RandyN on 2013-04-13
I'm using UFS for a single SATA3 disk (on an older SATA2 MOBO). I also currently have the NAS4Free server set to 1000baseTX Full duplex instead of auto negotiation but that made no difference. 

I* think* I have turned off IPV6 on the Ubuntu PC as I read that sometimes can be an issue but I'm not sure I've done that.

```
eth0      Link encap:Ethernet  HWaddr 00:19:d1:79:43:f5  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:921329 errors:0 dropped:0 overruns:0 frame:0
          TX packets:766398 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:74065209 (74.0 MB)  TX bytes:1132842660 (1.1 GB)
          Interrupt:21 Memory:dffe0000-e0000000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:817 errors:0 dropped:0 overruns:0 frame:0
          TX packets:817 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:81233 (81.2 KB)  TX bytes:81233 (81.2 KB)


```

---

### Post by papibe on 2013-04-13
It looks off (no IPv6 addresses displayed).

What protocol are you using for the transfer? smb, nfs, ftp, stfp?

Regards.

---

### Post by RandyN on 2013-04-13
I used a win7 machine and transferring the test file back and forth from my Ubuntu PC comes in at 50MB/s. From Win7 to the NAS server I got 70MB/s and in the reverse 35MB/s.

Very odd...the slow speed only seems to be a problem when uploading from Ubuntu to the NAS4Free (and vice versa).

SMB/CIFS protocol

I tried to turn off auto negotiation and set the speed on Ubuntu

```
sudo ethtool -s eth0 autoneg off speed 1000 duplex full
```

but when I run sudo ethtool eth0 it still shows auto negotiation on.

---

### Post by RandyN on 2013-05-02
I flashed the BIOS on the Ubuntu PC (a Dell Dimension 9200) as the flash is supposed to improve the networking in a  gigabit environment but it did not help with the transfer speeds between the Ubuntu PC and the NAS4Free server. Now I would suspect it perhaps has something to do with the D-Link DGE-530T NIC I installed in the NAS BUT the NIC is supported under FreeBSD 9.1 and transfers to and from the NAS to the Win7 machine were OK.

---

### Post by papibe on 2013-05-02
This is what I would do:

Try transfer using other protocols:
[LIST]
[*]FTP.
[*]NFS.
[*]rsync over ssh (use the option --progress to measure the rate).
[/LIST]
FTP should be the fastest. NFS second, and rsync/ssh should be last (because of encryption).

If none of these transfers suffer for the asynchrony problem, we may conclude then it is a samba configuration problem, and we can start playing with tuning options.

Just my thoughts.
Regards.

---

### Post by tgalati4 on 2013-05-02
Try making a permanent mount in /etc/fstab.  Then try your tests again.  Sometimes mounting in Nautilus can cause slow performance.

---

