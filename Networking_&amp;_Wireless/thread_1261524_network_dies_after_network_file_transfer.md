---
title: "network dies after network file transfer"
date: 2009-09-08
forum: Networking &amp; Wireless
---

### Post by chucklarge on 2009-09-08
whenever i transfer files >100megs or so over network (nfs, netatalk, http) the transfer starts and then pauses after 50-150megs downloaded.  Then the network on the ubuntu machine serving the files goes down and I can not connect to it.  the network may come back up after like 10 min or so.  The weird thing is when the download pauses, if i restart the ubuntu network, the download resumes but then pauses again after another 50-150megs dl.  i just restarted networking about 8 times to finish a 1gig file.  any ideas?

Chuck
9.04
Linux atombomb 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GNU/Linux

```
eth0      Link encap:Ethernet  HWaddr 00:24:21:1b:d3:1c  
          inet addr:192.168.0.143  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::224:21ff:fe1b:d31c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1369519 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2829395 errors:0 dropped:155 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:107168787 (107.1 MB)  TX bytes:4076266816 (4.0 GB)
          Interrupt:253 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:259 errors:0 dropped:0 overruns:0 frame:0
          TX packets:259 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:24168 (24.1 KB)  TX bytes:24168 (24.1 KB)

```

an iostat during a file transfer where i have to keep restarting networking
[http://paste.ubuntu.com/267649/](http://paste.ubuntu.com/267649/)

update-
i found this [https://bugs.launchpad.net/ubuntu/+bug/296162](https://bugs.launchpad.net/ubuntu/+bug/296162) which describes very similar problems.  
This suggestion made no difference
sudo ethtool -K eth0 rx off tx off

---

### Post by chucklarge on 2009-09-29
-UPDATE-
I am pretty confident i resolved this.  So i have and MSI Industrial IM-945GC (MS-9832) atom 330 board with 2 Realtek RTL8111C GbE network devices.  Apparently there is an issue with Realtek devices and Ubuntu.  It supposedly was fixed with 8.04 but i had the same problems.  

The solution is to remove the default driver r8169 and replace it with a compiled version from Realtek r8168.

[http://ubuntuforums.org/showthread.php?p=4210510](http://ubuntuforums.org/showthread.php?p=4210510)

---

### Post by ionplay on 2012-03-30
I have replaced my r8169 with the new r8168
and did a apt-get update; apt-get -y dist-upgrade

I still can not transfer large files without the network dying

ubuntu 8.04
asus mainboard

---

