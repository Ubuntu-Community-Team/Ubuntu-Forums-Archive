---
title: "establish wired network connection"
date: 2013-02-04
forum: Networking &amp; Wireless
---

### Post by qdott on 2013-02-04
I tried to install a recent kernal update that got hung up and wouldn't finish so I aborted the update.  After that I could no longer use $sudo modprobe b43 to initiate my wireless connection.  My strategy is to establish a wired connection, make sure all updates could be installed, and then try to establish the wireless connection again.  However, I cannot establish a wired connection.  I cannot type in any information into the Add wired network connection  in Network Connections: the boxes are gray and will not allow editing.  Help?!

Total beginner, so thanks for your patience.
12.04, Dell Inspiron 1520

---

### Post by Bucky Ball on 2013-02-04
*Thread moved to **Networking & Wireless**.*

Welcome to the forums. You should have more luck here. You've made it clear you're a beginner so we will be gentle. ;)

Any help you don't understand just ask for a simple explanation.

---

### Post by steeldriver on 2013-02-04
what do you mean exactly by "could no longer use $sudo modprobe b43 to initiate my wireless connection"?

if you are having sudo / authorization issues in general, then that could be why the nm-applet is not letting you do stuff either

---

### Post by qdott on 2013-02-04
I was using $sudo modprobe b43 to connect to my wireless router every time I booted ubuntu.  After I aborted an update that involved a kernal (it hung up indefinitely and I finally aborted it), the command $sudo modprobe b43 now hangs indefinitely in the terminal. My solution was to establish a wired connection and then properly install the update, but I'm having trouble even using Network Connections gui to get connected.

---

### Post by Bucky Ball on 2013-02-04
After the update have you checked 'Additional Drivers'? Is there anything b43 in there? Could you possibly give the output of this command:

```
sudo lshw -C network
```

You could also try installing:

b43-fwcutter
firmware-b43-installer

Restart and see what happens.

---

### Post by qdott on 2013-02-06
I have b43, b43-fwcutter-015, b43legacy in /lib/firmware.  

When I type "$sudo service network-manager start", the network icon appears in the tray, but no wireless signals are detected (even the one that is configured that used to work, and the one I'm currently connected to on a different computer).  When I type "$sudo modprobe b43" it just hangs.  When I plug in a DHCP ethernet cable no connections appear, either.

Here is what I get from "$sudo lshw -C network":

~$ sudo lshw -C network
[FONT=&quot]   *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=wl latency=0
       resources: irq:17 memory:fe8fc000-fe8fffff
  *-network UNCLAIMED
       description: Ethernet controller
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64
       resources: memory:fe5fe000-fe5fffff
[/FONT]

---

### Post by qdott on 2013-02-11
I got my wireless connected using the following:

sudo apt-get remove bcmwl-kernal-source

sudo modprobe b43

Thanks Bucky Ball and steeldriver for your patience with a newbie!

---

### Post by Bucky Ball on 2013-02-11
Excellent work. If all good, to help others, could you please perform the second suggestion in my signature below. Cheers.

---

