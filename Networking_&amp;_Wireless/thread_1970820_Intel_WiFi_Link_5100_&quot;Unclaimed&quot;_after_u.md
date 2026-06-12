---
title: "Intel WiFi Link 5100 &quot;Unclaimed&quot; after upgrade to 12.04"
date: 2012-05-01
forum: Networking &amp; Wireless
---

### Post by Toby on 2012-05-01
Upgraded to 12.04 yesterday, been trying to get the wireless working ever since. Checking the network config reveals that the adapter is 'unclaimed'.


> 
**sudo lshw -C Network**
  *-network UNCLAIMED     
       description: Network controller
       product: WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: memory:f8000000-f8001fff



I've tried using ndiswrapper, but I can't seem to get it to work.


> 
**ndiswrapper -l**
netw5s32 : driver installed
	device (8086:4232) present (alternate driver: iwlagn)

**sudo ifup wlan0**
Ignoring unknown interface wlan0=wlan0.


I'm not sure how to proceed.
Please advise.

---

### Post by chili555 on 2012-05-01
> I've tried using ndiswrapperBoooo!

Please try this:```
sudo modprobe -r ndiswrapper
sudo modprobe iwlwifi
dmesg | grep iwl
rfkill list all
```These changes are temporary; if they work, we'll need to tweak a couple of files.

---

### Post by Toby on 2012-05-01
.

> [B]sudo modprobe iwlwifi
[/B]FATAL: Module iwlwifi not found.


> **dmesg | grep iwl**
[   16.137829] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   16.137832] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   17.120105] iwlagn 0000:04:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.120115] iwlagn 0000:04:00.0: setting latency timer to 64
[   17.120160] iwlagn 0000:04:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[   17.142057] iwlagn 0000:04:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   17.142191] iwlagn 0000:04:00.0: irq 47 for MSI/MSI-X
[   17.388532] iwlagn 0000:04:00.0: request for firmware file 'iwlwifi-5000-2.ucode' failed.
[   17.390747] iwlagn 0000:04:00.0: request for firmware file 'iwlwifi-5000-1.ucode' failed.
[   17.390844] iwlagn 0000:04:00.0: no suitable firmware found!
[   17.391435] iwlagn 0000:04:00.0: PCI INT A disabled


> **rfkill list all**
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no


---

### Post by chili555 on 2012-05-02
Are you sure you are booted into a 12.04 kernel?```
uname -r
```One of the significant changes in 12.04 is the change of iwlagn to iwlwifi. You obviously have the older, not the newer.

Here is a package with the firmware. Download it to your desktop. Right-click it and select *Extract Here*. Now open a terminal and do:```
sudo cp Desktop/iwl_firmware/* /lib/firmware
sudo modprobe -r iwlagn
sudo modprobe iwlagn
```You should be all set.

I am still mystified about your kernel version.

---

### Post by Toby on 2012-05-02
Ah! Thank you so much! You were right, btw. Not sure how this happened.
> 2.6.35-23-generic

Thank you so much for your help!

---

### Post by chili555 on 2012-05-02
Happy to help. Glad it's working. Have fun!!

---

### Post by faalhaas on 2012-05-13
Hi,

Was searching for this since the upgrate to 12.04. Helped me out there, now working on my Vaio Z11. Thanks for that!

Faalhaas

PS: Anyone know how to get the stamina/speed switch to get to work on a Z11?

---

### Post by mohitsa on 2012-11-21
> **chili555 said:**
> Boooo!

Please try this:```
sudo modprobe -r ndiswrapper
sudo modprobe iwlwifi
dmesg | grep iwl
rfkill list all
```These changes are temporary; if they work, we'll need to tweak a couple of files.


Thanks. I was having the same problem with my Dell Latitude E5400 with an Intel 5100 card. Could you please explain what iwlwifi does?

Thanks

---

### Post by chili555 on 2012-11-21
> **mohitsa said:**
> Thanks. I was having the same problem with my Dell Latitude E5400 with an Intel 5100 card. Could you please explain what iwlwifi does?

Thanks*iwlwifi* is the driver for your device. Is it not loading automatically on boot?

---

### Post by mohitsa on 2012-11-22
> **chili555 said:**
> *iwlwifi* is the driver for your device. Is it not loading automatically on boot?


You got it. Its not loading at boot time. How can I get it to load automatically? Sorry but I'm new to Linux.

---

### Post by chili555 on 2012-11-22
Sometimes I scare myself.

Please do:```
sudo su
echo iwlwifi >> /etc/modules
exit
```If it isn't fixed now, post back and we'll have a look.

---

### Post by mohitsa on 2012-11-24
> **chili555 said:**
> Sometimes I scare myself.

Please do:```
sudo su
echo iwlwifi >> /etc/modules
exit
```If it isn't fixed now, post back and we'll have a look.

Thanks. Its fixed now.

---

