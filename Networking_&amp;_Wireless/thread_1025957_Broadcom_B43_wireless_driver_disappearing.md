---
title: "Broadcom B43 wireless driver disappearing"
date: 2008-12-30
forum: Networking &amp; Wireless
---

### Post by khaan on 2008-12-30
Hi,

I've got a quite freshly installed Ubuntu 8.10 Intrepid Ibex. I've just migrated from Debian, so the restricted drivers stuff is still quite a mystery to me.

I have a BCM4312 in my Dell Inspiron 1501 laptop.

In my Hardware Drivers list, I have the "Broadcom STA wireless driver" entry, but it does not seem to do the trick for me. The interface is up, but when trying to connect to a network it fails with "Association request to the driver failed" messages in /var/log/wpa_supplicant.

But also, in the Hardware Drivers list, there should be a "Broadcom B43 wireless driver" entry, but it happened to have disappeared. By disappeared, I mean that I remember it was there the first time I launched the Hardware Drivers manager (but I had no wi-fi network nearby, so I left it there for later). Also, today, I have been trying various tips from the forums, and that "Broadcom B43 wireless driver" entry re-appeared once (no idea what made it come back). I selected it, and it was the only time my wireless was working perfectly! I rebooted to see if it would remain so, and after reboot, the entry disappeared once again from the Hardware Drivers list, and my wireless has not been working since. I tried to redo the last steps I did before the entry reappeared, but no luck.

Also, having had some not-so-god experiences from my last system, I would rather like to avoid to have to use ndiswrapper.

So my question is: could someone tell me how to bring the "Broadcom B43 wireless driver" entry back to my Hardware Drivers list? Or at least could someone tell me how this Hardware Driver works: where does it look for the list of restricted drivers to display / to load?

Many thanks in advance!

---

### Post by kevdog on 2008-12-30
Can you do the following for me:

lsmod | grep -e wl -e b43
lshw -C network
lspci -nnm
modinfo b43
modinfo wl


Thanks - this should be an easy solution.

---

### Post by khaan on 2008-12-30
```
$ lsmod | grep -e wl -e b43
wl                   1076372  0 
ieee80211_crypt        13572  2 ieee80211_crypt_tkip,wl
```
```
$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 01
       serial: 00:19:7e:62:5f:7d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:6c:e4:8b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.2.3 latency=64 module=ssb multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 22:a5:a2:1f:e3:13
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
```
note: My ethernet interface is using b44, which I heard is known to conflict with lots of other drivers. On my previous system, I had to rmmod b44 when I wanted to use ndiswrapper. But this time, I tried to rmmod b44 and ssb, but it did not make my B43 restricted driver come back.
```
~$ lspci -nnm
00:00.0 "Host bridge [0600]" "ATI Technologies Inc [1002]" "RS480 Host Bridge [5950]" -r10 "Dell [1028]" "Device [01f5]"
00:01.0 "PCI bridge [0604]" "ATI Technologies Inc [1002]" "RS480 PCI Bridge [5a3f]" "" ""
00:05.0 "PCI bridge [0604]" "ATI Technologies Inc [1002]" "RS480 PCI Bridge [5a37]" "" ""
00:06.0 "PCI bridge [0604]" "ATI Technologies Inc [1002]" "RS480 PCI Bridge [5a38]" "" ""
00:12.0 "SATA controller [0106]" "ATI Technologies Inc [1002]" "SB600 Non-Raid-5 SATA [4380]" -p01 "Dell [1028]" "Device [01f5]"
00:13.0 "USB Controller [0c03]" "ATI Technologies Inc [1002]" "SB600 USB (OHCI0) [4387]" -p10 "Dell [1028]" "Device [01f5]"
00:13.1 "USB Controller [0c03]" "ATI Technologies Inc [1002]" "SB600 USB (OHCI1) [4388]" -p10 "Dell [1028]" "Device [01f5]"
00:13.2 "USB Controller [0c03]" "ATI Technologies Inc [1002]" "SB600 USB (OHCI2) [4389]" -p10 "Dell [1028]" "Device [01f5]"
00:13.3 "USB Controller [0c03]" "ATI Technologies Inc [1002]" "SB600 USB (OHCI3) [438a]" -p10 "Dell [1028]" "Device [01f5]"
00:13.4 "USB Controller [0c03]" "ATI Technologies Inc [1002]" "SB600 USB (OHCI4) [438b]" -p10 "Dell [1028]" "Device [01f5]"
00:13.5 "USB Controller [0c03]" "ATI Technologies Inc [1002]" "SB600 USB Controller (EHCI) [4386]" -p20 "Dell [1028]" "Device [01f5]"
00:14.0 "SMBus [0c05]" "ATI Technologies Inc [1002]" "SBx00 SMBus Controller [4385]" -r13 "Dell [1028]" "Device [01f5]"
00:14.1 "IDE interface [0101]" "ATI Technologies Inc [1002]" "SB600 IDE [438c]" -p8a "Dell [1028]" "Device [01f5]"
00:14.2 "Audio device [0403]" "ATI Technologies Inc [1002]" "SBx00 Azalia (Intel HDA) [4383]" "Dell [1028]" "Device [01f5]"
00:14.3 "ISA bridge [0601]" "ATI Technologies Inc [1002]" "SB600 PCI to LPC Bridge [438d]" "Dell [1028]" "Device [01f5]"
00:14.4 "PCI bridge [0604]" "ATI Technologies Inc [1002]" "SBx00 PCI to PCI Bridge [4384]" -p01 "" ""
00:18.0 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1100]" "" ""
00:18.1 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] Address Map [1101]" "" ""
00:18.2 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] DRAM Controller [1102]" "" ""
00:18.3 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] Miscellaneous Control [1103]" "" ""
01:05.0 "VGA compatible controller [0300]" "ATI Technologies Inc [1002]" "RS482 [Radeon Xpress 200M] [5975]" "Dell [1028]" "Device [01f5]"
05:00.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4312 802.11a/b/g [4312]" -r01 "Dell [1028]" "Device [0007]"
08:00.0 "Ethernet controller [0200]" "Broadcom Corporation [14e4]" "BCM4401-B0 100Base-TX [170c]" -r02 "Dell [1028]" "Device [01f5]"
08:01.0 "SD Host controller [0805]" "Ricoh Co Ltd [1180]" "R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [0822]" -r19 "Dell [1028]" "Device [01f5]"
08:01.1 "System peripheral [0880]" "Ricoh Co Ltd [1180]" "R5C843 MMC Host Controller [0843]" -r01 "Dell [1028]" "Device [01f5]"
```
```
$ modinfo b43
filename:       /lib/modules/2.6.27-9-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       FW13
license:        GPL
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     9B6D0D14CB834660F8EAC23
alias:          ssb:v4243id0812rev0D*
alias:          ssb:v4243id0812rev0B*
alias:          ssb:v4243id0812rev0A*
alias:          ssb:v4243id0812rev09*
alias:          ssb:v4243id0812rev07*
alias:          ssb:v4243id0812rev06*
alias:          ssb:v4243id0812rev05*
depends:        mac80211,ssb,input-polldev,led-class,rfkill
vermagic:       2.6.27-9-generic SMP mod_unload modversions 586 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistance (default on) (int)
```
```
$ modinfo wl
filename:       /lib/modules/2.6.27-9-generic/volatile/wl.ko
alias:          pci:v000014E4d0000432Dsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Csv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Asv*sd*bc*sc*i*
alias:          pci:v000014E4d00004329sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004328sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004315sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004313sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004312sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004311sv*sd*bc*sc*i*
depends:        ieee80211_crypt
vermagic:       2.6.27-9-generic SMP mod_unload modversions 586 
license:        MIXED/Proprietary
parm:           oneonly:int
parm:           piomode:int
parm:           nompc:int
parm:           name:string
```

---

### Post by kevdog on 2008-12-30
So for a temporary fix -- just to verify

sudo ifconfig eth1 down
sudo rmmod wl
sudo modprobe b43
sudo ifconfig eth1 up

You then need to connect to your network.  To verify that your card is using b43 rather than the wl(STA) driver, double check with lshw -C network and look for the driver= statement under the eth1 interface.

---

### Post by khaan on 2008-12-30
I get:
```
$ sudo ifconfig eth1 down
$ sudo rmmod wl
$ sudo modprobe b43
$ sudo ifconfig eth1 up
[COLOR="Red"]eth1: ERROR while getting interface flags: No such device[/COLOR]
```
eth1 disappeared:
```
$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:b9:6c:e4:8b  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::219:b9ff:fe6c:e48b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:761 errors:0 dropped:0 overruns:0 frame:0
          TX packets:813 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:804925 (804.9 KB)  TX bytes:103465 (103.4 KB)
          Interrupt:10 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)
```
b43 did load:
```
$ lsmod | grep b43
b43                   131356  0 
rfkill                 17176  1 b43
mac80211              216820  1 b43
led_class              12164  1 b43
input_polldev          11912  1 b43
ssb                    40580  2 b43,b44
```
however it did not register as the driver for the wireless interface:
```
$ lshw -C network
WARNING: you should run this program as super-user.
  *-network [COLOR="Red"]UNCLAIMED[/COLOR]     
       description: Network controller
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:6c:e4:8b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.2.3 latency=64 module=ssb multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 22:a5:a2:1f:e3:13
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
```

---

### Post by kevdog on 2008-12-30
Try this -- are you sure b43 is compatible with this device?

sudo rmmod b43 b44 ssb
sudo modprobe b43 b44

Then check lshw -C network to see if device was claimed.

---

### Post by khaan on 2008-12-31
Awesome!

That did the trick.
Then I unloaded the STA restricted driver, as it was not used in your solution. It was still working.
Upon reboot, wl did not load any more, b43 did load and claim the device and B43 had even reappeared in my Hardware Drivers list (already switched on). So it's now working even without having to script the unloading-reloading of the modules in the correct order.

Thanks very much!


I guess to sum up the whole issue, there seems to have a bug that the Hardware Driver does not detect that there is an unused B43 restricted driver as long as the STA restricted driver is switched on.

---

### Post by chenxiaolong on 2009-01-01
Hi

I have the exact same issue as Khaan and I was wondering what did you exactly do when you got it working? I followed all the steps mentioned, but wl still loads for me when I reboot. I also got the same outputs for the commands.

Thanks.

---

### Post by kevdog on 2009-01-01
I would try either uninstalling the driver or blacklisting the driver. This is done by:

echo "blacklist wl" | sudo tee -a /etc/modprobe.d/blacklist

I think wl is the name of the driver.  If it is something different substitute the name wl above for something else.

---

### Post by chenxiaolong on 2009-01-01
Thanks kevdog. That disabled the wl driver, but the b43 driver still won't work even though the Hardware Drivers dialog shows that it is enabled.

Thanks

---

### Post by chenxiaolong on 2009-01-01
This is my result of lshw -C Network after rebooting

> ~$ lshw -c Network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:73:21:c0:d0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 8a:91:de:4a:6c:4d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by kevdog on 2009-01-01
Can you list lspci -nnm

I just want to make sure your chipset is compatible with the b43 device.  This is of course unless you can tell me specifically you have used b43 in the past and it worked.

---

### Post by chenxiaolong on 2009-01-01
Yes, I have used b43 in the past.

> ~$ lspci -nnm
00:00.0 "RAM memory [0500]" "nVidia Corporation [10de]" "C51 Host Bridge [02f0]" -ra2 "Hewlett-Packard Company [103c]" "Device [30b7]"
00:00.1 "RAM memory [0500]" "nVidia Corporation [10de]" "C51 Memory Controller 0 [02fa]" -ra2 "Hewlett-Packard Company [103c]" "Device [30b7]"
00:00.2 "RAM memory [0500]" "nVidia Corporation [10de]" "C51 Memory Controller 1 [02fe]" -ra2 "Hewlett-Packard Company [103c]" "Device [30b7]"
00:00.3 "RAM memory [0500]" "nVidia Corporation [10de]" "C51 Memory Controller 5 [02f8]" -ra2 "Hewlett-Packard Company [103c]" "Device [30b7]"
00:00.4 "RAM memory [0500]" "nVidia Corporation [10de]" "C51 Memory Controller 4 [02f9]" -ra2 "Hewlett-Packard Company [103c]" "Device [30b7]"
00:00.5 "RAM memory [0500]" "nVidia Corporation [10de]" "C51 Host Bridge [02ff]" -ra2 "Hewlett-Packard Company [103c]" "Device [30b7]"
00:00.6 "RAM memory [0500]" "nVidia Corporation [10de]" "C51 Memory Controller 3 [027f]" -ra2 "Hewlett-Packard Company [103c]" "Device [30b7]"
00:00.7 "RAM memory [0500]" "nVidia Corporation [10de]" "C51 Memory Controller 2 [027e]" -ra2 "" ""
00:02.0 "PCI bridge [0604]" "nVidia Corporation [10de]" "C51 PCI Express Bridge [02fc]" -ra1 "" ""
00:03.0 "PCI bridge [0604]" "nVidia Corporation [10de]" "C51 PCI Express Bridge [02fd]" -ra1 "" ""
00:05.0 "VGA compatible controller [0300]" "nVidia Corporation [10de]" "C51 [Geforce 6150 Go] [0244]" -ra2 "Hewlett-Packard Company [103c]" "Device [30b7]"
00:09.0 "RAM memory [0500]" "nVidia Corporation [10de]" "MCP51 Host Bridge [0270]" -ra2 "Hewlett-Packard Company [103c]" "Device [30b7]"
00:0a.0 "ISA bridge [0601]" "nVidia Corporation [10de]" "MCP51 LPC Bridge [0260]" -ra3 "Hewlett-Packard Company [103c]" "Device [30b7]"
00:0a.1 "SMBus [0c05]" "nVidia Corporation [10de]" "MCP51 SMBus [0264]" -ra3 "Hewlett-Packard Company [103c]" "Device [30b7]"
00:0a.3 "Co-processor [0b40]" "nVidia Corporation [10de]" "MCP51 PMU [0271]" -ra3 "Hewlett-Packard Company [103c]" "Device [30b7]"
00:0b.0 "USB Controller [0c03]" "nVidia Corporation [10de]" "MCP51 USB Controller [026d]" -ra3 -p10 "Hewlett-Packard Company [103c]" "Device [30b7]"
00:0b.1 "USB Controller [0c03]" "nVidia Corporation [10de]" "MCP51 USB Controller [026e]" -ra3 -p20 "Hewlett-Packard Company [103c]" "Device [30b7]"
00:0d.0 "IDE interface [0101]" "nVidia Corporation [10de]" "MCP51 IDE [0265]" -rf1 -p8a "Unknown vendor [f03c]" "Device [30b7]"
00:0e.0 "IDE interface [0101]" "nVidia Corporation [10de]" "MCP51 Serial ATA Controller [0266]" -rf1 -p85 "Hewlett-Packard Company [103c]" "Device [30b7]"
00:10.0 "PCI bridge [0604]" "nVidia Corporation [10de]" "MCP51 PCI Bridge [026f]" -ra2 -p01 "" ""
00:10.1 "Audio device [0403]" "nVidia Corporation [10de]" "MCP51 High Definition Audio [026c]" -ra2 "Hewlett-Packard Company [103c]" "Device [30b7]"
00:14.0 "Bridge [0680]" "nVidia Corporation [10de]" "MCP51 Ethernet Controller [0269]" -ra3 "Hewlett-Packard Company [103c]" "Device [30b7]"
00:18.0 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1100]" "" ""
00:18.1 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] Address Map [1101]" "" ""
00:18.2 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] DRAM Controller [1102]" "" ""
00:18.3 "Host bridge [0600]" "Advanced Micro Devices [AMD] [1022]" "K8 [Athlon64/Opteron] Miscellaneous Control [1103]" "" ""
03:00.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4311 802.11b/g WLAN [4311]" -r01 "Hewlett-Packard Company [103c]" "Device [1363]"
07:05.0 "FireWire (IEEE 1394) [0c00]" "Ricoh Co Ltd [1180]" "R5C832 IEEE 1394 Controller [0832]" -p10 "Hewlett-Packard Company [103c]" "Device [30b7]"
07:05.1 "SD Host controller [0805]" "Ricoh Co Ltd [1180]" "R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [0822]" -r19 "Hewlett-Packard Company [103c]" "Device [30b7]"
07:05.2 "System peripheral [0880]" "Ricoh Co Ltd [1180]" "R5C843 MMC Host Controller [0843]" -r0a "Hewlett-Packard Company [103c]" "Device [30b7]"
07:05.3 "System peripheral [0880]" "Ricoh Co Ltd [1180]" "R5C592 Memory Stick Bus Host Adapter [0592]" -r05 "Hewlett-Packard Company [103c]" "Device [30b7]"
07:05.4 "System peripheral [0880]" "Ricoh Co Ltd [1180]" "xD-Picture Card Controller [0852]" -rff -pff "" ""


---

### Post by chenxiaolong on 2009-01-01
By the way, the Hardware Drivers dialog shows a that the b43 driver is activated, but my wireless light doesn't turn on (after rebooting the computer). I guessing the b43 driver isn't loading at startup.

---

### Post by chenxiaolong on 2009-01-01
lshw -C Network shows that it's using the b43 driver but it still doesn't work. 

> WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network:0 DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:73:21:c0:d0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 6a:60:26:57:6e:44
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


---

### Post by chenxiaolong on 2009-01-01
I typed in the command "sudo ifconfig wlan0 up" instead of "sudo ifconfig eth1 up" and my wireless card's light turned on, but it can't find any wireless networks. After than command, lshw -C Network now says:

> ~$ lshw -c Network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:73:21:c0:d0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: da:ef:f5:61:f6:ef
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


It shows that the wireless isn't diabled.

---

### Post by chenxiaolong on 2009-01-01
I ended up doing a reinstall because it was too much of a pain in the neck. But it works perfectly now.

---

### Post by Vimmander on 2010-07-25
I had a similar experience just now.  All I had to was remove the STA driver via Hardware Drivers, restart, and reinstall the B43 driver.  There's still the issue of having to do Fn+F2 to get it going, but at least it works

> **chenxiaolong said:**
> By the way, the Hardware Drivers dialog shows a that the b43 driver is activated, but my wireless light doesn't turn on (after rebooting the computer). I guessing the b43 driver isn't loading at startup.

I'd like to know if a workaround has been found for this.  It's very interesting, and since B43 is the open source driver, one  would expect a solution soon (unless I missed it in the technobable above :))

---

