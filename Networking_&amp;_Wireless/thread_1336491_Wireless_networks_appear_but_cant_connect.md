---
title: "Wireless networks appear but cant connect"
date: 2009-11-24
forum: Networking &amp; Wireless
---

### Post by hrafninn on 2009-11-24
I have been running Ubuntu 9.04 for many months without any wireless networking problems.  Suddenly today, I noticed that I cannot connect to wireless networks anymore. The networks, however, do appear under the network icon with showing strong signal.

**Output from lshw:**
*-network
                description: Wireless interface
                product: BCM4328 802.11a/b/g/n
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: wlan0
                version: 03
                serial: 00:1c:26:94:47:cb
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 module=wl multicast=yes wireless=IEEE 802.11abgn

**Output from iwconfig:**
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11  Nickname:""
          Access Point: Not-Associated
          Link Quality:5  Signal level:231  Noise level:168
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

vboxnet0  no wireless extensions.

pan0      no wireless extensions.

**Doesn't this "Access Point: Not-Associated" signal a problem?**


Output from **dmesg | grep -e ndis -e wlan:**

[   15.607576] udev: renamed network interface eth1 to wlan0
[   17.068968] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   17.125257] usbcore: registered new interface driver ndiswrapper
[   36.053058] wlan0: no IPv6 routers present

Can anyone help?

---

### Post by Hachi-Roku on 2009-11-25
Hey i had the same 'sudden-ness' too, although mine is a WPA key issue.

Possible that an network manager update has gone backwards?

---

