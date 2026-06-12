---
title: "Server networking issue: SIOCSIFADDR: No such device"
date: 2010-11-20
forum: Networking &amp; Wireless
---

### Post by Whelk on 2010-11-20
I've just installed a 10.10 server, but it can't seem to see the network.  It's hooked up via CAT-5 cable that's confirmed to work on other machines. Pinging gives an error stating "connect: Network is unreachable" 

lspci shows an ethernet controller:

> 
02:0b.0 Ethernet controller:  National Semiconductor Corporation DP83820 10/100/1000 Ethernet Controller


Trying a network restart or ifup results in the following:

> 
SIOCSIFADDR: No such device
eth0: ERROR while gettign interface flags: No such device
SIOCSIFNETMASK: No such device
SIOCSIFBRDADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device


/etc/network/interfaces is as follows:

> 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 192.168.1.110
        netmask 255.255.255.0
        network 192.168.1.0
        broadcast 192.168.1.255
        gateway 192.168.1.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.1.1
        dns-search ARDA


/etc/udev/rules.d/70-persistent-net.rules is as follows:

> 
# PCI device ox100b:0x0022 (ns83820)
SUBSYSTEM=="net", ACTION="add", DRIVERS=="?*", ATTR{address}=="00:09:5b:22:d3:35", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


The address matches that printed on the card.

Any ideas why I keep getting all those "No such device" errors when lspci sees the Ethernet controller?

---

### Post by CharlesA on 2010-11-20
What does this return:

```
ifconfig
```

Check [here]("http://muffinresearch.co.uk/archives/2008/07/13/vmware-siocsifaddr-no-such-device-eth0-after-cloning/") as well.

---

### Post by Whelk on 2010-11-20
ifconfig:

```

lo      Link encap:Local Loopback
        inet addr:127.0.0.1 Mask:255.0.0.0
        inet6 addr: ::1/128 Scope:Host
        UP LOOPBACK RUNNING  MTU:16436 Metric:1
        RX packets:331 errors:0 dropped:0 overruns:0 frame:0
        TX packets:331 errors:0 dropped:0 overruns:0 carrier:0
        collisions:0 txqueuelen:0
        RX bytes:60505 (60.5 KB) TX bytes: 60505 (60.5 KB)

```

---

### Post by CharlesA on 2010-11-20
Did the link I posted help any? It seems like a mismatch in the MAC causes the card not to be detected.

---

### Post by Whelk on 2010-11-20
Moving the rules file didn't cause a new one to be generated.  I tried a few things mentioned in the comments, and those didn't seem to work either.  The MAC address does match that on the card, so I don't know that that's the issue anyway.

Another problem is that the system seems to randomly freeze up for a minute or so, then generate a warning and restore activity.  I think I'm just going to call this old box done.  Thanks for looking at it, though.

---

### Post by CharlesA on 2010-11-20
Given that it's behaving strangely, perhaps it's the mobo that's going out?

I've seen that happen a few times before it bites the dust.

---

