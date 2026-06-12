---
title: "Dell Mini 10 wireless failure on Ubuntu 9.10"
date: 2010-02-16
forum: Networking &amp; Wireless
---

### Post by jbeau10 on 2010-02-16
I am a newbie and I trying to setup my wireless connection on a Dell 1010 -mini 10 without any luck. I have listed below the information I was able to retrieve.Thanks,




1 ) Dell Mini 1010 laptop
2.)Wireless Brand, Model and Wireless Chipset:
 Code:03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01) 

3.)               ifconfig                 
                           
eth1      Link encap:Ethernet  HWaddr 00:22:5f:72:c5:62  
          inet6 addr: fe80::222:5fff:fe72:c562/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:140 errors:0 dropped:0 overruns:0 frame:6129
          TX packets:140 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15820 (15.8 KB)  TX bytes:20020 (20.0 KB)
          Interrupt:17 
                            


            
                                              
4,) $ iwconfig -eth1      IEEE 802.11  Nickname:"" 

           Access Point: Not-Associated
                                  
$ lsmod | grep "wlan_module_name"
 

 5 ) Kernel boot messages
 Code:22.768063]eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.91.9

6 ) Network configuration
 Code:
 

 $ sudo lshw -C network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 00:22:5f:72:c5:62
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:d8000000-d8003fff

 

 7 ) Scan for networks:
 Code: eth1      Interface doesn't support scanning.

8 ) Ubuntu Version:
 Code: Ubuntu 9.10

 

9 ) Kernel/architecture (including 32 vs. 64 bit): Code:2.6.31-19-generic i686

10 ) Restarting the network:
 Code:
 

 * Reconfiguring network interfaces...Ignoring unknown interface eth0=eth0.

---

### Post by efflandt on 2010-02-16
What is the output of **sudo lspci -v | grep wl**?  It should be something like this:

```
$ sudo lsmod | grep wl
wl                   1277380  0 
lib80211                7812  2 lib80211_crypt_tkip,wl
```

I recently had trouble getting wireless to work on an older Dell with BCM4311 from Ubuntu 9.10 that I am sure worked earlier, and I know worked automatically on a newer Dell 1545 with BCM4312.  But when I recently booted it on the older Dell, there was no wireless and no second eth interface (not even a wlan interface).  So I deactivated Broadcom STA driver, rebooted, then a wlan showed up, but that would not work.  So I reactived Broadcom STA, rebooted, and then the wireless connection already configured to connect automatically, did.

When it is working properly **sudo iwlist scan** should list access points within range.

---

### Post by superprash2003 on 2010-02-17
do try system->admin->hardware drivers

---

