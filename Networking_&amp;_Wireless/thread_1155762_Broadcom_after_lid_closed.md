---
title: "Broadcom after lid closed"
date: 2009-05-11
forum: Networking &amp; Wireless
---

### Post by mrxoliver on 2009-05-11
I've already posted this on the linuxquestions site without much success, so... 

I am having trouble with the wireless drivers on my HP 2133 since updating from kubuntu 8.06 to 9.04 . When I start the computer, the wireless works perfect, but every time the screen goes blank or I close the lid, the wireless stops working.

There is not a problem with the actual drivers that I can find so far, I am using the newer "wl" driver as recommended on some of the other threads, I've blacklisted "b43", ran the shell script that downloads the latest drivers etc. etc.

Here is some info that I've copied out from the terminal, keeping only the relevant bits.

Thanks!


BEFORE --> WORKING

```
~$ lspci

02:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)    

~$ lspci -v

02:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 02)
        Subsystem: Hewlett-Packard Company Device 1371                       
        Flags: bus master, fast devsel, latency 0, IRQ 24                    
        Memory at fdffc000 (64-bit, non-prefetchable) [size=16K]             
        Capabilities: <access denied>                                        
        Kernel driver in use: wl                                             
        Kernel modules: wl, ssb     

~$ ifconfig

eth1      Link encap:Ethernet  HWaddr 00:21:00:83:44:3c  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:ff:fe83:443c/64 Scope:Link              
          UP BROADCAST RUNNING MULTICAST  MTU:15~$ lspci --> the same

~$ lspci -v 

02:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev ff) (prog-if ff)
        !!! Unknown header type 7f
        Kernel driver in use: wl
        Kernel modules: wl, ssb

~$ ifconfig

eth1      Link encap:Ethernet  HWaddr 00:21:00:83:44:3c
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:ff:fe83:443c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2146 errors:0 dropped:0 overruns:0 frame:719
          TX packets:2202 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2099431 (2.0 MB)  TX bytes:431282 (431.2 KB)
          Interrupt:24 Base address:0xc000

~$ dmesg

[   14.849490] wl: module license '' taints kernel.                                                                                                                                 
[   14.863955] wl 0000:02:00.0: PCI INT A -> GSI 24 (level, low) -> IRQ 24                                                                                                          
[   14.863970] wl 0000:02:00.0: setting latency timer to 64
[   15.355681] eth1: Broadcom BCM4312 802.11 Wireless Controller 5.10.79.10
[   39.708067] eth1: no IPv6 routers present
```

AFTER --> NOT WORKING

```
~$ lspci --> the same

~$ lspci -v 

02:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev ff) (prog-if ff)
        !!! Unknown header type 7f
        Kernel driver in use: wl
        Kernel modules: wl, ssb

~$ ifconfig

eth1      Link encap:Ethernet  HWaddr 00:21:00:83:44:3c
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:ff:fe83:443c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2146 errors:0 dropped:0 overruns:0 frame:719
          TX packets:2202 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2099431 (2.0 MB)  TX bytes:431282 (431.2 KB)
          Interrupt:24 Base address:0xc000

~$ dmesg --> the same
```

---

### Post by Tenn lynx on 2009-05-11
same thing here on a HP pavilion dv7 laptop using intel PRO 5100 wireless

drops when idle or lid closed.

I think this is all probably related:
[http://ubuntuforums.org/showthread.php?t=1146367](http://ubuntuforums.org/showthread.php?t=1146367)

[http://ubuntuforums.org/showthread.php?t=1155461](http://ubuntuforums.org/showthread.php?t=1155461)

except maybe it's not "random"...

---

