---
title: "Two NIC's, one Ping (fresh install)"
date: 2009-07-10
forum: Networking &amp; Wireless
---

### Post by Drate on 2009-07-10
Networking/Install Problem: Using 8.04.2 Server, accross multiple machines, same result = with two NICs installed, I can recieve DHCP, and then recievce ONE ping reply, at which point I experience no further network traffic.

Every install done on machine with two nic's has the same result.  Removing secondary NIC solves problem, but I now have a condition that I NEED the secondary NIC.  This is going to be a production environment machine, any help would be appreciated.

---

### Post by iponeverything on 2009-07-10
> **Drate said:**
> Networking/Install Problem: Using 8.04.2 Server, accross multiple machines, same result = with two NICs installed, I can recieve DHCP, and then recievce ONE ping reply, at which point I experience no further network traffic.

Every install done on machine with two nic's has the same result.  Removing secondary NIC solves problem, but I now have a condition that I NEED the secondary NIC.  This is going to be a production environment machine, any help would be appreciated.

you are not providing enough information.

post the output of:

iptables -L -n
ifconfig
route -n

---

### Post by Drate on 2009-07-10
sudo iptables -L -n

Chain INPUT (policy ACCEPT)
target     prot opt source          destination

Chain FORWARD (policy ACCEPT)
target    prot opt source          destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source          destination

---------------------------

ifconfig

eth0     Link encap:Ethernet  HWaddr 00:24:81:xx:xx:xx
         inet addr:xxx.xxx.xxx.10  Bcast:xxx.xxx.xxx.255 Mask:xxx.xxx.xxx.0
         inet6 addr: xxxx::xxx:xxxx:xxxx:xxxx/64 Scope:Link
         UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
         RX packets:1257 errors:0 dropped:0 overruns:0 frame:0
         TX packets:140 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:109648 (107.0 KB)  TX bytes:12633 (12.3 KB)
         Interrupt: 18 Memory:f8000000-f8012100

lo       Link encap:Local Loopback
         inet addr:127.0.0.1  Mask:255.0.0.0
         inet6 addr:  ::1/128 Scope:Host
         UP LOOPBACK RUNNING  MTU:16436  Metric:1
         RX packets:16 errors:0 dropped:0 overruns:0 frame:0
         TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:0
         RX bytes:1344 (1.3 KB)  TX bytes:1344 (1.3 KB)

--------------------------------

route -n

Kernel IP routing table
Destination     Gateway     Genmask     Flags Metric Ref     Use Iface
xxx.xxx.xxx.0   0.0.0.0     xxx.xxx.xxx.0  U   0      0      0 eth0
0.0.0.0         xxx.xxx.xxx.1 0.0.0.0      UG  100    0      0   eth0

---

### Post by Drate on 2009-07-10
*NEW INFORMATION*
For the first time since noticing these problems I tried pinging another Ubuntu Linux machine. I get consistent replies from another Ubuntu Linux machine AND from a Barracuda Spam firewall (which, as I recall, runs on Linux), but still only ONE ping reply from Cisco firewalls and Windows machines.

Again, this ONLY happens on Ubuntu machines with TWO NICs. This does NOT happen on exactly the same hardware with only ONE NIC. I of course have tried moving the network cable around to verify I was on the correct NIC. And this new information proves that I AM on the right NIC, just receiving very strange results.

Also, I can ping 4.2.2.1 and Google IP addresses (which I presume are NOT Windows boxes) after having first pinged a local linux box, and I can ping a known Ubuntu Linux box across the internet.  So intra-net routing is not the issue.

This is just weird, but surely I'm not the first one to have the two-nic server problem?

---

### Post by gombadi on 2009-07-10
You say you have two nic's but the output of ifconfig only showed eth0.

Where is the other nic configured?  Can you -
```
cat /etc/network/interfaces
```

Also are you using public ip address or private ip ranges? Knowing what the first three numbers in your ip address would make it easier to find the problem. Have you configured both nics on the same network?

---

### Post by Crafty Kisses on 2009-07-10
Could be a couple of issues. Can I see the results of this command?
```
iptables -t nat -L
```

---

### Post by Drate on 2009-07-15
sudo iptables -t nat -L

Chain PREROUTING (policy ACCEPT)
target prot opt source destination

Chain POSTROUTING (policy ACCEPT)
target prot opt source destination
MASQUERADE all -- 192.168.122.0/24 anywhere

Chain OUTPUT (policy ACCEPT)
TARGET PROT OPT SOURCE DESTINATION

----------

The second NIC is not configured, just in.
I tried puppy linux and it does NOT have the problem... this problem only exists (so far) in Ubuntu while two nics are physically installed.

---

### Post by Drate on 2009-07-15
well, fun stuff... it's all working now.... after booting into puppy, seeing puppy not have a problem, and then booting back to ubuntu everything seems to be fine... i'm utterly confuzzled.  if anyone has a CLUE what was going on so i could reproduce, anticipate, and consistently resolve the issue please let me know.

---

