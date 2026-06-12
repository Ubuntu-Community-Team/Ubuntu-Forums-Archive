---
title: "Network Manager doesn't claim wireless after uninstall NDISWrapper"
date: 2009-11-19
forum: Networking &amp; Wireless
---

### Post by discumax1 on 2009-11-19
NM was working fine on all wireless expect WPA2-PSK, then I followed this lovely guide [http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847) thinking NDISWrapper might solve this problem, it DIDN'T. Now that I have uninstalled NDIS, NM will not claim my wireless card back.... I tried to revert all the step in that guide, 

I removed the blacklist in [php]sudo gedit /etc/modprobe.d/blacklist.conf[/php]but this only helped NM claiming LAN, the only thing I couldn't undo was 

[php]sudo update-initramfs -k all -u [/php] in step 3, I have no idea what it does, only 3 weeks new to ubuntu. Typing lshw -C Network returned the following

[php]*-network UNCLAIMED     

       description: Network controller

       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection

       vendor: Intel Corporation

       physical id: 0

       bus info: pci@0000:02:00.0

       version: 61

       width: 64 bits

       clock: 33MHz

       capabilities: bus_master cap_list

       configuration: latency=0

       resources: memory:f4000000-f4001fff

  *-network

       description: Ethernet interface

       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller

       vendor: Realtek Semiconductor Co., Ltd.

       physical id: 0

       bus info: pci@0000:08:00.0

       logical name: eth0

       version: 01

       serial: 00:1e:68:14:fb:32

       width: 64 bits

       clock: 33MHz

       capabilities: bus_master cap_list rom ethernet physical

       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=192.168.1.102 latency=0 multicast=yes

       resources: irq:29 ioport:c000(size=256) memory:f8000000-f8000fff memory:c0000000-c001ffff(prefetchable)[/php]I also tried replacing NM with WICD, no luck, so I switched back. Anyone have input on this?

Oh, a side question, I have a locked folder name ndiswrapper-1.55 on my desktop, how do I delete this? gksudo nautilus showed nothing my desktop (empty)

---

### Post by discumax1 on 2009-11-19
help :confused:

---

### Post by blackienl on 2009-11-19
Try installing wicd and see if that takes it. From my expierence it works alot better than NM with my Intel Pro Wireless.


**Edit**
**Sorry, didnt see the bottom of your post where you already tried this.**

---

### Post by discumax1 on 2009-11-19
ya, it seems that I have done something that blocks all other application but NIDSWraper (which by the way didn't work although it claimed it), so I'm pretty sure its not the program itself, but something else

---

### Post by pytheas22 on 2009-11-19
You shouldn't need ndiswrapper for this card (and I think it actually won't work anyway with that particular kind of wireless card).  There should already be a driver (the iwl4965 module) pre-installed in Ubuntu that will work for it.  If you blacklisted iwl4965, remove that line from your /etc/modprobe.d/blacklist.conf file if you haven't already.  Then please run the following commands and post the output:
```

sudo rmmod ndiswrapper
sudo rmmod iwl4965
sudo modprobe iwl4965
cat /etc/modprobe.d/blacklist*
sudo iwlist scan
dmesg | grep -ie radio -e iwl -e wlan
cat /etc/issue
```

---

### Post by discumax1 on 2009-11-21
wow, worked like a charm!!

I got to the 3rd command line, then it auto detected and connected to wireless like b4! Thanks a bunch
sudo modprobe iwl4965

---

### Post by discumax1 on 2009-11-21
[SIZE=4]unfortunately, the wireless wouldn't auto start after reboot, I'd have to manually do step 3 again to give a kick start, any idea?
Also, , I have a locked folder name ndiswrapper-1.55 on my desktop, how do I delete this? gksudo nautilus showed nothing on my desktop (empty)[/SIZE]

---

### Post by pytheas22 on 2009-11-22
Try running this command once:
```

echo iwl4965 | sudo tee -a /etc/modules
```

and from then on your wireless should work automatically after a reboot without the need for typing anything manually.  If this doesn't solve it, let me know and we can try a different solution.

---

