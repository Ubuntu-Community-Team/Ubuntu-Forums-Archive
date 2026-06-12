---
title: "Wake-on-lan from suspend"
date: 2010-12-10
forum: Networking &amp; Wireless
---

### Post by popawu on 2010-12-10
Hi,

I try to wake up my PC with wake-on-lan from a suspend or hibernate state, but it does'nt work.
Here is what I did :


- Interface configuration with ethtool by adding wol option:
ethtool -s eth0 wol g (script added in startup)
Option is enabled and the card is compatible :
```
me@server:~$ sudo ethtool eth0
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Half 1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Half 1000baseT/Full 
        Advertised pause frame use: No
        Advertised auto-negotiation: Yes
        Link partner advertised link modes:  10baseT/Half 10baseT/Full 
                                             100baseT/Half 100baseT/Full 
        Link partner advertised pause frame use: No
        Link partner advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        Link detected: yes
```- Whitelist of the network card in acpi configuration :
card driver :
```
me@server:~$ lsmod | grep mii
mii                     4425  1 r8169
```acpi config :
```
me@server:~$ sudo vi /etc/default/acpi-support
...
# Add modules to this list to leave them in the kernel over suspend/resume
MODULES_WHITELIST="r8169"
...
```- suspend with pmi :
```
me@server:~$sudo pmi action suspend
```- wake-up by sending a magic paket with ether-wake :
```
me@server2:~$ether-wake -i eth0.1 00:1A:4D:XX:XX:XX
```I don't know how to debug.
Fyi, the PC wakes up from a halt state, and I've tested with all compatible options of the network card, with no luck. I can see the light of the led on the router, so the card looks alive.

config :
Linux version 2.6.35-23-generic-pae (buildd@roseapple) (gcc version 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5) ) #41-Ubuntu SMP Wed Nov 24 10:35:46 UTC 2010
Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)

hope someone can help me on this :)
thx

---

### Post by popawu on 2010-12-13
UP :o

---

### Post by popawu on 2010-12-13
Hi,

Here is a workaround :

Edit the script /usr/lib/pm-utils/sleep.d/55NetworkManager and comment the call to the function suspend_nm (sending org.freedesktop.NetworkManager.sleep signal)

You can also rename the script, so the sleep.d acpi init won't call it and the card will stay alive.
Not very clean but working.

Another way is to run the NIC from pci-bus : (does not work for me :( )


First, stop the NIC :
echo 1 > /sys/class/net/eth0/device/remove
 Then, restart it from the PCI bus :
echo 1 > /sys/class/pci_bus/0000:00/device/0000:00:00.0/rescan


see [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/462933](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/462933)

---

### Post by aay on 2011-07-23
popawu,

Thanks, thanks, thanks!!!!  I looked everywhere and tried seemingly everything (to no avail) to try and get WOL working on my desktop.  Only getting rid of 55NetworkManager worked.   Thanks again so very much!

Adam

---

