---
title: "Missing connections tab in Network GUI"
date: 2010-07-27
forum: Networking &amp; Wireless
---

### Post by ragemaw on 2010-07-27
I have recently installed lucid 10.04, and I am having difficulty accessing my wireless.  Following instructions to install the drivers for my wireless card, I always run into a problem when I need to configure my card.  When I go to system-administration-network, there is no connections tab listed.  I can only access General, DNS and hosts.   I was wondering if anyone else had encountered and solved this problem.

Thanks

---

### Post by P4man on 2010-07-27
hmm.. i dont even have system > administration > network ?
Is the ubuntu (gnome)?

Anyway to configure the network; right click the network manager in the tray top right. Make sure wireless is enabled and then select edit connections.

---

### Post by ragemaw on 2010-07-27
I believe I installed a package to get the network option.  In any case, when I set up the network using the method you described, the connection doesn't work. (continuously tries to connect with no success)  When I do an ifdown wlan0, I get an error that wlan0 is not configured.

---

### Post by Iowan on 2010-07-27
Check **ifconfig -a** to see if wireless appears.
If not, check (post) **sudo lshw -C network**.

---

### Post by 7seastraveller on 2011-08-30
I know this thread is more than a year old. 
 
To get System->Administration->Network, you need to install gnome-network-admin package. But I got the same problem. After installation, I only get "General", "DNS" and "Hosts" tab, no Connection tab. I am using Ubuntu 10.04.
 
If anyone still reading this please point me to the right direction. Thanks

---

### Post by northd_tech on 2011-08-30
I remember there being **2** things to check in [Gnome] Network Manager applet (but I use Wicd instead of Network Manager and am under Vi$ta right now so I can't verify):

"Enable Networking" and "Enable Wireless"

If both of those are already checked, then you might have other problems.  It helps to know what kind of wireless hardware you have for troubleshooting purposes- can you post the results of the following terminal commands:

```
sudo lshw -C network
lspci -nnvv | egrep 'etwork|ireless|thernet'
ifconfig
iwconfig
nm-tool
cat /etc/lsb-release
lsmod
rfkill list all

```

EDIT:  Here is the NetworkManager (NM) documentation page with several screenshots (but it can look different under different Window Manager environments and different NM versions):

[https://help.ubuntu.com/community/NetworkManager0.7#User%20Settings%20and%20System%20Settings](https://help.ubuntu.com/community/NetworkManager0.7#User%20Settings%20and%20System%20Settings)

---

### Post by praseodym on 2011-08-30
Hi folks,

in Lucid and Maverick the tool **gnome-network-admin** (I loved it then, only had a modem that time) wasnt as good as ist was once until Karmic, they took something out. Since Natty it is develepod again. Ubuntustudio installs it per default (wireless network configured with wpa_supplicant) because of the realtime-kernel latencies, which are interrupted by the continious scanning of the network-manager. You have to choose network-manager or configure with:

```
sudo adduser $USER dip
```
Login again and:

```
sudo pppoeconf
```
The files you can configure by hand are /etc/network/interfaces, /etc/resolv.conf, and /etc/hosts

---

