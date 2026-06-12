---
title: "Asus EeePC 4G, Ubuntu 8.10 &quot;Intrepid Ibex&quot;, Atheros AR5007EG Wireless Network Adapter"
date: 2010-06-24
forum: Networking &amp; Wireless
---

### Post by Tuatar on 2010-06-24
Hello! I'm having some difficulty connecting to my wireless network . I'm using a Live Boot CD Ubuntu 8.10 on an Asus EeePC 4G, the wireless network adapter is an "Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)". I'm completely new to Linux, and the tutorials I've found on this forum and some other sites haven't really helped. 

So far, I've used ndiswrapper to install what I think is the correct driver from the Windows XP installation already on the laptop - the file I used is named "net5211.inf". Ndiswrapper accepted the file, and in the list of currently installed windows drivers it says the hardware is present. However, checking with "lshw -C network" shows that the wireless card is still UNCLAIMED. The LED lights on the laptop chassis indicate the wireless access card is enabled.

I'm not sure which parts of the following info are helpful, but I'll follow the recommendations for posting an issue and put it all here:

"iwconfig" gives:
```
lo   no wireless extensions
eth0 no wireless extensions
pan0 no wireless extensions
```


"sudo lshw -C network" returns:
```
ubuntu@ubuntu:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: L2 100 Mbit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: a0
       serial: 00:1e:8c:ec:8f:10
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl2 driverversion=2.0.4 firmware=L2 latency=0 link=no module=atl2 multicast=yes port=twisted pair
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 4a:20:02:51:c1:6b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

The kernel version is: 2.6.27-7-generic, i686.

Is there any other information I should post?

---

### Post by dtfinch on 2010-06-24
Getting the native driver (rather than ndiswrapper) installed and set up is mentioned at [https://help.ubuntu.com/community/EeePC/Fixes#Ath5k%20Driver](https://help.ubuntu.com/community/EeePC/Fixes#Ath5k%20Driver) , but I haven't tried that method personally.

---

### Post by pxr on 2010-06-24
Or try the image you'll find at

[http://7977home.com/700/](http://7977home.com/700/)

I uploaded it the other day for someone else who wanted a version of Ubuntu for an Eee pc 700.

Everything works 'out of the box'

I've used this on about 4 or 5 700's. This was the original eeebuntu (see eeebuntu.org) specifically compiled for these netbooks.

Just don't hit the 'upgrade to new distribution' button in Update manager, there's not enough space on a 4GB Eee pc drive to install the update files and it just locks out.

---

### Post by Tuatar on 2010-07-13
Thanks pxr and dtfinch for your help, but I'm going to leave ubuntu alone for the time being...I'll probably come back to it when XP burns out the ssd and I need to get a new one. Sorry about the long absence from this thread, I really appreciate your assistance :)

---

### Post by snowpine on 2010-07-13
Ubuntu 8.10 is obsolete and no longer supported in any way. If you try the current release (10.04) I bet your hardware will probably work out-of-the-box. :)

---

### Post by moore.bryan on 2010-07-13
> **snowpine said:**
> ubuntu 8.10 is obsolete and no longer supported in any way. If you try the current release (10.04) i bet your hardware will probably work out-of-the-box. :)

+1

---

