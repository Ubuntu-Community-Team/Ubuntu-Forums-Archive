---
title: "wireless internet stopped working (ethernet still working)"
date: 2009-10-25
forum: Networking &amp; Wireless
---

### Post by crash123 on 2009-10-25
I just installed Ubuntu 9.04 a few days ago on my laptop (dual-booting with Vista). At first, my wireless was hit or miss; sometimes the built-in Intel card would pick up signals, sometimes my belkin expresscard would pick them up, sometimes both at the same time, sometimes neither, etc. Yesterday, the wireless just stopped working altogether, though ethernet works without a hitch. My wireless still works fine on Vista, though.

I´ve tried manually manually reconfiguring the network with xnetcardconfig. No luck. I´ve tried everything I can think of with Network Tools. No luck. I´ve looked all over the forums for a solution and have tried a few things but they haven´t helped. When I click on ¨connection information" after right-clcking on the empty four bars at the top of my screen, it says there are no valid active connections found. It seems like the computer recognizes them from what I see with iwconfig, and they have worked in the past, though intermittently. 

Any thoughts on what´s going on here? I´m new to linux and know* very* little about how it works.

Below is all of the info requested on the sticky. Tried to upload it as an attachment but was having problems for some reason. Let me know if there&#347; anything else I should tell you, and thanks for the help.

Machine/Model: Toshiba Satellite M4910
Ubuntu 9.04
Kernel architecture: 2.6.28-16-generic x86_64

Wireless Brand and info:

02:00.0 Network controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)
08:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100

Wireless interfaces:

iwconfig wlan0
wlan0     IEEE 802.11bgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

iwconfig wlan1
wlan1     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Modules (ones that seemed relevant from using lsmod):

ath9k                 310836  0 
iwlagn                114692  0 
iwlcore               129024  1 iwlagn
lbm_cw_mac80211       259000  3 iwlagn,iwlcore,ath9k
led_class              13064  2 iwlcore,ath9k
lbm_cw_cfg80211        85048  4 iwlagn,iwlcore,ath9k,lbm_cw_mac80211

Kernel info that seemed relevant from using dmesg:

[   12.863830] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[   12.863833] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   12.863952] iwlagn 0000:08:00.0: enabling device (0000 -> 0002)
[   12.863963] iwlagn 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.863978] iwlagn 0000:08:00.0: setting latency timer to 64
[   12.864044] iwlagn 0000:08:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
[   12.896210] iwlagn 0000:08:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[   12.896305] iwlagn 0000:08:00.0: irq 2298 for MSI/MSI-X
[   12.947296] phy0: Selected rate control algorithm 'ath9k_rate_control'
[   12.948037] Registered led device: ath9k-phy0::radio
[   12.948052] Registered led device: ath9k-phy0::assoc
[   12.948066] Registered led device: ath9k-phy0::tx
[   12.948079] Registered led device: ath9k-phy0::rx
[   12.948087] phy0: Atheros AR5418 MAC/BB Rev:2 AR2122 RF Rev:81: mem=0xffffc20010320000, irq=16
[   12.948211] cfg80211: Calling CRDA for country: CO
[   12.952860] cfg80211: Regulatory domain changed to country: CO
[   12.952864]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   12.952866]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   12.952868]     (5170000 KHz - 5250000 KHz @ 20000 KHz), (300 mBi, 1700 mBm)
[   12.952870]     (5250000 KHz - 5330000 KHz @ 20000 KHz), (300 mBi, 2300 mBm)
[   12.952872]     (5735000 KHz - 5835000 KHz @ 20000 KHz), (300 mBi, 3000 mBm)
[   12.962243] udev: renamed network interface wlan1 to wlan0
[   12.966358] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
[   13.009470] udev: renamed network interface wlan0_rename to wlan1
[   13.051532] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   13.051607] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   13.269137] lp: driver loaded but no devices found
[   13.355820] Adding 2192832k swap on /dev/sda6.  Priority:-1 extents:1 across:2192832k


Network config:

*-network               
       description: Wireless interface
       product: AR5008 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster1
       version: 01
       serial: 00:17:3f:5a:a6:67
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
*-network
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wmaster0
       version: 00
       serial: 00:22:fa:a1:3c:50
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn

Network scans:

wlan1     No scan results
wlan0     No scan results

Restarting my network:

sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                    There is already a pid file /var/run/dhclient.eth0.pid with pid 3533
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:17:3f:5a:a6:67
Sending on   LPF/wlan0/00:17:3f:5a:a6:67
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.wlan1.pid with pid 3589
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan1/00:22:fa:a1:3c:50
Sending on   LPF/wlan1/00:22:fa:a1:3c:50
Sending on   Socket/fallback
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan1/00:22:fa:a1:3c:50
Sending on   LPF/wlan1/00:22:fa:a1:3c:50
Sending on   Socket/fallback
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
 * if-up.d/mountnfs[wlan1]: waiting for interface wlan0 before doing NFS mounts
 * if-up.d/mountnfs[wlan1]: waiting for interface eth0 before doing NFS mounts
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:17:3f:5a:a6:67
Sending on   LPF/wlan0/00:17:3f:5a:a6:67
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
 * if-up.d/mountnfs[wlan0]: waiting for interface eth0 before doing NFS mounts
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhc](http://www.isc.org/sw/dhc)

---

### Post by crash123 on 2009-10-26
<bump> 

can anyone help here?

---

### Post by Iowan on 2009-10-26
Results of **ifconfig -a**? 
Wireless is still one of my weak areas. I don't see **wlan0** or **wlan1** in network config info, yet those are the interfaces **dhclient** is trying for address.
Does **lshw -C network** provide any new info?

Dunno if [this]("http://ubuntuforums.org/showpost.php?p=8094281&postcount=6") one provides any insight about **wmaster1**...

---

### Post by crash123 on 2009-10-26
Thanks for the help, Iowan. I've run **ifconfig -a** and **lshw -c network** and have attached the results here. I didn't see anything that stuck out to me, but then again, I'm pretty clueless. It *does* provide some info on wmaster1, if that helps.

---

### Post by Iowan on 2009-10-26
Wired is still working? The **avahi** addresses (169.254.*.*) usually indicates DHCP failure... all three interfaces have **avahi** addresses.  The link suggests you need to download a driver for the Intel card - something I haven't had to do (so I can't help). Dunno about the Atheros card - maybe there's more info on the forum.

---

### Post by crash123 on 2009-10-26
I should clarify that I don't have the ethernet hooked up right now. The router is in another room in the house, but over the weekend I tested things by hooking up to it through ethernet to see if the issue was wireless specific or not. Internet works flawlessly through ethernet when I hook it up.

I'm not sure from the link how to determine that I need a driver, but again, I'm still learning how to read all of this stuff. One of the many things I tried the other day was to download a driver for the Intel card to see if that made a difference. But the hardware installer didn't recognize anything with the download as a driver (keeps looking for .inf files, which weren't in the download), so that didn't work out. But it seems odd to me that either wireless card would have worked at all without a driver when I first installed Ubuntu, even though it had some issues. Maybe the updates screwed things up? I dunno.

Thanks for the help, though. I'll see if I can't find out more.

---

### Post by kevdog on 2009-10-26
Can you look at dmesg and post in your thread the relevant lines relating to either atheros, ath9k, or such topics.

---

### Post by crash123 on 2009-10-27
I've tried out dmesg and posted what looked relevant (athk9k starts showing up in the second section). Thanks for taking a look.

---

