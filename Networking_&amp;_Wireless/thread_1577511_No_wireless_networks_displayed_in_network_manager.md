---
title: "No wireless networks displayed in network manager"
date: 2010-09-19
forum: Networking &amp; Wireless
---

### Post by Levviathor on 2010-09-19
A couple of weeks ago my laptop's wifi started acting up, to the point that it didn't function.  When I click the nwManager icon to being up a list of available networks, it is empty.  If I try to create a new network, with the credentials of my modem, it appears to work, and asks for the password.  After I enter the password, it seems to work for about 30 seconds (much longer than normal) but then it prompts me again for the password.  This cycle continues indefinitely.

I'm running Karmic on a Dell i1525.  I'm not sure how to find out what wireless card I have.  I'd be happy to run commands and post the output, if that will help.

---

### Post by Levviathor on 2010-09-29
Bump.

---

### Post by dineshs on 2010-09-29
These links may help.
[http://ubuntuforums.org/showpost.php?p=9680300&postcount=14](http://ubuntuforums.org/showpost.php?p=9680300&postcount=14)
[http://ubuntuforums.org/showpost.php?p=9767936&postcount=11](http://ubuntuforums.org/showpost.php?p=9767936&postcount=11) 
If not please post the results of
```
sudo lshw -C network
```and```
iwconfig
```

---

### Post by Levviathor on 2010-10-14
I haven't done much screwing around with the modem settings, though that seems to have worked for the two linked posts.

However, my modem is using WEP, not WPA1 or WPA2 like the two posts.


Also, here's the output of the two commands.
```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          
vboxnet0  no wireless extensions.

pan0      no wireless extensions.


-----------


sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:56:9a:f2
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:28 memory:fe8fc000-fe8fffff ioport:de00(size=256)
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: eth1
       version: 01
       serial: 00:1f:3a:b8:6b:cb
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:fe7fc000-fe7fffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```

---

### Post by johnnytm on 2010-10-14
take a look at this post [http://ubuntuforums.org/showthread.php?t=1594577](http://ubuntuforums.org/showthread.php?t=1594577) there are a few links there that may be of some help to you. and that broadcom driver you are using is an old version. try updating it
```
       sudo apt-get --purge remove bcmwl-kernel-source
                 sudo apt-get install patch  
                 sudo apt-get install bcmwl-kernel-source 
```

---

