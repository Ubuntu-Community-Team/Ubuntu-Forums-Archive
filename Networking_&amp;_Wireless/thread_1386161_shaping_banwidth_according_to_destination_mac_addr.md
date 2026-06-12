---
title: "shaping banwidth according to destination mac address"
date: 2010-01-20
forum: Networking &amp; Wireless
---

### Post by hosonno on 2010-01-20
hello everybody,
I'm trying to shape bandwidth using HTB method and filtering classes with destination mac address.
for this I've found two codes but none of them seem to filter bandwidth as i want (test with iperf)
can some one explain me the problem with theses codes 

code 1 
```

tc qdisc add dev eth0 root handle 1: htb
tc class add dev eth0 parent 1: classid 1:1 htb rate 1000kbit ceil 1000kbit
tc filter add dev eth0 parent 1: protocol ip prio 3 u32 match u16 0x0800 0xFFFF at -2 match u16 0xM4M5 0xFFFF at -4 match u32 0xM0M1M2M3  0xFFFFFFFF at -8 

```code2:
```

tc qdisc add dev eth0 root handle 1: htb
tc class add dev eth0 parent 1: classid 1:1 htb rate 1000kbit ceil 1000kbit
tc filter add dev eth0 parent 1: protocol 802_3 prio 3 u32 match u32 0xM0M1M2M3 0xffffffff at 0 match u32 0xM4M50000 0xffff0000 at 4 classid 1:1

```ps: mac address here is M0:M1:M2:M3:M4:M5

---

### Post by hosonno on 2010-01-21
it seem that the problem come from the fact that mac filtering can be applied only on bridge.

any one can confirm this ?


"The qdisc has a built-in classifier which assigns packets coming from or  sent to different machines to different classes. Either the MAC or IP and  either source or destination addresses can be used. **The MAC address can only  be used when the Linux box is acting as an ethernet bridge**, however. The  classes are automatically assigned to machines based on the packets seen."

source [http://lartc.org/lartc.html](http://lartc.org/lartc.html)

---

