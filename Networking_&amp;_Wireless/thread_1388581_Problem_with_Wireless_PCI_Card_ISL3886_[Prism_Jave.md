---
title: "Problem with Wireless PCI Card ISL3886 [Prism Javelin/Prism Xbow]"
date: 2010-01-23
forum: Networking &amp; Wireless
---

### Post by caiporaman on 2010-01-23
Hi everyone.

I have the pci ISL3886 [Prism Javelin/Prism Xbow], and yes, i can connect to wireless network but i can't connect to the internet.
In the WinXP works fine (with the driver on the cd).

I searched the forums and found this:
[B]
Ubuntu 7.10 - Installed ndiswrapper - Can't get wireless card working  [/B]
[http://ubuntuforums.org/showthread.php?t=587501](http://ubuntuforums.org/showthread.php?t=587501)

**[SOLVED] WLAN works with live CD but not when installed.**
[http://www.linuxformat.co.uk/forums/viewtopic.php?p=56311](http://www.linuxformat.co.uk/forums/viewtopic.php?p=56311)

**      Intersil 3886 ndiswrapper and iwconfig  **
**[B][http://ubuntuforums.org/showthread.php?t=35949](http://ubuntuforums.org/showthread.php?t=35949)**
[/B]
But none of these worked with me.

Informations: 

**lspci**
01:06.0 Network controller: Intersil Corporation ISL3886 [Prism Javelin/Prism Xbow] (rev 01)

**iwconfig**
wlan0     IEEE 802.11bg  ESSID:"******"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 00:23:69:5D:BF:2D   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:2D60-3163-EDD7-437D-43BD-8D05-0298-2EFC-D1DE-12BC-DB5A-EF3D-CC82-07CE-9382-EE2A [3]
          Power Management:off
          Link Quality=70/70  Signal level=-129 dBm  Noise level=-1 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

**modprobe  -l | grep 54**
kernel/drivers/serial/8250_exar_st16c554.ko
kernel/drivers/scsi/aha1542.ko
kernel/drivers/net/wireless/prism54/prism54.ko
kernel/drivers/net/wireless/p54/p54common.ko
kernel/drivers/net/wireless/p54/p54usb.ko
kernel/drivers/net/wireless/p54/p54pci.ko
kernel/drivers/net/wireless/p54/p54spi.ko
kernel/drivers/media/video/cx88/cx88-vp3054-i2c.ko
kernel/drivers/isdn/hisax/hisax_st5481.ko
kernel/drivers/edac/i5400_edac.ko
kernel/sound/pci/ali5451/snd-ali5451.ko
kernel/sound/pci/hda/snd-hda-codec-si3054.ko
kernel/net/ieee802154/nl802154.ko
kernel/net/ieee802154/af_802154.ko

**lshw -C network**
  *-network               
       description: Wireless interface
       product: ISL3886 [Prism Javelin/Prism Xbow]
       vendor: Intersil Corporation
       physical id: 6
       bus info: pci@0000:01:06.0
       logical name: wmaster0
       version: 01
       serial: 00:01:38:79:33:08
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=p54pci ip=****** latency=80 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:fb000000-fb001fff

more information needed?

Thanks!

Ps: Sorry for my ugly english =P

---

### Post by chili555 on 2010-01-23
Please let us see:```
ping -c3 74.125.47.103
cat /etc/resolv.conf
```Thanks.

---

### Post by Vyzygota on 2012-12-03
Hello,
I'm brand new user of Ubuntu 11.04 polish edition.
This post helps me to install my WLAN card but 
I see avalible networks but i can't connect to them.
I try different network settings (WPA/WPA2/TKIP/AES, B/G, mixed, etc) nothing helps.
Please help.

---

### Post by chili555 on 2012-12-03
The moderators hate posting to old threads. Please start your own new thread and include the result of this terminal command:```
lspci -nn | grep 0280
```

---

