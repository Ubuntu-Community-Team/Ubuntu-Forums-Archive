---
title: "Wireless won't setup even when &quot;detected&quot;"
date: 2009-08-15
forum: Networking &amp; Wireless
---

### Post by DarknessEnemy on 2009-08-15
Hi everyone, I hope you can help me because Im getting bald from pulling my hair out of exasperation.

I followed the instructions in this thread [[http://ubuntuforums.org/showthread.php?t=575785]](http://ubuntuforums.org/showthread.php?t=575785]) And even when everything came out like the thread said: > (step)
4) sudo ndiswrapper -l

output should show:

netmw14x : driver installed
device ( 11AB:2A08 ) present


I try to setup my wireless but it cannot be detected. Like if it was off (yes, I checked, is on)... I go to the gtk interface from ndiswrapper it gives me a window in the beggining saying "Unable to see if hardware is present."  I close it and it says "Hardware present: Yes" but I still cannot setup my wireless.

HELP!

I hope you can help me and thank you in advance ^^.

---

### Post by superprash2003 on 2009-08-15
post output of
1)sudo iwconfig
2)lshw -C network

---

### Post by DarknessEnemy on 2009-08-15
```
xxx@xxx-laptop:~$ sudo iwconfig
[sudo] password for xxx:
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

xxx@xxx-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED
       description: Ethernet controller
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:e0:b8:e6:ba:d7
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.0.100 latency=0 module=r8169 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 7e:44:1f:7e:ca:77
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

---

### Post by DarknessEnemy on 2009-08-15
bump...

---

### Post by DarknessEnemy on 2009-08-15
Ok, I just solve it... I just needed to restart the computer... IM sorry for the inconvenience.

---

