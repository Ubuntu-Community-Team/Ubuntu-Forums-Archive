---
title: "wifi vs ethernet DNS problem"
date: 2009-08-20
forum: Networking &amp; Wireless
---

### Post by zot171 on 2009-08-20
Hey everyone! I've got an interesting problem with my Linksys WRT54G with DD-WRT firmware (v24-sp1) and my AT&T Motorola modem (model 2210, I think) that I hope we can solve. At first install and boot up, I ran into many problems with both devices wanting to be the DHCP server, ending with me finally putting the modem in bridged mode and setting the router to handle the PPPoE authentication, DHCP leasing, DDNS, et al. (This is where it get weird ==>) Now, any computer connected through ethernet can access the internet without a problem, but if any computer tries to get online through the wireless access point, they can access the internet, but DNS lookup seems to fail. You can still access the internet, but only using IP addresses (74.125.45.100 will get you to google, but google.com doesnt work) I originally thought it was AT&Ts DNS servers failing on me, so I registered with openDNS and entered theirs as my primary and secondary static DNS servers on the router, with no change.

Any ideas?

---

### Post by FreeLanceR187 on 2012-05-23
Hi guys,

Reviving this old thread as I'm experiencing the exact same issue. It seems that one of the services running along with my wlan connection is confusing my WRT54G router and causes it to loose DNS capabilities until rebooted.

Any clue of what could cause the issue?
I've read somebody mentionning lokkit for a similar issue but I don't feel like deactivating it.

Thanks

Edit: Just noticed a similar topic here (kUbuntu)
[http://ubuntuforums.org/showthread.php?t=1971342](http://ubuntuforums.org/showthread.php?t=1971342)

---

### Post by chili555 on 2012-05-23
Let's clarify and confirm. You have somebody's DSL modem connected to a WRT54G and connect wired and wirelessly to the WRT54G, correct? Is it also running dd-wrt firmware? Are the wired computers, if any, getting DNS nameservers? We need to isolate if it's a modem problem, a router problem or an Ubuntu wireless problem. Tell us more details, please.

---

### Post by FreeLanceR187 on 2012-05-23
You got most of it. The setup is:

-1 cable modem
-1 WRT54G running DDWRT
-3 wired computers
-5 wireless devices (including phones)

The DDWRT is using the latest stable release for my WRT54G version.

The DNS ips are 2/3 static, 1/3 dynamic (using Open DNS and getting the last IP from my provider). So I don't think it could be related to the Domain Name Server being unavailable.

It has been working fine until past week. I switched my laptop back to ubuntu. Since that, whenever it is running, I, from time to time, loose DNS capabilities on all devices (including wired ones). A router reboot fixes the issue everytime. When is happens, DNS ip on devices is still correct (the router IP). He seems to be the one failing.

I actually didn't think it could come from my ubuntu laptop until yesterday when I didn't use it for the whole day...and surprisingly, I didn't experience any DNS issue. Turned it on this morning and in a matter of minutes, it happened again.

I'll have a test it wired for a day and see if it works as well. I didn't have time to try it out yet.

My guess is there are services conflicting somewhere in my network setup. I was wondering if you guys have ever heard of something similar.

Laptop is a XPS15(l502x).
lshw -C network
  *-network DISABLED      
       description: Wireless interface
       product: Centrino Wireless-N 1000
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.2.0-24-generic firmware=39.31.5.1 build 35138 latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:53 memory:f1b00000-f1b01fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 06
       serial: 
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=192.168.57.173 latency=0 multicast=yes port=MII speed=1Gbit/s
       resources: irq:50 ioport:2000(size=256) memory:f1804000-f1804fff memory:f1800000-f1803fff


Let me know if there's anything else I can provide.

Thanks

---

### Post by chili555 on 2012-05-23
It's hard to diagnose the wireless problem with the ethernet connected:> *-network
description: Ethernet interface
product: RTL8111/8168B PCI Express Gigabit Ethernet controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:06:00.0
logical name: eth0
version: 06
serial:
size: 1Gbit/s
capacity: 1Gbit/s
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw [COLOR="Red"]ip=192.168.57.173[/COLOR] Second, this usually indicates the wireless switch is set to disable the wireless:> *-network [COLOR="Red"]DISABLED[/COLOR]
description: Wireless interface
product: Centrino Wireless-N 1000
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:03:00.0
logical name: wlan0Last, the Intel chipsets have a known issue with 802.11N. Please do:```
sudo gedit /etc/modprobe.d/iwlwifi.conf
```Add a single line:```
options iwlwifi 11n_disable=1
```Proofread, save and close gedit. Detach the ethernet cable and reboot. Switch the wireless back on and let us hear your report.

---

### Post by FreeLanceR187 on 2012-05-24
> It's hard to diagnose the wireless problem with the ethernet connected:
[QUOTE]
*-network
description: Ethernet interface
product: RTL8111/8168B PCI Express Gigabit Ethernet controller
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:06:00.0
logical name: eth0
version: 06
serial:
size: 1Gbit/s
capacity: 1Gbit/s
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=192.168.57.173
Second, this usually indicates the wireless switch is set to disable the wireless:

> *-network DISABLED
description: Wireless interface
product: Centrino Wireless-N 1000
vendor: Intel Corporation
physical id: 0
bus info: pci@0000:03:00.0
logical name: wlan0
[/QUOTE]


I was connected on a different network when I ran the command. I just wanted you to have a look at the wireless card. I had a feeling that something like > Last, the Intel chipsets have a known issue with 802.11N. would come up.

I disabled the "n" capabilities of the wireless card as you recommended. So far so good. I'll keep you posted on the long run.

Thanks for you help.

---

