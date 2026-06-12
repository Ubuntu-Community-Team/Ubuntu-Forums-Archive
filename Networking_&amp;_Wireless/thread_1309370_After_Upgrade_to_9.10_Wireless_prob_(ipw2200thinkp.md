---
title: "After Upgrade to 9.10: Wireless prob (ipw2200/thinkpad t43)"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by dankuoni on 2009-11-01
Wireless stopped working after upgrading to Karmic. Everything seems fine, but nm-applet tells me: "Wireless networks: device not ready" and the output of nm-tool is:
```
- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ipw2200
  State:             unavailable
  Default:           no
  HW Address:        00:12:F0:C7:95:D2

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points

```

Why is it unavailable?! I have no hardware switch!

Thanks for your help!
*dankuoni

1.) Machine Brand: 
```
IBM Thinkpad T43 2668-45G
```
2.) Output of lcpsi:
```
Network controller: Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection (rev 05)

```3.) Output of iwconfig:
```
eth1      unassociated  ESSID:off/any
          Mode:Managed  Channel=0  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
4.) Output of lsmod | grep ipw2200
```
ipw2200               140292  0
libipw                 43148  1 ipw2200
lib80211                6432  2 ipw2200,libipw

```
5.) Output of dmesg | grep ipw2200
```
[   20.907847] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   20.907851] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   20.907944] ipw2200 0000:0b:02.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   20.908039] ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
[   20.908089] ipw2200 0000:0b:02.0: firmware: requesting ipw2200-bss.fw
[   21.187460] ipw2200: Detected geography ZZE (13 802.11bg channels, 19 802.11a channels)

```
6.) Output of lshw:
```
      description: Wireless interface
       product: PRO/Wireless 2915ABG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:0b:02.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:c7:95:d2
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=unassociated
       resources: irq:21 memory:b4001000-b4001fff
```
7.) Output of iwlist scan:
```
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
pan0      Interface doesn't support scanning.
irda0     Interface doesn't support scanning.
eth1      No scan results

```
8.) Ubuntu version
```
Ubuntu 9.10
```
9.) Kernel
```
2.6.31-14-generic i686
```

---

### Post by anthony_barker on 2009-11-01
I have the same driver on thinkpad T42. Wifi works but drops quite frequently. Intel Corporation PRO/Wireless 2200BG

Need to reconnect manually every 30 minutes or so.

Kernel conflict?
Linux ant-laptop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/458577](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/458577)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/261886](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/261886)

---

### Post by jallen13 on 2010-03-03
I have the same problem. Except on a Thinkpad T42- identical wireless hardware.

I had 7.10 (Gutsy Gibbon) on my t42 and it worked right out of the box, nothing to configure.

I just upgraded my laptop to 9.10 (Clean wipe & reinstall of OS) and no wireless. :(  

Did anyone resolve this?

---

### Post by chili555 on 2010-03-03
How about letting us see:```
sudo modprobe ipw2200
dmesg | grep ipw
```Thanks.

---

### Post by Milos_SD on 2010-03-04
I have IBM ThinkPad T42 with that card and I can't get it working. Network manager says Wireless disconnected. And dmesg | grep ipw2200 show Firmware error detected. Restarting. That message spams syslog. I did modprobe ipw2200 with some debug option, and here is the dmesg output:
[http://pastebin.com/3jhWGNKz](http://pastebin.com/3jhWGNKz)

---

