---
title: "Broadcom BCM4306"
date: 2009-04-10
forum: Networking &amp; Wireless
---

### Post by Hydem on 2009-04-10
Hi all,

I recently reinstalled Ubuntu on my laptop, it's a Dell Latitude D600, quite old but should do the trick. Anyway, I've got no problems except with my wireless card which doesn't want to work. I've been looking about everywhere for solutions but none have worked. Here is some output that I hope is useful (in no particular order):


sudo lsmod|grep -e b43 -e ssb -e ndiswrapper

```
ndiswrapper           196380  0 
b43legacy             128028  0 
rfkill                 17176  3 rfkill_input,b43legacy
mac80211              216820  1 b43legacy
led_class              12164  1 b43legacy
input_polldev          11912  1 b43legacy
ssb                    40580  1 b43legacy
usbcore               149488  4 ndiswrapper,uhci_hcd,ehci_hcd

```

ndiswrapper -l

```
bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: ssb)

```

lspci -nnm

```
02:03.0 "Network controller [0280]" "Broadcom Corporation [14e4]" "BCM4306 802.11b/g Wireless LAN Controller [4320]" -r02 "Dell [1028]" "Device [0001]"

```

lshw -C network

```
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:a1:aa:78
       width: 64 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 firmware=5705-v3.16 ip=192.168.1.68 latency=32 mingnt=64 module=tg3 multicast=yes
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:7e:a2:f4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: d6:c2:db:40:58:01
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

iwconfig

```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

```

sudo iwlist scan

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

pan0      Interface doesn't support scanning.


```

I've installed the restricted drivers and also done something with the b43 and b43legacy drivers. Ndiswrapper was also installed - all of them together might be causing more problems than solving.

Other than that, I'm all ears.

Thanks in advance

---

