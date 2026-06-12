---
title: "NFS autofs freezes client after a while"
date: 2020-04-20
forum: MINT
---

### Post by c902 on 2020-04-20
Hello,


I use NFS to connect to my server. When accessing from client 1, the client gets slower file access after a while and the sometimes it freezes completely. After a reboot everything seems fine again. On client 2 everything is fine.


Server: Debian GNU/Linux 9.12 (stretch)
in /etc/exports
```
/mnt/md0/chris  10.0.0.0/24(rw,sync,no_subtree_check)
```


Client 1: Linux Mint 19.3 Tricia (Ubuntu Bionic)
Client 2: Linux Mint 19 Tara (Ubuntu Bionic)
both use autofs to connect to the NFS share
in /etc/auto.master
```
/net    -hosts    --timeout=60
```


```
root@client1:~# cat /var/log/syslog | grep -i automount
Apr 19 21:29:21 client1 kernel: [    4.001453] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
Apr 19 21:29:27 client1 systemd[1]: Starting Automounts filesystems on demand...
Apr 19 21:29:27 client1 systemd[1]: Started Automounts filesystems on demand.
```


do you have any hint what could be wrong here, or where to look?


Thanks, Chris

---

### Post by TheFu on 2020-04-20
Debian and Mint are not Official Ubuntu flavors. 

I’ve never used NFS with either let me see what jumps out.
a) looks like you are using SW-RAiD?  How is the performance on the host to that storage?  Just trying to exclude stuff.
b) use async, not sync if you want better performance.
c) what are the autofs mount options?
d) have you excluded the networking already?  Does iperf3 show no network performance issues between each client and the server?  All wired networking?  All intel NiCs?

My autofs options, an example mount:
```
/d/D1                -fstype=nfs,proto=tcp,intr,rw,async                   istar:/d/D1
```

My exports file on the server (Ubuntu 16.04):
```
/d/D1   lubuntu(rw,async,root_squash) romulus(rw,root_squash,async) hadar(rw,root_squash,async) 
```
i don't do subnet-wide authorizations.

The mount:
```
istar:/d/D1                       nfs4  3.5T  3.5T   16G 100% /d/D1
```

Anything interesting in the nfstats?

BTW, i've not seen any performance issues over time 1 day, 1 month or 10 months of uptime.

---

### Post by Tadaen_Sylvermane on 2020-04-20
I had a fair number of issues when I was trying to use autofs inside LTSP pxe boot machines. Problems getting the chroot set up. Switched to systemd via fstab and haven't looked back. Admittedly I didn't really get autofs or research my issues too much.

```
nfs.mylan.home:/snapraid/pool /snapraid/pool nfs defaults,noauto,x-systemd.automount,x-systemd.timeout=30 0 0
```

Whether or not one likes it, systemd is here to stay. I don't however know how much you can fine tune it like autofs. But for basic use it's to easy.

---

### Post by slickymaster on 2020-04-21
Thread moved to **MINT** for a better fit

---

### Post by TheFu on 2020-04-21
> **Tadaen_Sylvermane said:**
> I had a fair number of issues when I was trying to use autofs inside LTSP pxe boot machines. Problems getting the chroot set up. Switched to systemd via fstab and haven't looked back. Admittedly I didn't really get autofs or research my issues too much.

```
nfs.mylan.home:/snapraid/pool /snapraid/pool nfs defaults,noauto,x-systemd.automount,x-systemd.timeout=30 0 0
```

Whether or not one likes it, systemd is here to stay. I don't however know how much you can fine tune it like autofs. But for basic use it's to easy.

The systemd-automount has been solid in my testing here the last few months. I doubt the underlying code involved is any different between autofs and systemd-automount. These are just configuration and management layers.

---

### Post by c902 on 2020-04-23
Hello,

thanks for all the input so far. Here are some answers to your questions or recommendations:
[LIST]
[*]yes, I use SW raid on the server, performance is fine, no problem when accessing from the other client
[*]I switched to async, thanks
[*]autofs mount options are in the original mail
[*]iperf3 shows 60MByte/s, client1 (the one with the problem) uses wired access, client2 (without problems) is connected via WiFi
[/LIST]

do you have any further suggestions?

Thx, Chris

---

### Post by TheFu on 2020-04-23
60MByte/s is terrible performance. Terrible.

For example, on 3 different systems here, all GigE connected except the last one:

```
[  4]   0.00-10.00  sec   626 MBytes   525 Mbits/sec                  receiver
```
10 yr old Core i5.

```
[  4]   0.00-10.00  sec   519 MBytes   435 Mbits/sec                  receiver
```
5 yr old Pentium G.

```
[  6]   0.00-10.00  sec  33.2 **GBytes**  28.5 Gbits/sec                  receiver
```
KVM virtual machine running on the "server" HW. Not really a fair test.

The "server" is a Ryzen 5.  All connections are wired.

Just for fun, used a Raspberry Pi3 (100 base-tx) as a client:
```
[  4]   0.00-10.00  sec   112 MBytes  94.2 Mbits/sec                  receiver
```

Definitely fix the network. That's where the issue is, most likely. Cannot say whether the SW-RAID is slow since no facts were provided. 
[https://arstechnica.com/gadgets/2020/02/how-fast-are-your-disks-find-out-the-open-source-way-with-fio/](https://arstechnica.com/gadgets/2020/02/how-fast-are-your-disks-find-out-the-open-source-way-with-fio/) might be helpful.

Nothing about nfsstat?
```
Server rpc stats:
calls      badcalls   badclnt    badauth    xdrcall
826773     0          0          0          0       

```
Any bad* on yours?

---

### Post by c902 on 2020-04-25
first I want to stress that I was reporting M**Byte**/sec not M**bit**/sec, so 60MByte/sec is not so bad, but after having the client online for several hours most certainly lead to a system slow down or even freeze.

nevertheless I followed your advice to look into the network and tweaked a little bit around to measure transfers between server, client1 and client2, and compared speed tests between server and clients to get a clue where the bottleneck could be. So I narrowed it down to the connection between client1 and the router. As client1 has 2 NICs I switched to the other one - and solved the problem. I observed no strange behaviour today when working on client1 for several hours with regular server access.

So these are the results (this time in Mbit/sec)
```
[  4]   0.00-10.00  sec  1.09 GBytes   934 Mbits/sec                  receiver
```

So I will set this thread to closed and thank you all for your support.

---

### Post by TheFu on 2020-04-25
I’d assumed you used the provided output from iperf, which is Mbps.  Disk and network performance is typically reported in bps by the monitoring tools, not Bps. The only people using bytes are software weenies. Sorry.   i used Bps when i was a SW weenie.

When looking at raw network performance, there seems to be a relationship between the age and cheapness of the network card.  intel PRO/1000 has always been 980 Mbps or better, but those cheap cards using the skge and marvell and realtek chips from 10+ yrs ago do really poorly.  i have a mix of those around here, but the new builds all get intel network chips.  it really does matter.

Have a cheap USB3-to-GigE adaptor for laptops which does very well:
```
[  4]   0.00-10.00  sec  1.07 GBytes   921 Mbits/sec                  receiver
```

Did you ever look at the other stuff suggested?

---

