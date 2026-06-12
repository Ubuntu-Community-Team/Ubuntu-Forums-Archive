---
title: "unable to  activate ethernet"
date: 2010-03-12
forum: Networking &amp; Wireless
---

### Post by gobindsingh on 2010-03-12
Hellow, 

I have tried the command on ubantu workstation but it giving error :
# mii-tools
SIOCGMIIPHY on  'eth1' failed: operationsnot support.
no MII interface found. 

Please help me. Internet not working.
Can u tell me anonymous of kudzu command in fedora. 
Please help me to resole this problem,


Thankz,
Gobind Gill

---

### Post by chili555 on 2010-03-12
Is eth1 your ethernet interface? Usually, it's eth0. Please post:```
ifconfig
sudo lshw -C network
```Thanks.

---

### Post by gobindsingh on 2010-03-12
when i the follwing command ifconfig Its showing 2 ethernet 
# ifconfig 
eth1
......
.......
......
Eth2
...
...
.
.....


lo
....
....
...

dot means the information  it gives ip adderssand netmwsk etc.

but when i run this comand:
#dmesg|grep eth0
eth0:registered as PCnet/PCI II 79c970A
udev: renamed network eth0_rename to eth1


#dmesg|grep eth1
eth0:registered as PCnet/PCI II 79c970A
udev: renamed network eth1 to eth2
udev: renamed network eth0_rename to eth1
eth1: linkup 


same with eth2.

but when i run mii-tool its not showing link up.
please.


Yes i run that command :
#lshw -C network 
it executed but my problem is still there.

Please help

---

### Post by chili555 on 2010-03-12
> Yes i run that command :
#lshw -C network
it executed but my problem is still there.Was there no output? May we see it please?> dot means the information it gives ip adderssand netmwsk etc.Do you have a valid IP address? What are you attempting to do with *mii-tool*?

---

### Post by Iowan on 2010-03-12
```
sudo lshw -C network
``` sometimes gives slightly different results...

---

