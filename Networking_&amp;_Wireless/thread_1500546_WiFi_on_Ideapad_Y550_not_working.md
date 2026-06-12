---
title: "WiFi on Ideapad Y550 not working"
date: 2010-06-03
forum: Networking &amp; Wireless
---

### Post by shankariyer on 2010-06-03
Installation was flawless. My WiFi router is up and I'm able to connect my Windows laptop. 

Once I login to Ubuntu, WiFi doesn't even start to scan and even if I go into 'network connections' to add the SSID manually, no luck. I just get the notification that I'm not connected, no other errors.

Here are few details, please help. Thanks.

```

root@user-laptop:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:5a:cd:d6:31  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:124 errors:0 dropped:0 overruns:0 frame:0
          TX packets:124 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9488 (9.4 KB)  TX bytes:9488 (9.4 KB)

root@user-laptop:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
root@user-laptop:~# lshw -C network
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:f4500000-f4503fff
  *-network
       description: Ethernet interface
       product: NetLink BCM5784M Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 10
       serial: 00:23:5a:cd:d6:31
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 firmware=sb v2.19 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:32 memory:f4600000-f460ffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:26:82:46:7a:20
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
root@user-laptop:~# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

root@user-laptop:~# /etc/init.d/network
networking                  network-interface-security  
network-interface           network-manager             
root@user-laptop:~# /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                              [ OK ] 
root@user-laptop:~# modprobe iwlagn
root@user-laptop:~# modprobe ndiswrapper



```

---

### Post by chili555 on 2010-06-03
Your Broadcom wireless card wants firmware in order to work. It's not included in a default install of Ubuntu because it's proprietary and some users object to any proprietary software. Not me; I just want my wireless card to work.

Can you please walk your laptop over to the router and hook up the ethernet cable and get a connection and then go to System > Administration > Hardware Drivers and activate your Broadcom card?

---

### Post by shankariyer on 2010-06-04
chili555, your suggestion was spot on! it works! Thanks much. (Again) You guys rock, in your super fast suggestions.

---

### Post by genfinch on 2010-07-20
I had the same problem (it's a recurring one after every upgrade or fresh install) and solved it like mentioned above. But this time, although ubuntu now detects the networks, it can't connect. It keeps asking for the password over and over, as though it is not correct. I've checked, double-checked and triple-checked the pw, it's correct, no typos, no nothing. Same pw works perfectly on our other laptop, too. Any ideas what might be wrong here?

---

### Post by shankariyer on 2010-07-20
I've that problem all the time. In my case, "after" I get to the desktop, it'd initially say its connected (to net), but actually its not. It's just connected to the router. 
So, one way to get connected has been - I just reboot the router and Ubuntu would loose connection and connect back, it works. Next, after it (erroneously) reports its connected, I still choose the access-point(SSID) and it'd prompt password and it connects fine.

This is not the ideal solution for you (or even me) that weirdness continues.

---

