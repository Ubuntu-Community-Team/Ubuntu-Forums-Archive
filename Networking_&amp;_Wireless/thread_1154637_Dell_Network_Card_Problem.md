---
title: "Dell Network Card Problem"
date: 2009-05-10
forum: Networking &amp; Wireless
---

### Post by david.paige on 2009-05-10
I am having a problem getting my Dell Optiplex 4500 network card working.  

I installed Ubuntu Jaunty using the Wubi installer.  I don't know if is contributing to the problem, but there it is.

When it boots and I click on the Network Manager, it shows auto eth0 disabled.  I have tried everything I can think of to get it working.  (I'm mostly a Windows person, with some AIX and Solaris background.)

The network card works perfectly within Windows, so there shouldn't be any defective hardware.  I am really perplexed, as I expected a generic network card to be configured out of the box.

Any ideas what might be wrong?

Perplexed at paiged dot fea dot st

---

### Post by cariboo on 2009-05-10
Could you open an Applicatioons-->Accessories-->Terminal and type:

```
sudo lshw -C network > network.txt
```

the above command will pipe all the details of your network card to a text file that you can easily copy to your windows partition. Could you paste the oputput from the command in your next post.

---

### Post by david.paige on 2009-05-10
Here is the output

 *-network DISABLED
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: eth0
       version: 10
       serial: 00:c0:a8:7f:bd:75
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 42:a3:ca:96:72:26
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

--------------
It seem strange that it won't work.  Realtek is a very common piece of hardware.

---

