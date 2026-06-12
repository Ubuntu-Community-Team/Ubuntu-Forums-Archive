---
title: "Ibex random slow down after login - iwlagn error"
date: 2009-02-04
forum: Networking &amp; Wireless
---

### Post by mr.fudo on 2009-02-04
Hello everybody,

I recently bought a new Sony Vaio, and immediately installed Intrepid Ibex on it, hoping for the best. Everything seemed to work fine, even wireless connection, and for a few days I really had no problems. A couple of days ago the system started to show a new behavior: after the login, when the network icon is trying to establish a wireless connection, everything slows down (mouse pointer not moving, keyboard almost non-reacting, nothing works...) and the OS turns absolutely unusable. This doesn't happen at every login (right now I'm connected to the wifi network and everything works fine), but it does happen quite often. When the system "freezes" I can (slowly) switch to a terminal (Ctrl+Alt+F2), where an infinite sequence of messages like these

$ iwlagn: Microcode SW error detected.  Restarting 0x2000000.
$ iwlagn: Error setting new RXON (-5)

fills the screen. I can only restart the laptop with Ctrl+Alt+Del, and hope that the following boot will be ok.

I'm using kernel 2.6.27-11, and keep all the packages updated.
The laptop is a Vaio NS21Z and mounts an Intel 5100 wireless card:

 *-network
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 00
       serial: 00:21:5d:ee:a3:d8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.0.11 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn

I can attach part of /var/log/syslog if you think it can help. Actually I will add/attach any information that might help someone figure out how to solve this problem that is driving me crazy!

I've been using Ubuntu (and Xubuntu) for a few months now, and I've usually been able to fix problems and issues just searching the web or the extremely helpful ubuntuforums! This time I haven't found any solution by myself... hope I can get some help from the community :)

Daniele

---

### Post by mr.fudo on 2009-02-06
Up

The problem is definitely related with the wireless connection: everything works fine if I turn off the wlan (external switch) before turning on the laptop. When I turn it on again (I need it to get online) I see the "connecting" icon, and the the system almost freezes.
Any hint? It's really annoying having to restart my laptop several times before being able to use it... 
Ideas?

---

