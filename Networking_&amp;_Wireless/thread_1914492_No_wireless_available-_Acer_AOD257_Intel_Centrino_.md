---
title: "No wireless available- Acer AOD257/ Intel Centrino Wireless N-100"
date: 2012-01-24
forum: Networking &amp; Wireless
---

### Post by texasmjl on 2012-01-24
I'm having an issue getting my system to recognize the fact that the wireless card exists.  Here are the basics of the system

Type: Acer Aspire One D257
Wireless card: Intel Centrino N-100
    When I type in lspci, this is what it reads 
        "02:00.0 Network controller: Intel Corporation Device 08ae"
    It also says there are no wireless connections
OS: I'm also using jolicloud (they said to use Ubuntu)

when I use the lshw -C network command I get this for what I believe is the wireless card
     ```
*-network UNCLAIMED
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:54000000-54001fff
     
```

Basically, I have been unable to use the wireless capabilities of my netbook when using jolicloud.  I also have Ubuntu on it, but the wireless works fine there.

Any help is greatly appreciated!

---

### Post by chow314 on 2012-06-25
gotta bump this, i would love to get jolicloud useable on my d257!

---

