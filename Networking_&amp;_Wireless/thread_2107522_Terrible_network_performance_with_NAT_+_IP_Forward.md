---
title: "Terrible network performance with NAT + IP Forwarding"
date: 2013-01-22
forum: Networking &amp; Wireless
---

### Post by MikeBenza on 2013-01-22
Hello,

I have a Ubuntu server (v11.10) that acts as a NAT for some clients.  The short version of the problem is that when a client is behind the NAT it can download at about 1MBps and when it's not behind the NAT (in a different port on the same switch as the public side of the NAT) it gets about 100MBps on a good day, 60MBps on a bad day.


Here's the physical setup:
NAT machine: dc**g**w-s1
Clients: dcw-s13...dcw-s16
The public side of the NAT (eth0) is connected to a gigabit network.  The NAT machine itself can also download about 100MBps / 60MBps during peak hours.  The private side of the NAT is eth1.  It's a gigabit ethernet NIC.  The private side connects to a [Netgear GS 116 Gigabit Switch](http://www.netgear.com/service-provider/products/switches/unmanaged-desktop-switches/GS116.aspx) on the last port.  The 4 clients are connected to the first four ports on the switch.  When all the clients are idle -- not downloading anything -- one client can only get 1MBps download from outside the NAT and about 8MBps from the NAT itself.  I'd like to increase those speeds.  

Here's dmesg | grep eth:
```

[    1.575969] e1000e 0000:00:19.0: eth0: (PCI Express:2.5GT/s:Width x1) 14:da:e9:39:08:fd
[    1.575974] e1000e 0000:00:19.0: eth0: Intel(R) PRO/1000 Network Connection
[    1.576020] e1000e 0000:00:19.0: eth0: MAC: 10, PHY: 11, PBA No: FFFFFF-0FF
[    1.685251] e1000 0000:08:01.0: eth1: (PCI:33MHz:32-bit) 00:1b:21:47:56:0a
[    1.685255] e1000 0000:08:01.0: eth1: Intel(R) PRO/1000 Network Connection
[    7.586792] e1000: eth1 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: RX/TX
[    7.587608] ADDRCONF(NETDEV_UP): eth1: link is not ready
[    7.590099] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[    7.793750] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   12.841054] e1000e: eth0 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[   12.841791] ADDRCONF(NETDEV_CHANGE): eth0: link becomes read

```

And here are my /etc/rc.local file for setting up the forwarding:
```

# NAT for clients.
/sbin/iptables -P FORWARD ACCEPT
/sbin/iptables --table nat -A POSTROUTING -o eth0 -j MASQUERADE

# Forward ports for RDP connections
for i in $(seq 50 1 150)
do
        /sbin/iptables -t nat -A PREROUTING -p tcp -i eth0 --dport $((31000 + $i)) -j DNAT --to 192.168.1.$i:8888
        /sbin/iptables -t nat -A PREROUTING -p tcp -i eth0 --dport $((21000 + $i)) -j DNAT --to 192.168.1.$i:3389
done

exit 0

```

I do need a NAT because IT policy requires that Windows machines without virus scanning programs be behind a NAT to prevent incoming connections.  They don't run virus scan because the computers are for testing the performance of our software.

Does anyone have any idea how I can improve the network performance for the machines behind the NAT?

---

### Post by SeijiSensei on 2013-01-22
The iptables kernel code is very efficient.  It is very unlikely to be the source of your problem.  I'd look to the hardware and the switch.

---

### Post by Doug S on 2013-01-23
> **SeijiSensei said:**
> The iptables kernel code is very efficient. It is very unlikely to be the source of your problem. I'd look to the hardware and the switch.Seiji, I'm not sure I agree. I mean I agree that the iptables kernel code is very efficient, as it should be. However there are 202 prerouting rules to go through, which has got to take a toll. My only real reference is my older, cpu starved, server which I always noticed was pretty sensitive to any additional iptables rules.
 
Mike: I wonder if you could to a test? Take out all, or most, of the prerouting rules and see if it makes a difference. I tried on my test server (not the pathetic one), but it's not really set up for packets to traverse the nat table.
 
Edit: I did an experiment via the INPUT chain. It took me a lot of rules in the input chain to bog down file trnasfer rates. With several hundreds of rules, the rate degradation was unnoticable. With 64,009 rules the degradation was very very noticable.

---

### Post by MikeBenza on 2013-05-15
The problem ended up being this bug: [843709]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/843709").  I bought a PCI-E gigabit network card and everything has been working correctly (i.e. full speed) since.

---

