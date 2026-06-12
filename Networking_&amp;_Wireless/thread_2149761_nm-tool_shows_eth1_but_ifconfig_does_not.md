---
title: "nm-tool shows eth1 but ifconfig does not ??"
date: 2013-05-29
forum: Networking &amp; Wireless
---

### Post by Andres Gonzalez on 2013-05-29
I am having problems with my Dell XPS Developer edition running 12.4.  I am using a USB2/Ethernet adapter that use to work fine but for some reason it no longer works. Using nm-tool, it shows:  Device: eth1   but when I do ifconfig there is no eth1 device.

And what are  lxcbr0 and virbr0  ???

my /etc/network/interfaces is configured for a static address for eth1 but still nothing.

In Unity, under System Settings--Network, Wired, it shows:  Wired Unmanaged.   The Options button is inactive so it is unavailable. What is "Airplane Mode"  ?

The most frustrating thing is that this USB2/Ethernet used to work just fine.

Any help would be greatly appreciated.

-Andres

---

### Post by steeldriver on 2013-05-29
You shouldn't usually define interfaces via /etc/network/interfaces if you are using network-manager - by default, if you do so network-manager will ignore them (hence 'unmanaged') - typically you should only have the loopback ('lo') interface in /etc/network/interfaces if you are using n-m

lxcbr would be related to virtualization containers I think --> [https://help.ubuntu.com/12.04/serverguide/lxc.html](https://help.ubuntu.com/12.04/serverguide/lxc.html)

---

