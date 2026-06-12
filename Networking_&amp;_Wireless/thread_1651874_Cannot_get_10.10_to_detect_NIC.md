---
title: "Cannot get 10.10 to detect NIC"
date: 2010-12-23
forum: Networking &amp; Wireless
---

### Post by jinxp1 on 2010-12-23
Hello,

I recently installed the 64bit version of 10.10 onto my machine, which runs on an Intel DP55WB motherboard. The on board NIC is not detected and I cannot get it to connect to a local wired connection. 

I ran sudo lshw and it returned (among other items)
```
        *-network UNCLAIMED
             description: Ethernet controller
             product: 82578DC Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi cap_list
             configuration: latency=0
             resources: memory:e0200000-e021ffff memory:e0224000-e0224fff ioport:2020(size=32)


```

Any suggestions on how to get 10.10 to recognize the NIC?

---

### Post by dineshs on 2010-12-24
Have you seen this?
[http://ubuntuforums.org/showthread.php?t=1390410&page=3](http://ubuntuforums.org/showthread.php?t=1390410&page=3)

---

### Post by jinxp1 on 2010-12-24
I took a look at that thread and it seems as if I'm experiencing a different problem from them. They can access the internet, but their speeds are lacking. However, my machine has no access to the internet.

The fix that they posted was an updated driver that addressed the 82598 and 82599-based Intel network connections; I'm using the 82578DC one. Nevertheless, I attempted to install their driver, but the make install command did not default to the /kernel/net/ixgbe location (I'm actually an ubuntu noobie :oops:) and I'm having issues getting that installed :(

Can you help me install that or suggest another solution specific to my problem?

---

### Post by dineshs on 2010-12-24
Did you install build-essential before *make install*?Without internet that would be difficult.Pl try
[http://ubuntuforums.org/showpost.php?p=2279820&postcount=2](http://ubuntuforums.org/showpost.php?p=2279820&postcount=2)

---

### Post by jinxp1 on 2010-12-24
Actually I gave up and installed 10.04 on the machine and networking is working flawlessly :)

Thanks for your help though!:)

---

