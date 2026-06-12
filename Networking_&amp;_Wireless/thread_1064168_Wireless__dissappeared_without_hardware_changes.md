---
title: "Wireless  dissappeared without hardware changes"
date: 2009-02-08
forum: Networking &amp; Wireless
---

### Post by ingridt on 2009-02-08
Hi,
Programs like wlassistant keeps saying "No wireless interfaces found", yet I did not take out anything out of the laptop. Only do all upgrades Ubuntu proposes. (Ubuntu 8.04.02 kernel 2.6.24-23-generic; but the problem persists since many previous kernels;) but I did not really need wireless the last 2 months)

Up to about 2 months ago I could go wireless by simply clicking the network of my choice, now all of this has disappeared. (I use to work with ethernet cable)

My question: how to get it back to active state, so I can surf wireless again?

Some more details:
**dmesg | grep -e eth -e wlan**
[   15.981871] eth0: Tigon3 [partno(BCM95787m) rev b002 PHY(5787)] (PCI Express) 10/100/1000Base-T Ethernet 00:1b:24:64:57:62
[   15.981878] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] WireSpeed[1] TSOcap[1]
[   15.981881] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   18.844387] Driver 'sd' needs updating - please use bus_type methods
[   18.844578]  sda:<4>Driver 'sr' needs updating - please use bus_type methods
[   40.222321] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   40.222332] tg3: eth0: Flow control is off for TX and off for RX.
[   56.573733] eth0: no IPv6 routers present

**lspci**
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
05:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)

** iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by utnubuuser on 2009-02-08
Check the release notes at the Ubuntu HardyHeron wiki, or the Intrepid Ibex wiki.  I seem to remember reading something there about that wireless setup.

---

### Post by ingridt on 2009-02-10
So I go to [http://www.ubuntu.com/getubuntu/releasenotes/804](http://www.ubuntu.com/getubuntu/releasenotes/804)

And read:
> Network Manager

    *

      In Ubuntu 8.04, network-manager only manages interfaces that are marked for roaming. Thus, all interfaces that were previously managed by network-manager will be set to roaming mode during upgrade. Technically, this takes any interface stanzas using the dhcp method with no options and that are marked auto, and removes them from /etc/network/interfaces. If you rely on your interfaces being started by ifupdown when the system starts up, you need to re-enable them in /etc/network/interfaces manually, or disable roaming in System -> Administration -> Network.


If this is the solution, I do not see any wireless in System > Administration > Network.
But I might be inspecting the wrong pages, as googling on "Ubuntu HardyHeron wiki" gives far more then just one result. For the moment I cannot afford to spend yet another day searching wiki's as I did Sunday searching forums all day.

So, does this roaming has anything to do with my problem?

---

### Post by ingridt on 2009-02-10
Just one more detail: wireless has been working fine since the first install, without any configurations to do. It simply stopped working somewhere in the period of time I did not need it (last 2 months).

---

### Post by ingridt on 2009-11-17
it was just a matter of touching a button on the laptop that turns wireless on and off...

---

