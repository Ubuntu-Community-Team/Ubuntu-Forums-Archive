---
title: "Marvell Yukon 88E8053 sky2, sk98lin or skge?"
date: 2009-07-17
forum: Networking &amp; Wireless
---

### Post by daszorz on 2009-07-17
I'm in the process of setting up my ubuntu box as a router and i've added a Marvell Yukon 88E8053 pci-e Gigabit Ethernet card, it was working with the sky2 module but I've read that this is outdated and sk98lin should be used. Then I read skge should be used. I've managed to blacklist sky2 and I've tried to load both sk98lin and skge and failed. My question is, what module should I be using and how the hell do i load them? I've tried modprobe skge (because it's installed) and I've tried to install sk98lin to vary degrees of failure.

I'm running ubuntu server.

Anybody got any answers? Thanks.

---

### Post by daszorz on 2009-07-18
Can anybody help me?

---

### Post by daszorz on 2009-07-19
I'll try one more time...?

---

### Post by moe458 on 2009-09-02
> **daszorz said:**
> I'll try one more time...?

was there a resolution to this problem...anyone have an idea's how to install this crap !!:confused:

---

### Post by banchoff on 2009-09-15
Hi, 
  I have a similar card:

 Ethernet controller: Marvell Technology Group Ltd. 88E8050 PCI-E ASF Gigabit Ethernet Controller (rev 18)

   I'm using the sky2 driver, and randomly the card resets:

[970196.706605] sky2 eth1: hung mac 0:2 fifo 195 (194:189)
[970196.706611] sky2 eth1: receiver hang detected
[970196.706913] sky2 eth1: disabling interface
[970196.707227] sky2 eth1: enabling interface
[970199.917018] sky2 eth1: Link is up at 1000 Mbps, full duplex, flow control rx

  I've managed to replicate the error with a ping -f.
  Should I try another driver? recompile the one I'm using?

The system is a Hardy. And the problem is noticeable only if you look at the logs (I mean, there is no observable loss of connection when this happens).

Thanks for reading! 
Bye!

---

### Post by banchoff on 2009-10-15
Does anybody know if this problem is still present in the following ubuntu releases (8.10 and 9.04)?

---

### Post by wipmonkey on 2009-11-12
I have "Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 15)" sky2 has always failed me. I used the sk98lin driver with 9.04 with out any issues. I've upgraded to 9.10 and now I cannot compile the sk98lin driver.

it fails with
```

/tmp/Sk98IbJacTglOlfKBVoZDOeOR/all/skge.c: In function ‘sk98lin_init_device’:
/tmp/Sk98IbJacTglOlfKBVoZDOeOR/all/skge.c:624: error: ‘struct proc_dir_entry’ has no member named ‘owner’
/tmp/Sk98IbJacTglOlfKBVoZDOeOR/all/skge.c: In function ‘SkGeTestMsi’:
/tmp/Sk98IbJacTglOlfKBVoZDOeOR/all/skge.c:1963: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
include/linux/interrupt.h:116: note: expected ‘irq_handler_t’ but argument is of type ‘int (*)(int,  void *)’
/tmp/Sk98IbJacTglOlfKBVoZDOeOR/all/skge.c: In function ‘SkDrvEvent’:
/tmp/Sk98IbJacTglOlfKBVoZDOeOR/all/skge.c:6680: error: ‘struct net_device’ has no member named ‘priv’
/tmp/Sk98IbJacTglOlfKBVoZDOeOR/all/skge.c:7017: error: ‘struct net_device’ has no member named ‘priv’
make[2]: *** [/tmp/Sk98IbJacTglOlfKBVoZDOeOR/all/skge.o] Error 1
make[2]: *** Waiting for unfinished jobs....
make[1]: *** [_module_/tmp/Sk98IbJacTglOlfKBVoZDOeOR/all] Error 2
make: *** [sub-make] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic-pae'
+++ Compiler error

```

this has been an issue since at least 2006
I'm thinking about getting an "intel pwla8391gt" $27 pci card to solve this once and for all.

---

### Post by daszorz on 2009-12-20
Wow this thread came to life a few months later. I haven't done a thorough speedtest and I don't know how to look into error logs so I don't know if any of this is really causing a problem. Oh well, I have gigabit ethernet in my mind at least.

---

### Post by foresto on 2011-10-23
I don't know if it will work with the 88E8053 chip, but I just finished packaging the latest sk98lin driver (from August 2011) for Ubuntu Natty.  You can find my announcement post here:

[http://ubuntuforums.org/showthread.php?p=11382042#post11382042](http://ubuntuforums.org/showthread.php?p=11382042#post11382042)

---

