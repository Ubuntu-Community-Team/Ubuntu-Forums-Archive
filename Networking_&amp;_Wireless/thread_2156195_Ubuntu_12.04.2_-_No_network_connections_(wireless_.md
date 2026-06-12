---
title: "Ubuntu 12.04.2 - No network connections (wireless or Ethernet)"
date: 2013-06-20
forum: Networking &amp; Wireless
---

### Post by Anu6is on 2013-06-20
I'm on a fresh install and I can't seem to connect to the internet. I'm assuming it's a driver issue but I need some direction in correctly installing. 

I'm currently getting the error "The system network services are not compatible with this version." whenever I navigate to System Settings -> Network


*Wireless script results*
```



*************** info trace ***************


***** uname -a *****


Linux Anu6is 3.5.0-23-generic #35~precise1-Ubuntu SMP Fri Jan 25 17:13:26 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


***** lsb_release *****


Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:    12.04
Codename:    precise


***** lspci *****


01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8162 Fast Ethernet [1969:1090] (rev 10)
    Subsystem: Toshiba America Info Systems Device [1179:ff1e]
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device [10ec:8212]
    Kernel driver in use: rtl8192ce


***** lsusb *****


Bus 001 Device 002: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 002 Device 002: ID 10f1:1a43 Importek 
Bus 006 Device 002: ID 04e8:1f03 Samsung Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub


***** iwconfig *****




***** rfkill *****




***** lsmod *****


rtl8192ce              58779  0 
rtl8192c_common        49512  1 rtl8192ce
rtlwifi                76086  1 rtl8192ce
mac80211              555198  3 rtl8192ce,rtl8192c_common,rtlwifi
cfg80211              208382  2 rtlwifi,mac80211


***** nm-tool *****


NetworkManager Tool


State: unknown




***** NetworkManager.state *****


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


***** NetworkManager.conf *****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq


[ifupdown]
managed=true


***** interfaces *****


auto lo
iface lo inet loopback


auto eth0
iface eth0 inet dhcp




***** iwlist *****




***** resolv.conf *****




***** blacklist *****


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


***** dmesg *****


[   10.585656] rtl8192ce: ****** This B_CUT device may not work with kernels 3.6 and earlier
[   10.585659] rtl8192ce: Using firmware rtlwifi/rtl8192cfwU_B.bin
[   10.765761] rtlwifi: Firmware rtlwifi/rtl8192cfwU_B.bin not available


****************** done ******************



```

Any assistance would be greatly appreciated, and I'll provide any further information required. 

**Figured I'd add this as well...

*Network Info*
```
*-network UNCLAIMED            description: Ethernet controller
       product: AR8162 Fast Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list
       configuration: latency=0
       resources: memory:f0100000-f013ffff ioport:3000(size=128)
  *-network
       description: Network controller
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=rtl8192ce latency=0
       resources: irq:17 ioport:2000(size=256) memory:f0000000-f0003fff



```

Thanks!!!

---

### Post by ahallubuntu on 2013-06-20
~

---

### Post by Anu6is on 2013-06-20
Thanks, I'll check it out.

---

### Post by Anu6is on 2013-06-20
I was really hopeful that that would work, still not connecting though. On reboot I get "Waiting up to 60 more seconds for network configuration"

[COLOR=#000000]dmesg | grep rt [/COLOR]

```
[   10.949318] rtl8192ce: ****** This B_CUT device may not work with kernels 3.6 and earlier[   10.949320] rtl8192ce: Using firmware rtlwifi/rtl8192cfwU_B.bin
[   11.284121] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   11.284446] rtlwifi: wireless switch is on



```

---

### Post by ahallubuntu on 2013-06-20
~

---

### Post by Anu6is on 2013-06-20
I did a re-install and tried the steps found here - [http://ubuntuforums.org/showthread.php?t=2152759](http://ubuntuforums.org/showthread.php?t=2152759) - and now my wireless is up and running. Thanks again for pointing me in the right direction @[ahallubuntu]("http://ubuntuforums.org/member.php?u=32392")[COLOR=#000000] [/COLOR]

Now to get that Ethernet connection working...

---

### Post by Anu6is on 2013-06-21
Installed security and recommended updates and issue has been resolved. 

Sorry that I can't pinpoint which update exactly fixed it but I suppose I'll mark this as resolved.

---

### Post by chili555 on 2013-06-21
> **Anu6is said:**
> Installed security and recommended updates and issue has been resolved. 

Sorry that I can't pinpoint which update exactly fixed it but I suppose I'll mark this as resolved.Does that include ethernet or do you still need some assistance?

---

### Post by Anu6is on 2013-06-21
> **chili555 said:**
> Does that include ethernet or do you still need some assistance?


The updates fixed the Ethernet... the advice you guys gave in the other post fixed the wireless. 

Thanks.

---

