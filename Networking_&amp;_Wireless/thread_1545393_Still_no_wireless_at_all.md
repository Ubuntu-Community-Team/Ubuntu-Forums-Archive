---
title: "Still no wireless at all"
date: 2010-08-03
forum: Networking &amp; Wireless
---

### Post by plzdontkillme11 on 2010-08-03
Hi,

I posted earlier, and I still have no wireless. I even reinstalled Ubuntu and restored my files but when I restarted I had no wireless yet again (it was working in the beginning). Under the Network Manager icon, there's not even a "Wireless Networks" option. It's just "wired network."

Here's all the info you need (hopefully):
```
 lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.5 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

``````
lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 002: ID 04f2:b070 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

``````
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:33:a8:96:ac  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: [fe80::21e:33ff:fea8:96ac/64]("http://fe80::21e:33ff:fea8:96ac/64") Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2125 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2334 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1376941 (1.3 MB)  TX bytes:526320 (526.3 KB)
          Interrupt:27 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:856 errors:0 dropped:0 overruns:0 frame:0
          TX packets:856 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:52600 (52.6 KB)  TX bytes:52600 (52.6 KB)

``````
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

``````
iwconfig wlan0
wlan0     No such device

``````
lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
oss_usb               104164  0 
oss_hdaudio           140744  0 
osscore               557813  2 oss_usb,oss_hdaudio
vga16fb                11385  0 
vgastate                8961  1 vga16fb
joydev                  8708  0 
i915                  285891  3 
drm_kms_helper         29297  1 i915
fbcon                  35102  71 
drm                   163034  4 i915,drm_kms_helper
tileblit                2031  1 fbcon
font                    7557  1 fbcon
i2c_algo_bit            5028  1 i915
bitblit                 4707  1 fbcon
video                  17375  1 i915
uvcvideo               57022  0 
softcursor              1189  1 bitblit
output                  1871  1 video
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
psmouse                63245  0 
intel_agp              24415  2 i915
agpgart                31788  2 drm,intel_agp
serio_raw               3978  0 
lp                      7028  0 
parport                32635  2 ppdev,lp
usb_storage            39457  0 
r8169                  34300  0 
mii                     438sudo lshw -C network
[sudo] password for vignesh: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:a8:96:ac
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.5 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:27 ioport:3000(size=256) memory:d0410000-d0410fff(prefetchable) memory:d0400000-d040ffff(prefetchable) memory:d0420000-d043ffff(prefetchable)
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list
       configuration: latency=0
       resources: memory:d4600000-d460ffff
1  1 r8169

```

iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


Help would be really appreciated. I've been trying to fix this for three days now.

Thanks in advance.

---

### Post by plzdontkillme11 on 2010-08-03
Oh, I forgot to mention, my laptop is a Toshiba Satelite L305.

---

### Post by arewethereyet on 2010-08-03
I'm looking around a little. Might want to try this out...


> **reed9 said:**
> 
[http://www.linuxforums.org/forum/wireless-internet/162669-built-card-cant-connect.html#post773488](http://www.linuxforums.org/forum/wireless-internet/162669-built-card-cant-connect.html#post773488)

Get yourself a wired connection and do
```
sudo apt-get install bcmwl-kernel-source
sudo modprobe -r ssb b43 wl
sudo modprobe wl

```

---

### Post by plzdontkillme11 on 2010-08-03
Thanks a lot for your reply, I'll get to that.

---

### Post by plzdontkillme11 on 2010-08-03
Um, I have an error:

```
sudo modprobe -r ssb b43 wl
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.

```

Same thing with the sudo modprobe wl.

---

### Post by arewethereyet on 2010-08-03
You don't by chance have a kill switch for your wireless somewhere on your laptop do you? or perhaps a a key combination that activates it(would likely show a wireless image below one of your keys)?

> **squid1230 said:**
> 
[http://www.linuxforums.org/forum/wireless-internet/163970-no-wireless-networks-atheros-ar5001-2.html#post780360](http://www.linuxforums.org/forum/wireless-internet/163970-no-wireless-networks-atheros-ar5001-2.html#post780360)
Jeebus! Mike Tbob you are a genius. You had me wondering why I didn't have a wireless switch like other laptops. Just when I was feeling rather inadequate I noticed under my F2 key a small wireless symbol. FN+F2 pressed, suddenly all the wireless networks appeared. Thank you for leading me to the solution.
Cheers mate!

---

### Post by plzdontkillme11 on 2010-08-03
Holy... wow. I don't know WHAT happened, lol. I pressed Fn+F8 (which is where the wireless symbol is) and didn't get any results. I was searching the forums, and voila, wireless networks popped up. Maybe a delayed reaction... 

Thank you SO much. Still annoyed that the answer was that simple! :p

---

