---
title: "Driver not Claiming Wirelesscard"
date: 2010-09-18
forum: Networking &amp; Wireless
---

### Post by Davan544 on 2010-09-18
Hello, I've been trying to get the wireless to work. The driver (ndiswrapper) is installed with the correct driver and it is running but has not taken control of the network card. So I don't know where to go from here other than to ask for help, thanks in advance.  Here is some info: ```
 dkorytov@ubuntu:~/ndiswrapper-1.56/utils$ ./ndiswrapper -l 
wg311v2 : driver installed     device (104C:9066) present 
dkorytov@ubuntu:~/ndiswrapper-1.56/utils$ sudo lshw -c network
   *-network UNCLAIMED
        description: Network controller
        product: ACX 111 54Mbps Wireless Interface
        vendor: Texas Instruments
        physical id: 9        
        bus info: pci@0000:02:09.0
        version: 00
        width: 32 bits
        clock: 33MHz
        capabilities: pm bus_master cap_list
        configuration: latency=64
        resources: memory:ff7fe000-ff7fffff memory:ff7c0000-ff7dffff
dkorytov@ubuntu:~/ndiswrapper-1.56/utils$ sudo ./ndiswrapper -a
104c:9066 wg311v2 Driver 'wg311v2' is already used for '104C:9066' 
dkorytov@ubuntu:~/ndiswrapper-1.56/utils$ lsmod 
 Module                  Size  Used by 
  ndiswrapper           184677  0 
  binfmt_misc             6587  1  ....
```

---

