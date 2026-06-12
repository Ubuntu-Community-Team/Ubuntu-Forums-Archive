---
title: "No network connection"
date: 2010-05-31
forum: Networking &amp; Wireless
---

### Post by pEkvo on 2010-05-31
I'm quite new to Ubuntu so apologies if I omit any necessary info.

I have been using Ubuntu 10.04 for a couple of weeks now and everything was going fine. I woke up this morning to find that my internet did not work anymore.

I noticed that my LED on the router for my PC did **not** come on. I changed UTP cable, no success, I changed port (to my brother's port which works because he has internet) but also no success.

I checked the physical link connection with:
```
ip link show eth0
```

which gave me:
```
eth0
2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN qlen 1000
    link/ether 00:19:66:ba:93:2d brd ff:ff:ff:ff:ff:ff

```

So the NO-CARRIER bit there is obviously disconcerting. I have tried DHCP and static IP addresses but I guess this is not something that will fix the NO-CARRIER issue?

The only thing I can think of is, when I opened Firefox this morning I went to the 'about:home' page and it said there had been updates/changes, could this have affected my driver? I think I can safely rule out a faulty cable or NIC. But the fact that no connection is being made is maybe because the driver is not doing its work?

Here is my NIC:
```
lspci
#2
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)

```

And
```

eth0      Link encap:Ethernet  HWaddr 00:19:66:ba:93:2d  
          inet addr:192.168.0.83  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:30 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:100 errors:0 dropped:0 overruns:0 frame:0
          TX packets:100 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8288 (8.2 KB)  TX bytes:8288 (8.2 KB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          inet6 addr: fe80::800:27ff:fe00:0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:59 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:15997 (15.9 KB)

```

---

### Post by puppywhacker on 2010-05-31
Your eth0 is UP in the ifconfig?? The realtek card you have is well supported by Linux. There have been zero packets being sent/received on eth0. Your network card maybe physically broken, like a pin bent.

for the NO-CARRIER check with "dmesg" if you have kernel messages also when you connect or disconnect the cable.
sudo mii-tool
sudo ethtool eth0

I think your card is a goner

---

### Post by pEkvo on 2010-05-31
> **puppywhacker said:**
> sudo mii-tool
This says 'eth0: link ok'

> **puppywhacker said:**
> sudo ethtool eth0
I tried this before but can't do this, I don't have the 'ethtool' which is why I used 'ip link show eth0'.

I'll see if I can find another NIC to test. Thanks.

---

### Post by puppywhacker on 2010-05-31
nevermind the ethtool, mii-tool is similar ... "link ok" means that the no-carrier should then be fixed somehow?? then my second guess (I typed but removed the text) is that you have a problem with your ip-routing? eth0 has 0 packets in and out, while vboxnet0 has over 50 packets transmitted, so it looked to me that your network is shooting the packets into the virtual world and not the real internet.

can you also print your routing table and ping the gateway
"route -n"

---

### Post by pEkvo on 2010-05-31
I found a different NIC, put it in the PCI slot, booted the computer and it didn't work immediately but at least the LED on my router was on.

So I deleted all the stuff I had in /etc/network/interfaces and just left the 'lo' and put the eth1 to dhcp. This worked and I had internet access....for about 15 minutes. I then read your post so I figured I might as well just plug the UTP cable back in my other NIC to follow your instructions and when I did the connection was immediately established, no more problems it seems.

Thanks for your help!

---

### Post by Iowan on 2010-05-31
Dunno if I'd mark the thread [SOLVED] yet - those fixes don't always *stay* fixed. There seem to be an increasing number of "worked last night, not this morning" threads...:confused:

---

