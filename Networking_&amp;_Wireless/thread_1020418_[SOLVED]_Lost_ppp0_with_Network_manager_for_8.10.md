---
title: "[SOLVED] Lost ppp0 with Network manager for 8.10"
date: 2008-12-24
forum: Networking &amp; Wireless
---

### Post by oygle on 2008-12-24
Have Network manager for Intrepid installed, and used to have ppp0, however after installing a wireless broadband connection through Network manager, the ppp0 interface has gone.  :(

It's nowhere to be found in the network, and the network manager applet is saying ..

> Waiting for user uthentication on device 'ttyUSB0' ..

That divice should be configured as ppp0 , as it is a USB dongle, a wireless modem - E169 model

Here is what syslog says when I try to connect to the broadband wireless ..

> Dec 24 21:16:03 ****** NetworkManager: <info>  Activation (ttyUSB0) starting connection 'Optus 3G' 
Dec 24 21:16:03 ****** NetworkManager: <info>  (ttyUSB0): device state change: 3 -> 4 
Dec 24 21:16:03 ****** NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Dec 24 21:16:03 ****** NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled... 
Dec 24 21:16:03 ****** NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started... 
Dec 24 21:16:03 ****** NetworkManager: <debug> [1230113763.662364] nm_serial_device_open(): (ttyUSB0) opening device... 
Dec 24 21:16:03 ****** NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete. 
Dec 24 21:16:03 ****** NetworkManager: <info>  (ttyUSB0): powering up... 
Dec 24 21:16:03 ****** NetworkManager: <info>  Registered on Home network 
Dec 24 21:16:03 ****** NetworkManager: <info>  Associated with network: +COPS: 0,2,"50502",2 
Dec 24 21:16:03 ****** NetworkManager: <info>  Connected, Woo! 
Dec 24 21:16:03 ****** NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) scheduled... 
Dec 24 21:16:03 ****** NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) starting... 
Dec 24 21:16:03 ****** NetworkManager: <info>  (ttyUSB0): device state change: 4 -> 5 
Dec 24 21:16:03 ****** NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Dec 24 21:16:03 ****** NetworkManager: <info>  Starting pppd connection 
Dec 24 21:16:03 ****** NetworkManager: <debug> [1230113763.943208] nm_ppp_manager_start(): Command line: /usr/sbin/pppd nodetach lock nodefaultroute ttyUSB0 noipdefault usepeerdns lcp-echo-failure 0 lcp-echo-interval 0 ipparam /org/freedesktop/NetworkManager/PPP/12 plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so 
Dec 24 21:16:03 ****** NetworkManager: <debug> [1230113763.944371] nm_ppp_manager_start(): ppp started with pid 6931 
Dec 24 21:16:03 ****** NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) complete. 
Dec 24 21:16:03 ****** pppd[6931]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
Dec 24 21:16:03 ****** pppd[6931]: pppd 2.4.4 started by root, uid 0
Dec 24 21:16:03 ****** pppd[6931]: Using interface ppp0
Dec 24 21:16:03 ****** pppd[6931]: Connect: ppp0 <--> /dev/ttyUSB0
Dec 24 21:16:03 ****** NetworkManager: <info>  (ttyUSB0): device state change: 5 -> 6 
Dec 24 21:16:03 ****** NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Dec 24 21:16:06 ****** pppd[6931]: CHAP authentication succeeded
Dec 24 21:16:06 ****** pppd[6931]: CHAP authentication succeeded
Dec 24 21:16:06 ****** NetworkManager: <info>  (ttyUSB0): device state change: 6 -> 7 
Dec 24 21:16:06 ****** NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Dec 24 21:16:11 ****** pppd[6931]: Modem hangup
Dec 24 21:16:11 ****** pppd[6931]: Connection terminated.
Dec 24 21:16:11 ****** NetworkManager: <info>  (ttyUSB0): device state change: 7 -> 9 
Dec 24 21:16:11 ****** NetworkManager: <debug> [1230113771.603030] nm_serial_device_close(): Closing device 'ttyUSB0' 
Dec 24 21:16:11 ****** NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Dec 24 21:16:11 ****** NetworkManager: <info>  Marking connection 'Optus 3G' invalid. 
Dec 24 21:16:11 ****** NetworkManager: <info>  Activation (ttyUSB0) failed. 
Dec 24 21:16:11 ****** NetworkManager: <info>  (ttyUSB0): device state change: 9 -> 3 
Dec 24 21:16:11 ****** NetworkManager: <info>  (ttyUSB0): deactivating device (reason: 0). 
Dec 24 21:16:11 ****** NetworkManager: nm_system_device_flush_ip4_routes_with_iface: assertion `iface_idx >= 0' failed
Dec 24 21:16:11 ****** NetworkManager: nm_system_device_flush_ip4_addresses_with_iface: assertion `iface_idx >= 0' failed
Dec 24 21:16:11 ****** NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Dec 24 21:16:12 ****** pppd[6931]: Exit.
Dec 24 21:16:13 ****** NetworkManager: <debug> [1230113773.604634] ensure_killed(): waiting for ppp pid 6931 to exit 
Dec 24 21:16:13 ****** NetworkManager: <debug> [1230113773.604900] ensure_killed(): ppp pid 6931 cleaned up 

I notice some **debug** statements there for Network manager.  Does anyone have any ideas please ?

Oygle

---

### Post by superprash2003 on 2008-12-24
post output of ifconfig from the terminal


merry christmas..

---

### Post by oygle on 2008-12-24
> $ ifconfig
eth0      Link encap:Ethernet  HWaddr **:**:**:**:**:**  
          inet addr:192.168.1.***  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: ****::****:****:****:****/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:702 (702.0 B)  TX bytes:556 (556.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:114 errors:0 dropped:0 overruns:0 frame:0
          TX packets:114 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7784 (7.7 KB)  TX bytes:7784 (7.7 KB)

$

I have read some posts, were people using NM 0.7 that comes with 8.10, are not able to use ppp0 and eth0

With 8.04 (Hardy), there was an easy to use method to control ppp0 and eth0, but not so with NM 0.7

There seems no GUI function at all to control ppp0 , and even etho is obscure, I assume it is the 'hard wired' tab in Network manager.

If I have to 'disable' eth0 to get ppp0 going (and thereby the E169 USB dongle wireless modem), then how can i transfer/share files between 2 Ubuntu computers (i.e. without a LAN connection) ??

Thanks,

Oygle

---

### Post by oygle on 2008-12-26
Had to disable the LAN card (etho) in BIOS, reboot, and then modify the file /etc/network/interfaces as follow, this line ..

```
gateway 192.168.1.101
```

to

```
gateway 
```

restarted the network, and all of a sudden, the E169 USB wireless modem is working. I got a connection at last.

The gateway was previously used to share a dialup connection from another computer, and I thought as the only way that was done, was eth0, better remove that IP address.

So, wireless dongle (attached to USB port on computer, not attached to a router) is finally working with 8.10   :popcorn:

**BUT**, I have _no_ LAN at all, ... this is the only way to force it to work.

The only interfaces are lo and ppp0 (ppp0 is the USB dongle).

So, .. I have ppp0 back now, but no LAN, which is a real pain, because I can't 'share' this fast wireless connection (have had to use dialup for months), with other computer/s, nor can I move files from one computer to the other.  :(

This is 'solved' to some degree, got ppp0 back, but lost eth0, have started a [new thread here]("http://ubuntuforums.org/showthread.php?t=1022569")

Oygle

---

