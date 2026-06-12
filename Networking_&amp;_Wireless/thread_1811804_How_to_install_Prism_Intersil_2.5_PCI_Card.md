---
title: "How to install Prism Intersil 2.5 PCI Card?"
date: 2011-07-25
forum: Networking &amp; Wireless
---

### Post by revo8778 on 2011-07-25
I have a LINKSYS WMP11 PCI card with a Prism Intersil 2.5 chipset that I want to install and use as an access point to my ethernet connection. LSPCI and LSHW reveal that the PCI card is indeed present but no driver is installed. I've tried several solutions but none seem to work as an automatic "wlan0" or similar connection has not appeared. What do I need to do in order to install this PCI wifi card?

Running Ubuntu Lucid, latest kernel update.

---

### Post by chili555 on 2011-07-25
Please show us:```
lspci -nn | grep 0280
sudo lshw -C network
```Thanks.

---

### Post by revo8778 on 2011-07-25
Gladly:

Results of lspci:

```
04:02.0 Network controller [0280]: Intersil Corporation Prism 2.5 Wavelan chipset [1260:3873] (rev 01)

```Results of sudo lshw:

```
  *-network               
       description: Ethernet interface
       product: Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: b0
       serial: 00:23:54:5c:fe:a1
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI duplex=full firmware=L1e ip=192.168.10.91 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:27 memory:febc0000-febfffff ioport:ec00(size=128)
  *-network
       description: Wireless interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 2
       bus info: pci@0000:04:02.0
       logical name: eth1
       version: 01
       serial: 00:06:25:03:cd:48
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Intersil 1.3.1 latency=64 link=no multicast=yes wireless=IEEE 802.11b
       resources: irq:18 memory:f8fff000-f8ffffff(prefetchable)

```That first device (Atheros) is my Ethernet card.

And, for an added bonus, here's sudo iwconfig: 

```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"wlan1"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:2 Mb/s   Sensitivity:1/0  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/70  Signal level=-68 dBm  Noise level=-122 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:0   Missed beacon:0

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

```From what I gather, my WiFi card is set up properly but is mapped to eth1. I tried manually mapping it to wlan0 by following the directions here:

[http://www.lysium.de/blog/index.php?/archives/239-Getting-Prism-2.5-working-with-Ubuntu-10.04.html](http://www.lysium.de/blog/index.php?/archives/239-Getting-Prism-2.5-working-with-Ubuntu-10.04.html)

but wlan0 is not present. I also tried setting up a wireless network called "wlan1" through the NetworkManager applet, but it does not seem to function properly. My Kindle believes it to be an "Enterprise or Point-to-Point" network.

---

### Post by chili555 on 2011-07-25
What is wrong with eth1? I have a wireless card using eth1 as its interface and it works perfectly well. I wonder if all that manually mapping it to wlan0 has created a new problem.

You seem to have the appropriate driver:>  *-network
       description: Wireless interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       logical name: eth1
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes [COLOR="Red"]driver=orinoco[/COLOR] driverversion=0.15 Your mode is Managed, which is entirely appropriate for computer to router connection:> eth1      IEEE 802.11b  ESSID:"wlan1"  
          [COLOR="Red"]Mode:Managed[/COLOR]  Frequency:2.457 GHz  Access Point: None   
          Bit Rate:2 Mb/s   Sensitivity:1/0  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Encryption key:offLet's look at two more things before we crack open the chest and do an exploratory:```
cat /etc/network/interfaces
sudo iwlist eth1 scan
```

---

### Post by revo8778 on 2011-07-25
Results of cat:

```
auto lo
iface lo inet loopback

```Results of iwlist:

```
eth1      Interface doesn't support scanning : Device or resource busy

```

---

### Post by chili555 on 2011-07-25
> I also tried setting up a wireless network called "wlan1" through the NetworkManager applet,If you mean in 'Create New Wireless Network...' that's generally intended for ad-hoc connections; that is, computer-to-computer as is typical for internet connection sharing. I suggest you delete all of those settings.

Let's take a look at:```
cat /etc/udev/rules.d/70-persistent-net.rules
```We may have some undoing to do.

While you respond, I'll get out my old Prism card and scratch my head a bit.

---

### Post by revo8778 on 2011-07-25
Currently it's set to this:

```

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x1969:0x1026 (ATL1E)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:23:54:5c:fe:a1", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x1260:0x3873 (orinoco_pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:06:25:03:cd:48", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

```

By default, the second device is roughly the same but the names are eth* and eth0.

---

### Post by chili555 on 2011-07-26
I'd change it back:```
# PCI device 0x1260:0x3873 (orinoco_pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:06:25:03:cd:48", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="[COLOR="Red"]eth[/COLOR]*", NAME="[COLOR="Red"]eth1[/COLOR]"
```Reboot immediately. As well, often both hostap and orinoco load. In most cases, they conflict. Check:```
lsmod | grep -e orin -e host
```If both are loaded, I'd blacklist orinoco:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add two lines:```
blacklist orinoco
blacklist orinoco_pci
```Proofread, save and close. Reboot. If you still can't connect, reverse the process, blacklist hostap and hostap_pci and see if it helps.

I dug out my Prism 2.5 last evening and tried orinoco and hostap. I tried with and without Network Manager. I tried changing the router from WPA2 to WPA and to WEP. It connected perfectly to WEP and none other, even though the card reports its capable of WPA and WPA2:```
sudo iwlist eth1 auth
```I wonder if there is an issue with hostap and wpa_supplicant.

---

### Post by revo8778 on 2011-07-26
It's been changed back to it's defaults.

Results of lsmod:

```
orinoco_pci             3303  0 
orinoco                71312  1 orinoco_pci
cfg80211              148341  1 orinoco

```

Hostap does not appear to be loaded. Here's the current status of my blacklist:

```
blacklist amd76x_edac
blacklist bcm43xx
blacklist b43
blacklist b43legacy
blacklist ssb

```

Results of sudo iwlist:
```

eth1      unknown authentication information.

```

---

### Post by chili555 on 2011-07-26
Did you try blacklisting the orinoco suite and letting hostap load? Isn't hostap on your system?```
modinfo hostap
```If you get data from this command, try:```
sudo modprobe hostap
```If not, post back.

---

### Post by revo8778 on 2011-07-26
Results of modinfo hostap:

```

filename:       /lib/modules/2.6.32-33-generic/kernel/drivers/net/wireless/hostap/hostap.ko
license:        GPL
description:    Host AP common routines
author:         Jouni Malinen
srcversion:     F7328B75EAD6AD3F36B560C
depends:        lib80211
vermagic:       2.6.32-33-generic SMP mod_unload modversions 
parm:           other_ap_policy:Other AP beacon monitoring policy (0-3) (array of int)
parm:           ap_max_inactivity:AP timeout (in seconds) for station inactivity (array of int)
parm:           ap_bridge_packets:Bridge packets directly between stations (array of int)
parm:           autom_ap_wds:Add WDS connections to other APs automatically (array of int)

```Results of sudo modprobe hostap:

```

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.

```orinoco and orinoco_pci have been blacklisted.

---

### Post by chili555 on 2011-07-26
It looks like you tried ndiswrapper and it's not yet removed or at least disabled. Yes? Let's see:```
lsmod | grep ndis
ndiswrapper -l
```That's a lower-case L for 'list.'

---

### Post by revo8778 on 2011-07-26
Yes, I tried it a one point when attempting to get this card to work.

Results of lsmod | grep ndis:

```

ndiswrapper           244800  0 

```

Ndiswrapper -l produced no results.

---

### Post by chili555 on 2011-07-26
Let's do some housekeeping. First, let's examine the contents of a file:```
cat /etc/modprobe.d/blacklist
```I suspect it blacklists hostap and hostap_pci. If that's what it says, then do:```
sudo rm /etc/modprobe.d/blacklist
```Also, let's remove the file that calls ndiswrapper:```
sudo rm /etc/modprobe.d/ndiswrapper
```Now, we unload the module and load hostap, et al:```
sudo rmmod -f ndiswrapper
sudo modprobe hostap_pci
```Are there any suspicious errors or warnings? Does your wireless card come to life?```
iwconfig
```Thanks.

---

### Post by revo8778 on 2011-07-26
[FONT=Arial][FONT=monospace]cat /etc/modprobe.d/blacklist produced no results.

All other commands competed fine; no errors.

Results of final iwconfig:

```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"Rlan1"  
          Mode:Ad-Hoc  Frequency:2.457 GHz  Cell: 02:06:3B:21:CD:48   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry short limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:849  Invalid misc:0   Missed beacon:0

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

```



[/FONT]

[/FONT]

---

### Post by chili555 on 2011-07-26
Is Rlan1 by any chance your network? Can you click the Network Manager icon and see networks? Connect?```
sudo iwlist eth1 scan
```

---

### Post by revo8778 on 2011-07-27
Yes, Rlan1 is the ad-hoc network I have running.

Results of sudo iwlist:

```
eth1      No scan results

```

---

### Post by chili555 on 2011-07-27
Did you set up Ad Hoc networking in Network Manager? [https://help.ubuntu.com/community/WifiDocs/Adhoc#NetworkManager%20Method](https://help.ubuntu.com/community/WifiDocs/Adhoc#NetworkManager%20Method)

Your settings and readings look healthy to me.

---

