---
title: "Bridged ethernet interface problems"
date: 2008-12-21
forum: Networking &amp; Wireless
---

### Post by ThaddeusW on 2008-12-21
Ok I have a motherboard with two Ethernet interfaces and want to bridge them together. I took the following steps to create the bridge interface:

```

First I took down the primary interface. The secondary interface is not used.
#ifdown eth0

Next I created the bridge
#brctl addbr bridge0

Next I add both of the interfaces to the bridge:
#brctl addif bridge0 eth0
#brctl addif bridge0 eth1

Now I edited the interfaces file and added bridge0. Then I  bought the bridge0 interface up
#ifup bridge0

```

It appears to work because when I run ifconfig bridge0 it shows an address looks to be up and running. I tried to ping the rest of the network but no luck. I then tried to see if the bridge functions and connected a laptop to the second port and it didn't see the other side of the network. I was connected but no traffic was passed between the two adapters. 

I know it requires a kernel module but I read that if the module isn't loaded brctl fails to run. So I now have no idea. Any ideas?

---

### Post by albinootje on 2008-12-21
> **ThaddeusW said:**
> Ok I have a motherboard with two Ethernet interfaces and want to bridge them together. I took the following steps to create the bridge interface:
---cut---
I know it requires a kernel module but I read that if the module isn't loaded brctl fails to run. So I now have no idea. Any ideas?

Can you post the output of :
```

sudo route -n
sudo ifconfig -a
sudo lsmod |grep br

```

And can you check with "dmesg" to see any errors ?
And check for errors here : 
```

tail -f /var/log/syslog.0
tail -f /var/log/syslog
tail -f /var/log/kern.log.0
tail -f /var/log/kern.log

```

---

### Post by ThaddeusW on 2008-12-22
albinootje,

I did as you asked and I hope you can help me. 

route -n :
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 bridge0
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 bridge0 
```

ifconfig -a :
```
bridge0   Link encap:Ethernet  HWaddr 00:30:48:70:21:12  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:30:48:70:21:12  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Base address:0x3000 Memory:d3100000-d3120000 

eth1      Link encap:Ethernet  HWaddr 00:30:48:70:21:13  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Base address:0x3040 Memory:d3120000-d3140000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:844 errors:0 dropped:0 overruns:0 frame:0
          TX packets:844 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:50313 (49.1 KB)  TX bytes:50313 (49.1 KB) 
```

lsmod|grep br :
```
bridge                 55576  0   
```

tail -f /var/log/syslog :
```
Dec 22 00:05:21 Phobos postfix/smtpd[5945]: disconnect from localhost[127.0.0.1]
Dec 22 00:05:21 Phobos postfix/local[5949]: 71CC9E2D9F: to=<thaddeus@Phobos>, orig_to=<root@localhost>, relay=local, delay=0.08, delays=0.05/0.01/0/0.02, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Dec 22 00:05:21 Phobos postfix/qmgr[5417]: 71CC9E2D9F: removed
Dec 22 00:09:01 Phobos /USR/SBIN/CRON[6012]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Dec 22 00:09:06 Phobos kernel: [ 5006.966450] Bridge firewalling registered
Dec 22 00:09:46 Phobos kernel: [ 5047.043228] bridge0: Dropping NETIF_F_UFO since no NETIF_F_HW_CSUM feature.
Dec 22 00:12:07 Phobos kernel: [ 5187.471741] device eth0 entered promiscuous mode
Dec 22 00:12:07 Phobos kernel: [ 5187.471760] audit(1229922727.612:3): dev=eth0 prom=256 old_prom=0 auid=4294967295
Dec 22 00:12:09 Phobos kernel: [ 5189.011427] device eth1 entered promiscuous mode
Dec 22 00:12:09 Phobos kernel: [ 5189.011447] audit(1229922729.153:4): dev=eth1 prom=256 old_prom=0 auid=4294967295 
```

And dmesg also gives me the same stuff I see in the syslog. The only thing I might see being a problem is "Bridge firewalling registered" but I don't know what that means. The interfaces are showing a connection but its as if the bridge is not functioning at all.

---

### Post by albinootje on 2008-12-22
> **ThaddeusW said:**
> 
ifconfig -a :
```
bridge0   Link encap:Ethernet  HWaddr 00:30:48:70:21:12  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


I'm using a bridge on a machine, but only for one other NIC.
There the bridge shows its ip-address in ifconfig -a
Did you try : [code]sudo dhclient bridge0
```

See also here :
[http://ubuntuforums.org/showthread.php?t=402581](http://ubuntuforums.org/showthread.php?t=402581)
[http://ubuntuforums.org/showthread.php?t=31632](http://ubuntuforums.org/showthread.php?t=31632)

---

