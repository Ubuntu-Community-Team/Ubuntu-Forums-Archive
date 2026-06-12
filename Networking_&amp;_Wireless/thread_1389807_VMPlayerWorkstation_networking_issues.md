---
title: "VMPlayer/Workstation networking issues"
date: 2010-01-24
forum: Networking &amp; Wireless
---

### Post by rmarc71 on 2010-01-24
I've been trying to get the new VMPlayer working (also tried VMWare workstation eval with the same issue).

There's no network.  None of the vmnet device files get created.

The vmnet module does get compiled and loads:

```

s$ lsmod | grep vmnet
vmnet                  43004  0 

 ls /dev/vmn*
ls: cannot access /dev/vmn*: No such file or directory


```

If I create the device files (as I found a suggestion somewhere in my searches) I don't get errors, but still doesn't seem to work:

```

#! /bin/sh -e
#Create device nodes for vmnet
sync
`/bin/mknod --mode=600 /dev/vmnet0 c 119 0`
`/bin/mknod --mode=600 /dev/vmnet1 c 119 1`
`/bin/mknod --mode=600 /dev/vmnet2 c 119 2`
`/bin/mknod --mode=600 /dev/vmnet3 c 119 3`
`/bin/mknod --mode=600 /dev/vmnet4 c 119 4`
`/bin/mknod --mode=600 /dev/vmnet5 c 119 5`
`/bin/mknod --mode=600 /dev/vmnet6 c 119 6`
`/bin/mknod --mode=600 /dev/vmnet7 c 119 7`
`/bin/mknod --mode=600 /dev/vmnet8 c 119 8`
`/bin/mknod --mode=600 /dev/vmnet9 c 119 9`
sync
exit 0

```

```

sudo  vmware-networks --start
Failed to initialize

```

The network icon on the vmplayer no longer has a red x on it if I do that, but still doesn't give me any love.

Once I have the device files created and start vmplayer I note that vmnet says it's being used:

```

lsmod | grep vmnet
vmnet                  43004  2 

```

I used vmware workstation years ago, and I seem to recall that vmnet created interfaces on the host system (vmnet0, vmnet1 and vmnet8)  But I see none of those in my ifconfig:

```

~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:10:5a:67:bf:15  
          inet addr:xx.xx.xxx.115  Bcast:xx.xx.xx.119  Mask:255.255.255.248
          inet6 addr: fe80::210:5aff:fe67:bf15/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:152268 errors:1 dropped:0 overruns:1 frame:2
          TX packets:140457 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:127171019 (127.1 MB)  TX bytes:40144634 (40.1 MB)
          Interrupt:17 Base address:0x2c00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:666 errors:0 dropped:0 overruns:0 frame:0
          TX packets:666 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:98897 (98.8 KB)  TX bytes:98897 (98.8 KB)


```

If I restart vmware I get:
```

 /etc/init.d/vmware restart
Stopping VMware services:
   VMware USB Arbitrator                                               done
   VM communication interface socket family                            done
   Virtual machine communication interface                             done
   Virtual machine monitor                                             done
   Blocking file system                                                done
Starting VMware services:
   VMware USB Arbitrator                                               done
   Virtual machine monitor                                             done
   Virtual machine communication interface                             done
   VM communication interface socket family                            done
   Blocking file system                                                done
   Virtual ethernet                                                   failed

```

Ubuntu 9.10 server
Linux ac-linux-04 2.6.31-17-generic-pae #54-Ubuntu SMP Thu Dec 10 17:23:29 UTC 2009 i686 GNU/Linux
VMWare Player 3.0 (VMware-Player-3.0.0-203739.i386.bundle)

Any help would be appreciated.

R. Marc

---

### Post by rmarc71 on 2010-01-24
I had another 9.10 box (running desktop, not server).

Installed the vmplayer there, no issues.  They are running different kernels, perhaps that's the issue.

R. Marc

---

