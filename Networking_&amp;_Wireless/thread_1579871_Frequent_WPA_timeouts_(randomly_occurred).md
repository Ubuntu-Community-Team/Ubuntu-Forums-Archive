---
title: "Frequent WPA timeouts (randomly occurred)"
date: 2010-09-22
forum: Networking &amp; Wireless
---

### Post by SundeepG on 2010-09-22
Hey,

I have been using Ubuntu 10.04 for a while now. All of a sudden my WPA connections would seem to 'timeout'. When I say timeout, I am referring to the process where they will stop receiving data from the router after short periods of time, requiring me to disconnect and then reconnect to the wireless network. This problem only happens on WPA networks. The problem randomly started happening, with the timeout frequency progressing from once every hour, to once every 10 minutes, to now where it happens after about 10 seconds. Here is my information (lshw):
*-network               
       description: Wireless interface
       product: WiFi Link 1000 Series
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:26:c7:5e:37:12
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.101 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:34 memory:d3000000-d3001fff

I have tried reinstalling wpasupplicant although this is no help (along with almost every package installed when I typed in wireless). I am thinking that the problem may be remedied if I completely removed wpasupplicant and then reinstalled it (just a hypothesis) although I cannot remove it without uninstalling several important packages, like ubuntu-desktop. I found a similar thread dating back to Drapper and the solution they had was to do a fresh install of the OS. As this is extremely inconvenient, I was hoping someone could help me find another solution that doesn't require me having to back up all my data, do a clean OS install, reinstall all my old programs, reconfigure my settings, etc etc...

---

