---
title: "Linksys WUSB54Gv2 USB / Ubuntu 9.10 karmic koala / Dell Dimension 8200"
date: 2009-11-27
forum: Networking &amp; Wireless
---

### Post by danran on 2009-11-27
Dell Dimension 8200

Hi, I'm having issues getting my Linksys USB adapter (WUSB54Gv2) to work with Karmic Koala (Ubuntu 9.10). When I plug it in, it appears to be "seeing" all of the wireless networks but when I attempt to connect it times out (circle icon spins and spins in upper right corner of screen).

According to linux-wless.passys.nl, it is supported as in having a linux driver. So I dont need ndiswrapper. I downloaded the firmware and was going to place it in '/lib/firmware' but I see it is already there. 

dw@dw:/lib/firmware$ ls -la isl3887usb 
-rw-r--r-- 1 root root 29736 2009-10-17 15:55 isl3887usb

Below is some info I hope someone can understand and help me. It would be greatly appreciated!

lsusb:
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 13b1:000a Linksys 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

dw@dw:/lib/firmware$ ifconfig wlan1
wlan1     Link encap:Ethernet  HWaddr 00:0f:66:14:af:bf  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

dw@dw:/lib/firmware$ iwconfig wlan1
wlan1     IEEE 802.11bg  ESSID:"linksys"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

dw@dw:/lib/firmware$ lsmod
Module                  Size  Used by
zd1211rw               45408  0 
arc4                    1660  4 
ecb                     2524  4 
p54usb                 13980  0 
p54common              26336  1 p54usb
led_class               4096  1 p54common
mac80211              181236  3 zd1211rw,p54usb,p54common
cfg80211               93052  3 zd1211rw,p54common,mac80211
binfmt_misc             8356  1 
psmouse                56180  0 
serio_raw               5280  0 
dell_wmi                2564  0 
ppdev                   6688  0 
intel_rng               4444  0 
parport_pc             31940  1 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
dcdbas                  7292  0 
shpchp                 32272  0 
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
floppy                 54916  0 
intel_agp              27484  1 
agpgart                34988  1 intel_agp

lshw output:
  *-network:1
       description: Wireless interface
       physical id: 2
       logical name: wlan1
       serial: 00:0f:66:14:af:bf
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg


dw@dw:/lib/firmware$ iwlist scan
lo        Interface doesn't support scanning.

wmaster1  Interface doesn't support scanning.

wlan1     No scan results


dw@dw:/lib/firmware$ uname -mr
2.6.31-14-generic i686

dmesg output when unplugging and replugging usb wifi adapter:
[14600.920055] usb 1-1: USB disconnect, address 4
[14607.168020] usb 1-1: new full speed USB device using uhci_hcd and address 5
[14607.376301] usb 1-1: configuration #1 chosen from 1 choice
[14607.548023] usb 1-1: reset full speed USB device using uhci_hcd and address 5
[14607.687045] usb 1-1: firmware: requesting isl3887usb
[14607.693462] phy3: p54 detected a LM87 firmware
[14607.693468] p54: rx_mtu reduced from 3240 to 2384
[14607.693473] phy3: FW rev 2.13.24.0 - Softmac protocol 5.9
[14607.693478] phy3: cryptographic accelerator WEP:YES, TKIP:YES, CCMP:YES
[14608.716692] phy3: hwaddr 00:0f:66:14:af:bf, MAC:isl3887 RF:Frisbee
[14608.749489] phy3: Selected rate control algorithm 'minstrel'
[14608.750599] Registered led device: p54-phy3::assoc
[14608.750627] Registered led device: p54-phy3::tx
[14608.750654] Registered led device: p54-phy3::rx
[14608.750685] Registered led device: p54-phy3::radio
[14608.750699] usb 1-1: is registered as 'phy3'
[14608.816100] udev: renamed network interface wlan0 to wlan1
[14608.823214] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[14635.132046] phy3: failed to update LEDs.
[14635.304022] phy3: failed to update LEDs.

---

