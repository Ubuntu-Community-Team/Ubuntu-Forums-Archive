---
title: "Atheros Wifi Goes Up, Down, Up, Down, Up, Down Rinse and Repeat"
date: 2012-09-29
forum: Networking &amp; Wireless
---

### Post by iosion on 2012-09-29
I have 80 Acer Aspire One netbooks here in 4 different models. Makes for fun times.

My V2 model is a NAV-50. Also listed on the back is 532h-2622.

Using the newest config tool and newest image (from just a few days ago) I could install the image to this V2 fine but... the wifi would come up, go down. Up, down. Up... down again. Up again and... then down.

Wireless NIC is Atheros AR9285 PCI-E (rev 01)

Using Open1to1 build of Edubuntu 12. I believe it is 12.04, not sure until I get back in to the lab Monday.

What is odd... is that with earlier images of edubuntu this machine did NOT exhibit this behavior. Its only since the upgrade.

Can anyone help me with this bouncy wifi issue?

Thanks!

---

### Post by iosion on 2012-10-02
Bump.

My back is up against a wall here. Can anyone offer any ideas to help me move forward?

Thanks!

---

### Post by steeldriver on 2012-10-02
What driver?

```
sudo lshw -C network
```Sometimes the atheros drivers need to be run with hardware encryption disabled

---

### Post by iosion on 2012-10-02
*-network               
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth2
       version: c0
       serial: 70:5a:b6:1d:0b:fe
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.1.230 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:45 memory:57000000-5703ffff ioport:5000(size=128)
  *-network DISABLED
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 78:e4:00:3d:83:f7
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-29-generic-pae firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:56000000-5600ffff

---

### Post by iosion on 2012-10-02
I disabled the hardware encryption... still no go.

On off up down up down on off...

Help!

---

### Post by iosion on 2012-10-02
SOLVED

Please open a terminal and do:
Code:
sudo gedit /etc/modprobe.d/blacklist.conf
Add a line at the very end.
Code:
blacklist acer-wmi
Proofread twice, save and close gedit. Now do:
Code:
sudo gedit /etc/rc.local
Add one line above exit 0
Code:
rfkill unblock all
Proofread twice, save and close gedit.

Reboot. Post back to confirm to me that every change was done perfectly as requested and to tell me how your wireless is working.

I have NO idea why this worked, but it did.

//

---

