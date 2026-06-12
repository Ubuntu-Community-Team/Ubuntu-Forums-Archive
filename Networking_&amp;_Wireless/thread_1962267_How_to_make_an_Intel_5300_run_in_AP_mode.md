---
title: "How to make an Intel 5300 run in AP mode?"
date: 2012-04-20
forum: Networking &amp; Wireless
---

### Post by dengn on 2012-04-20
Hi,

I've got an Intel 5300 card, and I want to run it in AP mode.

I tried directly the iwconfig to set it to master mode, but it doesn's work. 

Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.

I also tried to use hostapd, but it seems that it's not the same as run an Atheros card.

in the hostapd conf file, I set 

driver=iwlwifi , which I found from lspci -v. However, i got an error again. 

hostapd -d /etc/hostapd/hostapd_new.conf 
Configuration file: /etc/hostapd/hostapd_new.conf
Line 3: invalid/unknown driver 'iwlwifi'
1 errors found in configuration file '/etc/hostapd/hostapd_new.conf'

Do you have some suggestions?

---

### Post by chili555 on 2012-04-20
> in the hostapd conf file, I set

driver=iwlwifi , which I found from lspci -v. However, i got an error again.
I believe the driver is actually *iwlagn*.> I tried directly the iwconfig to set it to master mode, but it doesn's work.

Error for wireless request "Set Mode" (8B06) :
SET failed on device wlan0 ; Invalid argument.
This may be helpful: [http://ns3.spinics.net/lists/linux-wireless/msg79587.html](http://ns3.spinics.net/lists/linux-wireless/msg79587.html)> You cannot set master mode without using hostapd.

---

### Post by dengn on 2012-04-21
Hi,

I've tried iwlagn. I still got an error.

Line3: invalid/unknown driver 'iwlagn'

---

### Post by dengn on 2012-04-21
> **chili555 said:**
> I believe the driver is actually *iwlagn*.This may be helpful: [http://ns3.spinics.net/lists/linux-wireless/msg79587.html](http://ns3.spinics.net/lists/linux-wireless/msg79587.html)

This is what I've got from lshw about my wireless card:

sudo lshw -C network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 5300 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:6a:c6:90:76
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.3.0-rc1+ firmware=8.24.2.12 ip=192.168.2.38 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:21 memory:efdfe000-efdfffff

---

### Post by dengn on 2012-04-21
> **dengn said:**
> This is what I've got from lshw about my wireless card:

sudo lshw -C network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 5300 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:6a:c6:90:76
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.3.0-rc1+ firmware=8.24.2.12 ip=192.168.2.38 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:21 memory:efdfe000-efdfffff

OK. I've solved it. The solution is to use the latest version of hostapd, here it's hostapd-0.7.3, and still configure the driver as nl80211.

---

### Post by chili555 on 2012-04-21
It took me a bit to figure this out. Evidently, you are running 12.04 where the driver is renamed iwlwifi:> $ modinfo iwlwifi
filename:       /lib/modules/[COLOR="Red"]3.2.0-23[/COLOR]-generic-pae/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
[COLOR="Red"]alias:          iwlagn[/COLOR]
license:        GPL
<snip>
I saw this: [http://www.ibm.com/developerworks/library/l-wifiencrypthostapd/](http://www.ibm.com/developerworks/library/l-wifiencrypthostapd/)> This WIC will not work as an access point because the iwlagn driver is not supported by hostapd, and in any case it does not support AP mode. (It is part of a low-budget integrated Centrino chip.) And this: [http://wireless.kernel.org/en/users/Drivers](http://wireless.kernel.org/en/users/Drivers)

The driver table says iwlagn is not capable of AP (access point) mode.

---

### Post by dengn on 2012-04-24
> **chili555 said:**
> It took me a bit to figure this out. Evidently, you are running 12.04 where the driver is renamed iwlwifi:I saw this: [http://www.ibm.com/developerworks/library/l-wifiencrypthostapd/](http://www.ibm.com/developerworks/library/l-wifiencrypthostapd/)And this: [http://wireless.kernel.org/en/users/Drivers](http://wireless.kernel.org/en/users/Drivers)

The driver table says iwlagn is not capable of AP (access point) mode.

Well. I don't know if that was old version or not. But in my case, it now works well by using Hostapd 0.7.3, however I still have a problem to work on.

By running the latest Hostapd 0.7.3 and configure the driver still as "driver = nl80211", I succeed to make my Intel 5300 AGN run as an AP.

The clients could find this AP, associate to it, get an IP address and share the Internet, only if I set the AP without a WPA password. (DHCP server and iptables are well set)

Once I added a WPA passphrase in the hostapd conf, the stations could only pass the authentication, but then were stuck in the step of getting IP address. I didn't modify anything of dhcp. 

Do you guys have any ideas? Or someone has a more decent way to run intel5300 agn in AP mode?

---

