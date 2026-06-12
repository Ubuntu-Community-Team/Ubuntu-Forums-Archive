---
title: "AWUS036NHR (Realtek 8188RU) and compat-wireless"
date: 2012-04-14
forum: Networking &amp; Wireless
---

### Post by Tesla01 on 2012-04-14
Hi,

I have ubuntu 11.10, Kernel 3.0.0-17. I wanted to use the alfa USB adapter AWUS036NHR on my Netbook Samsung NC10.

Awus had only drivers for kernel 2.6.x, so I used the drivers from Realtek Homepage.
The driver works to connect as client to accesspoint, but not in master mode to create an own accesspoint wich was the intention for buying this adapter.

lsmod says  "8192cu".

I read somewhere to use the compat-wireless drivers, which should support master mode. I installed compat-wireless-3.0-2, which worked without errors.

The problem ist now, that these drives did not activate the usb-adapter.
lsmod says: 
rtl8192cu 
rtl8192c_common
rtlwifi

if i unload these and modprobe 8192cu the card works again

any suggestions how to get it work without the original realtek drivers?

Tesla

---

### Post by Tesla01 on 2012-04-14
OK, maybe I found something..

> 

root@Netbook-NC10:~# lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04e8:6773 Samsung Electronics Co., Ltd 
Bus 001 Device 004: ID 0ac8:c326 Z-Star Microelectronics Corp. Namuga 1.3M Webcam
Bus 004 Device 002: ID 0458:00a2 KYE Systems Corp. (Mouse Systems) 
Bus 001 Device 007: ID 0bda:817f Realtek Semiconductor Corp. 

the device is the 0bda:817f Realtek Semiconductor Corp.
But the module does not contain the ID:

> 
root@Netbook-NC10:~# modinfo rtl8192cu
filename:       /lib/modules/3.0.0-17-generic/updates/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw.bin
description:    Realtek 8192C/8188C 802.11n USB wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Ziv Huang    <ziv_huang@realtek.com>
author:         Georgia        <georgia@realtek.com>
srcversion:     2179B6DDE6396967FCAFBE1
alias:          usb:v7392p7822d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB2Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p330Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3309d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3307d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p8178d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p8178d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07AAp0056d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0586p341Fd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v3359p13D3d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v3358p13D3d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7811d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v20F4p648Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED17d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pAB2Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3308d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v103Cp1629d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0EB0p9071d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0DF6p0052d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0846p9041d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p8189d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8p8188d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v06F8pE033d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v050Dp1102d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8177d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8754d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp817Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8177d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8176d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8170d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BDAp8191d*dc*dsc*dp*ic*isc*ip*
depends:        rtlwifi,mac80211,rtl8192c-common
vermagic:       3.0.0-17-generic SMP mod_unload modversions 686 
is it possible to add it and recompile the driver?
I haven't done something like this before..

---

### Post by chili555 on 2012-04-15
I suggest you try the Ubuntu version of compat-wireless, linux-backports-modules-cw-3.1-oneiric-generic. It *does* include your device:> $ modinfo rtl8192cu
filename:       /lib/modules/3.0.0-17-generic-pae/[COLOR="Red"]updates/cw-3.1[/COLOR]/rtl8192cu.ko
firmware:       rtlwifi/rtl8192cufw.bin
description:    Realtek 8192C/8188C 802.11n USB wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Ziv Huang	<ziv_huang@realtek.com>
author:         Georgia		<georgia@realtek.com>
srcversion:     FA58EF2F885D8862DDFE346
<snip>
alias:          usb:v0BDAp817Fd*dc*dsc*dp*ic*isc*ip*
<snip>
depends:        rtlwifi,mac80211,rtl8192c-common
vermagic:       3.0.0-17-generic-pae SMP mod_unload modversions 686 Whether it does master mode or not, I don't know. I don't have the device.

---

### Post by Tesla01 on 2012-04-17
> **chili555 said:**
> I suggest you try the Ubuntu version of compat-wireless, linux-backports-modules-cw-3.1-oneiric-generic. It *does* include your device:Whether it does master mode or not, I don't know. I don't have the device.

OK, I will give it a try.

Meanwhile I installed [http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.1/compat-wireless-3.1.1-1.tar.bz2](http://www.orbit-lab.org/kernel/compat-wireless-3-stable/v3.1/compat-wireless-3.1.1-1.tar.bz2).

With this driver the card activates (LED on) an I can connect to AP's. So far the driver seems OK.
Also hostapd can use the card now and startes up.

The Problem now its, nobody can see this newly created AP...
If I change to the internal wlan0 in hostapd.conf the AP appears and I can connect e.g. from a smartfone to it.


Any Ideas where to debug now? I can post a hostapd -dd later.

---

### Post by chili555 on 2012-04-17
> Any Ideas where to debug now?I'm sorry, I have none.

---

### Post by Tesla01 on 2012-04-19
I now bought also an AUWS036[COLOR=red]NH [/COLOR][COLOR=black]and this one works perrfektly.[/COLOR]
 
And in addition it uses the right regulatory domain, which the NHR did not (it only allowed 11 channels regardless of which iw reg set XX I did).
 
So I think the driver rtl8192cu still needs some overwork..

---

### Post by chili555 on 2012-04-19
> So I think the driver rtl8192cu still needs some overwork..Agreed. I'm glad you're all set now, even if it did take a replacement device.

---

