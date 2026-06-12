---
title: "Gigabit ethernet DP55KG &quot;No Such Device&quot;"
date: 2011-10-30
forum: Networking &amp; Wireless
---

### Post by R.Bucky on 2011-10-30
I reinstalled Ubuntu 10.04.03 64-bit Server yesterday and found that my Giga integrated ethernet says the following when starting eth0. The MB is an Intel DP55KG. My previous installation of the same distro functioned out of the box without issue. 
```
SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
SIOCSIFBRDADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Failed to bring up eth0.
```

I have installed the ethernet driver from Intel for the specific MB, verified the new module in /var/lib/modules/..., restarted the server and nothing. I still receive the same error message. 

lshw shows that the NIC is still unclaimed even though I have installed the drivers successfully and verified their placement.

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
             resources: memory:e3200000-e321ffff memory:e3224000-e3224fff iopor$
```

Any thoughts on getting this NIC up and running?

---

