---
title: "ssb?"
date: 2009-12-31
forum: Networking &amp; Wireless
---

### Post by SeaJayEmm on 2009-12-31
I have had great success getting wireless adapters to work with many different Linux distros. I have also helped countless people with getting their wireless adapters working with ubuntu. I love ubuntu (its on all my PCs). I have an old Dell Inspiron 8600 laptop with Ubuntu 9.04. I have a Linksys WPC54G pcmci wireless adapter. I am currently connected to my wireless network, however every time I reboot I have to rmmod bb4 and rmmod ssb, then remove and reinsert the adapter and it connects to my network. I have spent all day searching for a way to have it connect automatically upon boot but it seems to want to load the module=ssb on every boot. I have blacklisted bb4 as well as ssb and this keeps happening. Anyone know of a fix for this. Tonight I will upgrade to 9.10 and see what happens. Much thanks in advance for any help.

---

### Post by dmizer on 2009-12-31
The SSB module drives both broadcom wired and wireless. Since you said you also have the B44 module loading, I assume that you you also have a broadcom wired card (b43 is for wireless, and b44 is for wired).

That is why the two modules load persistently even though you have them in your blacklist.

I assume (also) that you are using ndiswrapper, which means that you'll probably have to edit your /etc/rc.local file so it looks like this:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
rmmod ndiswrapper
rmmod b44
rmmod ssb
modprobe ndiswrapper

exit 0

```

If that doesn't work, make sure that wireless is working and please post the output of this command:
```
lshw -C network
```

---

### Post by SeaJayEmm on 2009-12-31
Thanks for the reply. I am using ndiswrapper for the wireless card. I had already edited my /etc/r.local file, though it had a few extra things in it. It looks like this...
```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
rmmod b43
rmmod b44
rmmod ssb
rmmod ndiswrapper
modprobe ndiswrapper
modprobe ssb
modprobe b44
# By default this script does nothing.

exit 0
```

I see some difference, possibly the rmmods should go after "# By default this script does nothing." and before "exit 0".

The output of lshw -C network shows module=ssb for my wireless card at boot, after I input rmmod b44 and rmmod ssb and reinsert my wireless card lshw -C network shows module=ndiswrapper. I will try to edit my /etc/r.local file and see what happens and post back.

---

### Post by SeaJayEmm on 2009-12-31
Editing /etc/r.local did nothing. Here is the output of lshw -C network after boot, and the output of lshw -C network after I rmmod b44 and rmmod ssb. After boot it loads module=ssb for the wireless and after I rmmod b44 & ssb it shows module=ndiswrapper and the wireless works. I am looking to get it to load module=ndiswrapper at boot and have my wireless connect automatically. If not its not that big of a deal because I can get it to work by rmmod b44 & ssb. 
```

justin@dellmond:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:0c:f1:2f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=32 module=ssb multicast=yes
  *-network:1
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth1
       version: 04
       serial: 00:0c:f1:20:46:7d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 latency=32 maxlatency=34 mingnt=2 module=ipw2100 multicast=yes wireless=unassociated
  *-network
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 4e:f1:a3:1b:2f:f4
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
justin@dellmond:~$ rmmod b44
ERROR: Removing 'b44': Operation not permitted
justin@dellmond:~$ sudo rmmod b44
[sudo] password for justin: 
justin@dellmond:~$ rmmod ssb
ERROR: Removing 'ssb': Operation not permitted
justin@dellmond:~$ sudo rmmod ssb
justin@dellmond:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0 UNCLAIMED   
       description: Ethernet controller
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=32
  *-network:1
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth1
       version: 04
       serial: 00:0c:f1:20:46:7d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 latency=32 maxlatency=34 mingnt=2 module=ipw2100 multicast=yes wireless=unassociated
  *-network
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 03
       serial: 00:0c:41:a9:ed:36
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5a driverversion=1.53+Broadcom,04/09/2004, 3.40.6 ip=192.168.1.67 latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 4e:f1:a3:1b:2f:f4
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
justin@dellmond:~$ 


```

---

### Post by dmizer on 2009-12-31
Try running this in terminal:
```
sudo /etc/rc.local
```
See if your wireless comes up then.

---

### Post by SeaJayEmm on 2010-01-01
well i upgraded to 9.10 and all is well now. no conflicts with ndiswrapper and ssb. wireless connects at boot without having to rmmod b44 and ssb.

---

### Post by SeaJayEmm on 2010-01-06
Well I put Ubuntu 9.04 back on my laptop because 9.10 was very slow when it came to the internet. Again I was faced with moduel=ssb loading at boot for my wireless instead of ndiswrapper. I finally found the fix and it now loads module=ndiswrapper to control my wireless at boot and connects automatically. Before I had to remove my wireless pcmcia card, rmmod b44 and rmmod ssb, then reinsert my wireless pcmcia for it to connect. Here is how I got ndiswrapper to load at boot for my wireless. 
-edited /etc/modprobe.d/ndiswrapper and added 
alias pci:v000014E4d00004328sv*sd*bc*sc*i* ndiswrapper
install ssb /sbin/modprobe ndiswrapper; /sbin/modprobe --ignore-
-edited /etc/initramfs-tools/modules and added
ndiswrapper
-then ran sudo update-initramfs -u from terminal
If anyone is having a problem with ssb loading at boot to control your wireless try these steps. it worked for me

---

