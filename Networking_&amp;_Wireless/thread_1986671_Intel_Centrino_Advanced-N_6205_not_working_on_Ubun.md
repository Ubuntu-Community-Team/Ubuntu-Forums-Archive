---
title: "Intel Centrino Advanced-N 6205 not working on Ubuntu 10.04"
date: 2012-05-25
forum: Networking &amp; Wireless
---

### Post by pauloarras on 2012-05-25
Hello,

I am unable to make Wifi work on my Ubuntu laptop.

Here is the relevant info:

**1 ) Machine Brand and Model (PC/Laptop)**:
Laptop HP EliteBook 8460p

[B]2 ) Wireless Brand, Model and Wireless Chipset:
[/B]```
$ lspci -nn | grep -i Net
25:00.0 Network controller [0280]: Intel Corporation Device [8086:0085] (rev 34)
```Intel Centrino Advanced-N 6205

[B]3 ) check interface:
[/B]```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 10:1f:74:e3:26:b2  
          inet adr:164.129.122.122  Bcast:164.129.122.255  Masque:255.255.255.0
          adr inet6: fe80::121f:74ff:fee3:26b2/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:50311 erreurs:0 :0 overruns:0 frame:0
          TX packets:44072 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:33308388 (33.3 MB) Octets transmis:13660497 (13.6 MB)
          Interruption:20 Mémoire:d4500000-d4520000 

lo        Link encap:Boucle locale  
          inet adr:127.0.0.1  Masque:255.0.0.0
          adr inet6: ::1/128 Scope:Hôte
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          Packets reçus:1034 erreurs:0 :0 overruns:0 frame:0
          TX packets:1034 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:67020 (67.0 KB) Octets transmis:67020 (67.0 KB)

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.
```[B]4 ) Check for modules:
[/B]```
$ lsmod | grep iwlagn
``` returns nothing.

[B]5 ) Kernel boot messages
[/B]```
$ dmesg | grep -i iwl
``` returns nothing.

[B]6 ) Network configuration
[/B]```
$ lshw -C network
  *-network               
       description: Ethernet interface
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: 10:1f:74:e3:26:b2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=1.0.2-k4 firmware=0.13-4 ip=164.129.122.122 latency=0 multicast=yes
       resources: irq:20 memory:d4500000-d451ffff memory:d452a000-d452afff ioport:5020(size=32)
  *-network UNCLAIMED
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:25:00.0
       version: 34
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:d4100000-d4101fff 
```[B]7 ) Scan for networks:
[/B]```
$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.
```[B]8 ) Ubuntu Version: 
[/B]```
$ lsb_release -d
Description:    Ubuntu 10.04.4 LTS
```[B]9 ) Kernel/architecture (including 32 vs. 64 bit): 
[/B]```
$ uname -mr
2.6.35-32-generic x86_64
```Thanks in advance for your help!

---

### Post by chili555 on 2012-05-25
I suspect the problem you have is a rather new wireless adapter on a rather old Ubuntu version. I don't think the firmware you need was included in 10.04. As well, the pci.id 8086:0085 is not listed in iwlagn. I recommend you upgrade to 12.04. You seem to have the equipment to support it.

---

### Post by pauloarras on 2012-05-25
> **chili555 said:**
> I suspect the problem you have is a rather new wireless adapter on a rather old Ubuntu version. I don't think the firmware you need was included in 10.04. As well, the pci.id 8086:0085 is not listed in iwlagn. I recommend you upgrade to 12.04. You seem to have the equipment to support it.
Thanks for your reply.

Unfortunately, upgrading to 12.04 is not option for me (at least by now) since the laptop is provided by my company.

As regards the firmware, after inquiring into this I found on [http://intellinuxwireless.org/?n=Downloads](http://intellinuxwireless.org/?n=Downloads) that the relevant driver is iwlwifi-6000g2a-5.ucode and that it is present in /lib/firmware.
Furthermore, here is what I get from the following input:
```
$ sudo modprobe iwlagn

$ dmesg | grep iwl
899:[ 7639.776657] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
900:[ 7639.776667] iwlagn: Copyright(c) 2003-2010 Intel Corporation

$ modinfo iwlagn
filename:       /lib/modules/2.6.35-32-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
alias:          iwl4965
license:        GPL
author:         Copyright(c) 2003-2010 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
firmware:       iwlwifi-4965-2.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2a-4.ucode
firmware:       iwlwifi-6050-4.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-1000-3.ucode
srcversion:     91874136FCCE14B1F1909A4
alias:          pci:v00008086d00000084sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001226bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00000084sv*sd00001215bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001225bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00000083sv*sd00001205bc*sc*i*
alias:          pci:v00008086d00000089sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00000089sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00000087sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001221bc*sc*i*
alias:          pci:v00008086d00000085sv*sd00001211bc*sc*i*
alias:          pci:v00008086d00000082sv*sd00001201bc*sc*i*
alias:          pci:v00008086d00004239sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00004239sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00004238sv*sd00001111bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001326bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001321bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001307bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001306bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd00001301bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001121bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd00001101bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001316bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001216bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001311bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001211bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001321bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001221bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001306bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001206bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001301bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001201bc*sc*i*
alias:          pci:v00008086d0000423Bsv*sd00001011bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001021bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001001bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001114bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001014bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001111bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001011bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001104bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001004bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001101bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001001bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001124bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001024bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001121bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001021bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001215bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001314bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001214bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001211bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001226bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001225bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001324bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001224bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001221bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001205bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001304bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001204bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001201bc*sc*i*
alias:          pci:v00008086d00004230sv*sd*bc*sc*i*
alias:          pci:v00008086d00004229sv*sd*bc*sc*i*
depends:        iwlcore,cfg80211,mac80211
vermagic:       2.6.35-32-generic SMP mod_unload modversions 
parm:           swcrypto50:using crypto in software (default 0 [hardware]) (deprecated) (bool)
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           queues_num50:number of hw queues in 50xx series (deprecated) (int)
parm:           queues_num:number of hw queues. (int)
parm:           11n_disable50:disable 50XX 11n functionality (deprecated) (int)
parm:           11n_disable:disable 11n functionality (int)
parm:           amsdu_size_8K50:enable 8K amsdu size in 50XX series (deprecated) (int)
parm:           amsdu_size_8K:enable 8K amsdu size (int)
parm:           fw_restart50:restart firmware in case of error (deprecated) (int)
parm:           fw_restart:restart firmware in case of error (int)
parm:           disable_hw_scan:disable hardware scanning (default 0) (int)
parm:           ucode_alternative:specify ucode alternative to use from ucode file (int)

```

---

### Post by chili555 on 2012-05-25
> filename:       /lib/modules/[COLOR="Red"]2.6.35-32-generic[/COLOR]/kernel/drivers/net/wireless/iwlwifi/iwlagn.koMy fully updated 10.04 install has:> /lib/modules/[COLOR="Red"]2.6.32-41-generic[/COLOR]/kernel/drivers/net/wireless/iwlwifi/iwlagn.koYou obviously have a newer kernel and driver. I'm sorry if I made an error.

In any event, we wonder why the driver doesn't grab the device and create a wireless interface and connect. Your dmesg simply shows it loaded and sat down. Maybe we can see why. Let's check kernel messages for the PCI bus the card is on:```
dmesg | grep 25:00
dmesg | grep -i error
```Thanks.

---

### Post by pauloarras on 2012-05-25
Here is what I get from your input:
```
$ dmesg | grep 25:00
407:[    1.317516] pci 0000:25:00.0: reg 10: [mem 0xd4100000-0xd4101fff 64bit]
408:[    1.317787] pci 0000:25:00.0: PME# supported from D0 D3hot D3cold
409:[    1.317822] pci 0000:25:00.0: PME# disabled

$ dmesg | grep -i error
771:[   44.842182] lis3lv02d: probe of HPQ0004:00 failed with error -22
808:[   44.992138] EXT4-fs (dm-1): re-mounted. Opts: errors=remount-ro
```
Can you see any helpful info in this output?

---

### Post by chili555 on 2012-05-25
> Can you see any helpful info in this output?None, unfortunately. Would you please detach the ethernet cable, reboot so we have a clean slate and run:```
sudo modprobe iwlagn
dmesg > dmesg.txt
```Plug the ethernet back in and get a connection. Find the file dmesg.txt in your home directory. Paste it here and give us the link.

[http://paste.ubuntu.com/](http://paste.ubuntu.com/)

---

### Post by pauloarras on 2012-05-25
Here is the output from dmesg after reboot while Ethernet unplugged: [http://paste.ubuntu.com/1006597/](http://paste.ubuntu.com/1006597/)

Additionally, after running the modprobe command it complained about unresolved host...

---

