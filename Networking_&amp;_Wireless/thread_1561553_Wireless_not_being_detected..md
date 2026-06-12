---
title: "Wireless not being detected."
date: 2010-08-26
forum: Networking &amp; Wireless
---

### Post by tripmix on 2010-08-26
My wireless interface seem to be working properly, I used it just a few days ago. I have to type this in windows as any attempts to detect my wireless network router in ubuntu fails. The only thing I've installed since I last used it was a package called icetea something to get java working, it came with a bunch of dependencies. I think one of them was ndiswrapper, I know some people use this to get windows based wireless chips to work in linux. Could it somehow be interfering with my setup? Scanning for networks finds nothing nor do manually configuring wlan0 using iwconfig or editing the interface file. It's like my wireless network don't exist but I'm getting very good signal strength here in XP so it clearly is up and running as expected. I'm gonna try removing the icetea package now, in the mean while feel free to trow any suggestions you have my way.

EDIT: I've now removed the package called icedtea6-plugin and it's dependencies, the package I thought was ndiswrapper was actually xulrunner so ignore that. No change.

EDIT2: I ran a few commands to get some more info, here is the output:
```
  *-network DISABLED                                                                                                
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation                                                                                               
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:6b:a1:27:ae
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:32 memory:dc000000-dc001fff
```
```
wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
```

---

### Post by arubislander on 2010-08-26
Have you tried enabling your network. At times it gets disabled by itself, usually after waking up from hibernation.

Go to your network panel icon and right click. Make sure the Enable Networking and Enable Wireless options are checked.

---

### Post by tripmix on 2010-08-26
That seem to be what happened. I don't have a network panel icon with those options, maybe it's not in kde or just my box. Anyway I was able to fix it by editing this file "/var/lib/NetworkManager/NetworkManager.state" and restarting the network-manager afterwards. Thanks for the tip.

---

