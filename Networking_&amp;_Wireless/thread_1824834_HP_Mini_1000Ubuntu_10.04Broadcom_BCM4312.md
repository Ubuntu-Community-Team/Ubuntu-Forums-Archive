---
title: "HP Mini 1000/Ubuntu 10.04/Broadcom BCM4312"
date: 2011-08-14
forum: Networking &amp; Wireless
---

### Post by samphire on 2011-08-14
The wireless on my HP Mini 1000 suddenly stopped working yesterday. I had previously had problems with the wireless when I first installed 10.04, but after installing a driver it was fine.

Immediately before it stopped working the screen froze up and the machine switched off as the battery had run down. The network manager icon says 'Networking disabled' and I can't get the wireless back using the wireless on/off button either. I hadn't installed anything new recently. I'm including the code asked for in the sticky.

I'm relatively inexperienced with Linux - can follow a tutorial, but I'm afraid I do need code spelled out for me. It's possible that this could be something really simple and embarrassing! Any help would be appreciated.


```
  jo@jo-laptop:~$ lspci -nn | grep Broadcom
  01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
    
``````
[FONT=&quot]jo@jo-laptop:~$ lsusb[/FONT]   [FONT=&quot]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]  
 [FONT=&quot]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]  
 [FONT=&quot]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]  
 [FONT=&quot]Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]  
 Bus 001 Device 003: ID 10f1:1a08  
   [FONT=&quot]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT]
``````
  
jo@jo-laptop:~$ ifconfig
    lo        Link encap:Local Loopback  
              inet addr:127.0.0.1  Mask:255.0.0.0
              inet6 addr: ::1/128 Scope:Host
              UP LOOPBACK RUNNING  MTU:16436  Metric:1
              RX packets:11316 errors:0 dropped:0 overruns:0 frame:0
              TX packets:11316 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:0 
              RX bytes:896904 (896.9 KB)  TX bytes:896904 (896.9 KB)
    
``````
  
jo@jo-laptop:~$ iwconfig
    lo        no wireless extensions.
     
   
  eth1      IEEE 802.11  Access Point: Not-Associated   
              Link Quality:5  Signal level:0  Noise level:0
              Rx invalid nwid:0  invalid crypt:0  invalid misc:0
    
``````
  
jo@jo-laptop:~$ lsmod | grep "wl"
    wl                   1959598  0 
    [FONT=&quot]lib80211                5046  2 lib80211_crypt_tkip,wl[/FONT]
``````
  
jo@jo-laptop:~$ dmesg | grep "wl"
    [    9.379445] wl: module license 'MIXED/Proprietary' taints kernel.
    [    9.682686] wl 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
    [FONT=&quot][    9.682708] wl 0000:01:00.0: setting latency timer to 64[/FONT]
``````
  
jo@jo-laptop:~$ sudo lshw -C network
    [sudo] password for jo: 
      *-network DISABLED      
           description: Wireless interface
           product: BCM4312 802.11b/g
           vendor: Broadcom Corporation
           physical id: 0
           bus info: pci@0000:01:00.0
           logical name: eth1
           version: 01
           serial: 00:24:2c:2d:d2:81
           width: 64 bits
           clock: 33MHz
           capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
           configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11bg
           resources: irq:16 memory:feafc000-feafffff
    
``````
  
jo@jo-laptop:~$ iwlist scan
    lo        Interface doesn't support scanning.
     
   
  [FONT=&quot]eth1      Interface doesn't support scanning.[/FONT]
``````
  
jo@jo-laptop:~$ sudo /etc/init.d/networking restart
     * Reconfiguring network interfaces...                                   [ OK ]
  
```

---

### Post by samphire on 2011-08-14
OK, it was something grimly simple. Sorry.

---

### Post by Megajoshthebest on 2011-08-14
Are you dual-booting?

---

