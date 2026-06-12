---
title: "my wireless is not working"
date: 2009-11-26
forum: Networking &amp; Wireless
---

### Post by alotofloudcheese on 2009-11-26
My wireless is no longer working, I do not know what I did to mess it up. It was working plug and play. I have a hp dv7 laptop with 9.10. Below is all the info. Is the localname for the device that is not working in iwconfig a problem? any ideas? please help.
 
```
lshw -C network
 *-network               
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: [EMAIL="pci@0000:09:00.0"]pci@0000:09:00.0[/EMAIL]
       logical name: wmaster0
       version: 01
       serial: 00:26:5e:2c:ff:78
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:d1100000-d110ffff
 
 
dhcpclinet
[http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
dhclient: wmaster0: unknown hardware address type 801
 kernel: [   24.088421] ADDRCONF(NETDEV_UP): wlan0: link is not ready
 (wlan0): deactivating device (reason: 2). 
[http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)
 
 
iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
wmaster0  no wireless extensions.
wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
 
 
ifconfig
wlan0     Link encap:Ethernet  HWaddr 00:26:5e:2c:ff:78  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
wmaster0  Link encap:UNSPEC  HWaddr 00-26-5E-2C-FF-78-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

---

### Post by slymi2005 on 2009-11-26
My wireless stopped working today on both of my ubuntu computers but when I boot into windows 7 it works on both. This happens to me every now and then and it just comes back by itself after a while. Very annoying.

Not sure if you are experiencing the same problem as me but maybe someone else has some ideas.

---

### Post by newexperimentor on 2009-11-26
My wireless has never worked in Ubuntu 9.04, but does work fine in Vista.  Ubuntu  constantly asked for the password for networking.  No matter how many times I correctly enter it, I still can not get the wireless to work.

My prior posts have not elicited a solution.  Is there somewhere else we can go for solutions?

Like many other beginners, this is the kind of nonsense that drives people away.  As much as I loath Macro$shaft, their software works.  It may be grossly overpriced and have virtually no security, BUT IT WORKS.  Until Ubuntu consistently works without tweaking or forcing people into spending time in the fora hunting for solutions to problems that never should have arisen, it will remain a minority software and primarily a playtoy.

---

### Post by drpjkurian on 2009-11-27
> **alotofloudcheese said:**
> My wireless is no longer working, I do not know what I did to mess it up. It was working plug and play. I have a hp dv7 laptop with 9.10. Below is all the info. Is the localname for the device that is not working in iwconfig a problem? any ideas? please help.
 
```
lshw -C network
 *-network               
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: [EMAIL="pci@0000:09:00.0"]pci@0000:09:00.0[/EMAIL]
       logical name: wmaster0
       version: 01
       serial: 00:26:5e:2c:ff:78
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:d1100000-d110ffff
 
 
dhcpclinet
[http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
dhclient: wmaster0: unknown hardware address type 801
 kernel: [   24.088421] ADDRCONF(NETDEV_UP): wlan0: link is not ready
 (wlan0): deactivating device (reason: 2). 
[http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)
 
 
iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.
wmaster0  no wireless extensions.
wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
 
 
ifconfig
wlan0     Link encap:Ethernet  HWaddr 00:26:5e:2c:ff:78  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
wmaster0  Link encap:UNSPEC  HWaddr 00-26-5E-2C-FF-78-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

Hi
Please visit my thread to solve this issue. Your wireless card appears to be Atheros.
Madwifi is the robust driver for Atheros.
The thread is
[http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)

With regards
Dr Kurian

---

### Post by alotofloudcheese on 2009-11-27
Thanks for the sugesstion. Just did all that, and it still does not find any wireless networks. I tried it first with the original network manager did not auto connect to my network, and also did not see any wireless networks. So then I tried the manager you suggested that you use, and still does not find wireless networks. So I think I have some other problem other than drivers.

---

