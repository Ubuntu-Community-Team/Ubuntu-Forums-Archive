---
title: "Diskless PXE Boot  Fails to Mount Root File System"
date: 2010-12-16
forum: Networking &amp; Wireless
---

### Post by paulobear on 2010-12-16
Hi - 

I'm trying to set up an Ubuntu VM environment on a Windows 7 Host using VirtualBox to do Linux development at work. The development target (client) is an Atom single board computer. It is connected via both serial and crossover ethernet cable directly to the Windows host. 

I have successfully gotten everything working right up to the point where the client attempts to mount the root file system. For what it's worth, I did get this to work just fine on a VMware Workstation VM. So I'm not sure why it's not working for VirtualBox. 

The Ubuntu guest install is vanilla 10.10 Desktop plus the latest updates (about 209MB or so). I have modified the networking environment according to the attached files. I've only modified hosts.allow/deny because this issue appeared after things worked. I even re-installed Ubuntu from scratch to see if I'd messed something else up.

On the client, I get these messages at the end:

```
----------------------
Target boot log
----------------------
Sending DHCP requests ., OK
IP-Config: Got DHCP answer from 10.0.0.1, my address is 10.0.0.2
IP-Config: Complete:
     device=eth0, addr=10.0.0.2, mask=255.0.0.0, gw=255.255.255.255,
     host=10.0.0.2, domain=, nis-domain=(none),
     bootserver=10.0.0.1, rootserver=10.0.0.1, rootpath=/home/paulourada/timesys/atomus15w/rfs
Looking up port of RPC 100003/2 on 10.0.0.1 
Looking up port of RPC 100005/1 on 10.0.0.1
Root-NFS: Server returned error -13 while mounting /home/paulourada/timesys/atomus15w/rfs
VFS: Unable to mount root fs via NFS, trying floppy.
VFS: Insert root floppy and press ENTER
----------------------
```
This is what mountd reports in syslog:

```
----------------------
syslog
----------------------
Dec 15 18:59:28 taboul-ouradpa-vm mountd[2106]: refused mount request from 10.0.0.2 for /home/paulourada/timesys/atomus15w/rfs (/home/paulourada/timesys/atomus15w/rfs): unmatched host
----------------------
```
At one point, I started rpc.mountd with -d all option, and it gave me these messages when I tried to mount the root file system on the target:

```
----------------------
syslog
----------------------
Dec 15 18:25:07 taboul-ouradpa-vm mountd[2126]: check_default: access by 10.0.0.2 ALLOWED (cached) 
Dec 15 18:25:07 taboul-ouradpa-vm mountd[2126]: check_default: access by 10.0.0.2 ALLOWED (cached) 
Dec 15 18:25:07 taboul-ouradpa-vm mountd[2126]: MNT1(/home/paulourada/timesys/atomus15w/rfs) called 
Dec 15 18:25:07 taboul-ouradpa-vm mountd[2126]: refused mount request from 10.0.0.2 for /home/paulourada/timesys/atomus15w/rfs (/home/paulourada/timesys/atomus15w/rfs): unmatched host
----------------------
```

This is the result of ifconfig:

```
----------------------
Server ifconfig results
----------------------
eth0      Link encap:Ethernet  HWaddr 08:00:27:09:53:74  
          inet addr:10.0.2.15  Bcast:10.0.2.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe09:5374/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1300 (1.3 KB)  TX bytes:6876 (6.8 KB)

eth1      Link encap:Ethernet  HWaddr 08:00:27:bc:b8:a4  
          inet addr:10.0.0.1  Bcast:10.0.0.255  Mask:255.0.0.0
          inet6 addr: fe80::a00:27ff:febc:b8a4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:52082 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52198 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3145088 (3.1 MB)  TX bytes:29009392 (29.0 MB)
```

Since, after DHCP, the client reports its host name as 10.0.0.2, I’m thinking that something isn't getting resolved correctly, but I can't see how to point the server in the right direction. And the entry in dhcpd.conf specifies a host name, but somehow the target doesn't pick it up. Maybe it doesn't get transmitted back to the target, and it's only for server consumption? Since the root file system isn't mounted, there is no hostname file for the client to use, so it's kind of a chicken/egg problem?

I've searched the web for an answer, but I'm coming up with very little that applies to network booting. What little I did find on the subject related to what was in the hosts, hosts.allow and hosts.deny files in /etc. I've tried messing around w/those to no avail. There were several posts about the configuration of the /etc/exports file, and I've adjusted that as well. I've attached my configuration files for your reading enjoyment (yeah, right. :))

I've got to get this working this week so that I can deploy the VM to other developers.

Any ideas?

Thanks for listening.

Paul Ourada

---

