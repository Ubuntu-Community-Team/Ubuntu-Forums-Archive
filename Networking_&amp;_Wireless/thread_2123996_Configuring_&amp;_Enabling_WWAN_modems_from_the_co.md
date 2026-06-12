---
title: "Configuring &amp; Enabling WWAN modems from the command line"
date: 2013-03-09
forum: Networking &amp; Wireless
---

### Post by BhimaPandava on 2013-03-09
I'm trying to set up a headless router based on Ubuntu 12.10 32bit Server.  I'm looking for information about how to enable and configure WWAN modems from the command line.  If it matters, I am using a Soekris Net6501 and I have both a Sierra Wireless MC7710 Mini-PCIe modem and a Huawei e398 USB stick modem. 

Thanks!

Some commonly requested information: 

uname -mr: 3.5.0-25-generic i686

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:00:24:cf:28:3c
          inet addr:192.168.178.29  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: fe80::200:24ff:fecf:283c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1451 errors:0 dropped:0 overruns:0 frame:0
          TX packets:778 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:137713 (137.7 KB)  TX bytes:110500 (110.5 KB)
          Interrupt:19 Memory:a1000000-a1020000


eth1      Link encap:Ethernet  HWaddr 00:00:24:cf:28:3d
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:a2000000-a2020000


eth2      Link encap:Ethernet  HWaddr 00:00:24:cf:28:3e
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:a3000000-a3020000


eth3      Link encap:Ethernet  HWaddr 00:00:24:cf:28:3f
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Memory:a4000000-a4020000


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1184 (1.1 KB)  TX bytes:1184 (1.1 KB)

```

usb-devices:
```
T:  Bus=01 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1199 ProdID=683c Rev=00.06
S:  Manufacturer=Sierra Wireless, Incorporated
S:  Product=MC7710
S:  SerialNumber=001027009999999
C:  #Ifs= 6 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=sierra
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=sierra
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=sierra
I:  If#= 3 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=sierra
I:  If#= 4 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=sierra
I:  If#= 7 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=sierra

```

lsmod:
```
Module                  Size  Used by
dm_crypt               22403  0
coretemp               13169  0
kvm_intel             126746  0
kvm                   357807  1 kvm_intel
gpio_sch               12929  0
ie6xx_wdt              13146  0
i2c_isch               12640  0
microcode              18210  0
lpc_sch                12728  0
sierra                 17899  1
usbserial              36684  4 sierra
pch_can                17717  0
can_dev                14638  1 pch_can
pch_phub               13034  0
gpio_pch               13046  0
shpchp                 32190  0
lp                     13300  0
parport                40754  1 lp
usb_storage            39351  1
e1000e                174780  0
sdhci_pci              18156  0
sdhci                  27831  1 sdhci_pci
pch_gbe                38053  0

```

modinfo sierra:
```
filename:       /lib/modules/3.5.0-25-generic/kernel/drivers/usb/serial/sierra.ko
license:        GPL
version:        v.1.7.16
description:    USB Driver for Sierra Wireless USB modems
author:         Kevin Lloyd, Elina Pasheva, Matthew Safar, Rory Filer
srcversion:     EC22CAE2DAF403FAF64E925
alias:          usb:v413Cp8133d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0F3Dp68A3d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0F3Dp68AAd*dc*dsc*dp*icFFiscFFipFF*
alias:          usb:v1199p68A3d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p68A2d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6893d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6892d*dc*dsc*dp*icFFiscFFipFF*
alias:          usb:v1199p6891d*dc*dsc*dp*icFFiscFFipFF*
alias:          usb:v1199p6890d*dc*dsc*dp*icFFiscFFipFF*
alias:          usb:v1199p6880d*dc*dsc*dp*icFFiscFFipFF*
alias:          usb:v1199p685Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6859d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6856d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6855d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6853d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6852d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6851d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6850d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p683Ed*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p683Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p683Cd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p683Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p683Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6839d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6838d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6835d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6834d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6833d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6832d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6822d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6821d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6820d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6816d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6815d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6813d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6812d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6809d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6808d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6805d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6804d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6803d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p6802d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0029d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0028d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0027d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0026d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0025d*dc*dsc*dp*icFFiscFFipFF*
alias:          usb:v1199p0023d*dc*dsc*dp*icFFiscFFipFF*
alias:          usb:v1199p0301d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0120d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0112d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0021d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0019d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0224d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0024d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0022d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0220d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0020d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0218d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0018d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p0017d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v03F0p1E1Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v03F0p211Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v03F0p1B1Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0F3Dp0112d*dc*dsc*dp*ic*isc*ip*
depends:        usbserial
intree:         Y
vermagic:       3.5.0-25-generic SMP mod_unload modversions 686
parm:           nmea:NMEA streaming (bool)
parm:           debug:Debug messages (bool)

```

modinfo sierra_net:
```
filename:       /lib/modules/3.5.0-25-generic/kernel/drivers/net/usb/sierra_net.ko
license:        GPL
version:        v.2.0
description:    USB-to-WWAN Driver for Sierra Wireless modems
author:         Paxton Smith, Matthew Safar, Rory Filer
srcversion:     B078278AF3F0563D9C51E5B
alias:          usb:v0F3Dp68AAd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p68AAd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0F3Dp68A3d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p68A3d*dc*dsc*dp*ic*isc*ip*
depends:        usbnet
intree:         Y
vermagic:       3.5.0-25-generic SMP mod_unload modversions 686

```

ls /dev/ttyUSB*
```
/dev/ttyUSB0  /dev/ttyUSB1  /dev/ttyUSB2  /dev/ttyUSB3  /dev/ttyUSB4  /dev/ttyUSB5




```nmcli nm status:
```
RUNNING         STATE           WIFI-HARDWARE   WIFI       WWAN-HARDWARE   WWAN
running         connected       enabled         enabled    enabled         disabled

```

nmcli dev status:
```
DEVICE     TYPE              STATE
ttyUSB3    gsm               disconnected
eth3       802-3-ethernet    unavailable
eth2       802-3-ethernet    unavailable
eth1       802-3-ethernet    unavailable
eth0       802-3-ethernet    connected

```

nmcli con:
```
NAME                      UUID                                   TYPE              TIMESTAMP-REAL
Wired connection 2        cb0e616f-492e-4dcb-a340-d04eb0c26e16   802-3-ethernet    Sun 10 Mar 2013 10:28:10 AM CET
Wired connection 1        c91056d8-bcca-4a33-aa96-cac53d0f5e83   802-3-ethernet    Sun 10 Mar 2013 10:28:10 AM CET
Ifupdown (eth0)           681b428f-beaf-8932-dce4-687ed5bae28e   802-3-ethernet    Sun 10 Mar 2013 10:43:13 AM CET
Wired connection 3        68cf999e-f957-441b-8502-01a1caa8c590   802-3-ethernet    Sun 10 Mar 2013 10:28:10 AM CET

```

---

### Post by bmork on 2013-03-21
> **BhimaPandava said:**
> I'm trying to set up a headless router based on Ubuntu 12.10 32bit Server.  I'm looking for information about how to enable and configure WWAN modems from the command line.  If it matters, I am using a Soekris Net6501 and I have both a Sierra Wireless MC7710 Mini-PCIe modem and a Huawei e398 USB stick modem. 


usb-devices:
```
T:  Bus=01 Lev=01 Prnt=01 Port=02 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1199 ProdID=683c Rev=00.06
S:  Manufacturer=Sierra Wireless, Incorporated
S:  Product=MC7710
S:  SerialNumber=001027009999999
C:  #Ifs= 6 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=sierra
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=sierra
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=sierra
I:  If#= 3 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=sierra
I:  If#= 4 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=sierra
I:  If#= 7 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=sierra

```


This was a bit surprising to me. I've so far only seen the MC7710 appear as 68a3 in DirectIP mode and 68a2 in QMI mode.  Do you happen to know why the ID is what it is here (like: you've set it to that value yourself :), or is this how you bought it?  If so, what was the product description?

Regardless of the above, this does look like a DirectIP mode.  Sierra Wireless us fixed interface numbers to identify different USB functions, and if#7 is normally a DirectIP function.  I therefore also was a bit surprised to see that the "sierra" serial driver had bound to it.  But looking at the driver now, I see that this is related to the unexpected ID.  The "sierra" driver only blacklists if#7 for IDs which are handled by the "sierra_net" driver, i.e. 1199:68a3, 0f3d:68a3 and 0f3d:68aa.

> 
modinfo sierra_net:
```
filename:       /lib/modules/3.5.0-25-generic/kernel/drivers/net/usb/sierra_net.ko
license:        GPL
version:        v.2.0
description:    USB-to-WWAN Driver for Sierra Wireless modems
author:         Paxton Smith, Matthew Safar, Rory Filer
srcversion:     B078278AF3F0563D9C51E5B
alias:          usb:v0F3Dp68AAd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p68AAd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0F3Dp68A3d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1199p68A3d*dc*dsc*dp*ic*isc*ip*
depends:        usbnet
intree:         Y
vermagic:       3.5.0-25-generic SMP mod_unload modversions 686

```


Yes, you will either have to change the product ID of the module (if acceptable), or add an entry for the current ID to both drivers.

If the module is generally available with that ID, and if#7 really is DirectIP, then I think we should fix the drivers.  Are you able to verify this?


> 

ls /dev/ttyUSB*
```
/dev/ttyUSB0  /dev/ttyUSB1  /dev/ttyUSB2  /dev/ttyUSB3  /dev/ttyUSB4  /dev/ttyUSB5




```nmcli nm status:
```
RUNNING         STATE           WIFI-HARDWARE   WIFI       WWAN-HARDWARE   WWAN
running         connected       enabled         enabled    enabled         disabled

```

nmcli dev status:
```
DEVICE     TYPE              STATE
ttyUSB3    gsm               disconnected
eth3       802-3-ethernet    unavailable
eth2       802-3-ethernet    unavailable
eth1       802-3-ethernet    unavailable
eth0       802-3-ethernet    connected

```

nmcli con:
```
NAME                      UUID                                   TYPE              TIMESTAMP-REAL
Wired connection 2        cb0e616f-492e-4dcb-a340-d04eb0c26e16   802-3-ethernet    Sun 10 Mar 2013 10:28:10 AM CET
Wired connection 1        c91056d8-bcca-4a33-aa96-cac53d0f5e83   802-3-ethernet    Sun 10 Mar 2013 10:28:10 AM CET
Ifupdown (eth0)           681b428f-beaf-8932-dce4-687ed5bae28e   802-3-ethernet    Sun 10 Mar 2013 10:43:13 AM CET
Wired connection 3        68cf999e-f957-441b-8502-01a1caa8c590   802-3-ethernet    Sun 10 Mar 2013 10:28:10 AM CET

```

Sorry, don't know enough about the finer details here.  Except that connecting in PPP mode should work if ttyUSB3 is one of the ports supporting that.   The easiest way to find out is probably using a terminal application like minicom.

But I assume you'll prefer to use this module in DirectIP or QMI mode to remove the PPP bottleneck, so let's try to find out how to best do that....

---

### Post by BhimaPandava on 2013-03-28
> **bmork said:**
> This was a bit surprising to me. I've so far only seen the MC7710 appear as 68a3 in DirectIP mode and 68a2 in QMI mode.  Do you happen to know why the ID is what it is here (like: you've set it to that value yourself :), or is this how you bought it?  If so, what was the product description?

Regardless of the above, this does look like a DirectIP mode.  Sierra Wireless us fixed interface numbers to identify different USB functions, and if#7 is normally a DirectIP function.  I therefore also was a bit surprised to see that the "sierra" serial driver had bound to it.  But looking at the driver now, I see that this is related to the unexpected ID.  The "sierra" driver only blacklists if#7 for IDs which are handled by the "sierra_net" driver, i.e. 1199:68a3, 0f3d:68a3 and 0f3d:68aa.



Yes, you will either have to change the product ID of the module (if acceptable), or add an entry for the current ID to both drivers.

If the module is generally available with that ID, and if#7 really is DirectIP, then I think we should fix the drivers.  Are you able to verify this?




Sorry, don't know enough about the finer details here.  Except that connecting in PPP mode should work if ttyUSB3 is one of the ports supporting that.   The easiest way to find out is probably using a terminal application like minicom.

But I assume you'll prefer to use this module in DirectIP or QMI mode to remove the PPP bottleneck, so let's try to find out how to best do that....

Hi!  Sorry for the late reply, somehow I missed the notification that I had a reply to my question.


In regards to my MC7710 having a odd device ID, I am not sure but I suspect this is because it is an engineering sample which I came by on happenstance.  So I do not think changing the drivers based on this MC7710 is really the best idea. I am more than happy to make whatever changes on my system that are required... but I am not sure how to make them.


I am interested in connecting both modems using command line tools which are appropriate for headless servers, like this router.  If possible I'd like to avoid having to use external 3rd party tools.  Besides the fact the sakis3G website routinely goes down for weeks or months, I am trying to workout a simple & repeatable automatic backup and recovery strategy.  Hopefully without having to disassemble the router & modems, so that I can connect them to another device, so that I can connect to the internet to fetch the files/configuration details/instructions I need to connect to the internet.  Lastly my goal is to bond these modems using Balance-RR. If I am generally correct with my assessments, then I think the most desirable configuration would be using QMI for both devices.  That now the MC7710 is using option drivers bothers me, I am not sure what exactly I did to make that happen... so I am not sure how to return to using the Sierra QMI drivers.


In the meantime I have been using Sakis3G and UTMSKeeper to connect with the Huawei USB modem and with just that modem it's been working as well as could be expected.  Unfortunately Sakis3G does not appear to be able to connect more than one device at a time.  I also have been getting PIN errors when I attempt to use Sakis3G to connect using the MC7710.  I had suspected that this was because I am using a SIM card socket which is connected by wrapping a flexible circuit cable over the relevant pins on the Mini-PCIe edge connector when inserting it into the Mini-PCIe socket on the motherboard... but now I wonder if there might be other problems with my current configuration.


So, if you have further insights or suggestions, I'd love to hear them!


Thanks!


The following is a snapshot of my current configuration which includes the  working Huawei USB modem:

ifconfig 
For clarification:
bond0 is configured for 802.2ad, comprises eth2 & eth3, and is connected to my Mac.
br0 comprises eth0 and wlan0 and is served by the DHCP server.
wlan0 and mon.wlan0 are created by hostapd and are connected to a USB Wifi dongle.
ppp0 is the huawei USB modem
eth1 is a static connection to another server


```

bond0     Link encap:Ethernet  HWaddr 00:00:24:cf:28:3f
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::200:24ff:fecf:283f/64 Scope:Link
          UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:53819 errors:0 dropped:6 overruns:0 frame:0
          TX packets:38498 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:19953246 (19.9 MB)  TX bytes:14662240 (14.6 MB)


br0       Link encap:Ethernet  HWaddr 00:00:24:cf:28:3c
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::200:24ff:fecf:283c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6480 errors:0 dropped:0 overruns:0 frame:0
          TX packets:245 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:272468 (272.4 KB)  TX bytes:85778 (85.7 KB)


eth0      Link encap:Ethernet  HWaddr 00:00:24:cf:28:3c
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6547 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:692 (692.0 B)  TX bytes:456042 (456.0 KB)
          Interrupt:19 Memory:a1000000-a1020000


eth1      Link encap:Ethernet  HWaddr 00:00:24:cf:28:3d
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::200:24ff:fecf:283d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:55 errors:0 dropped:0 overruns:0 frame:0
          TX packets:561 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4338 (4.3 KB)  TX bytes:117090 (117.0 KB)
          Interrupt:16 Memory:a2000000-a2020000


eth2      Link encap:Ethernet  HWaddr 00:00:24:cf:28:3f
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:33870 errors:0 dropped:6 overruns:0 frame:0
          TX packets:37208 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:12742693 (12.7 MB)  TX bytes:14494040 (14.4 MB)
          Interrupt:16 Memory:a3000000-a3020000


eth3      Link encap:Ethernet  HWaddr 00:00:24:cf:28:3f
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:19949 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1290 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:7210553 (7.2 MB)  TX bytes:168200 (168.2 KB)
          Interrupt:17 Memory:a4000000-a4020000


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:10031 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10031 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1237858 (1.2 MB)  TX bytes:1237858 (1.2 MB)


mon.wlan0 Link encap:UNSPEC  HWaddr 90-F6-52-15-2A-10-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9373 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2557885 (2.5 MB)  TX bytes:0 (0.0 B)


ppp0      Link encap:Point-to-Point Protocol
          inet addr:77.116.20.164  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:149490 errors:0 dropped:0 overruns:0 frame:0
          TX packets:234208 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:19660599 (19.6 MB)  TX bytes:284866033 (284.8 MB)


wlan0     Link encap:Ethernet  HWaddr 90:f6:52:15:2a:10
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6468 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6503 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:362304 (362.3 KB)  TX bytes:487988 (487.9 KB)

```


Relevant output from USB Devices


```

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ef(misc ) Sub=02 Prot=01 MxPS=64 #Cfgs=  1
P:  Vendor=12d1 ProdID=1506 Rev=00.00
S:  Manufacturer=Huawei Technologies
S:  Product=HUAWEI Mobile
C:  #Ifs= 7 Cfg#= 1 Atr=c0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=01 Prot=01 Driver=option
I:  If#= 1 Alt= 0 #EPs= 1 Cls=ff(vend.) Sub=01 Prot=09 Driver=qmi_wwan
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=01 Prot=08 Driver=qmi_wwan
I:  If#= 3 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=01 Prot=03 Driver=option
I:  If#= 4 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=01 Prot=02 Driver=option
I:  If#= 5 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage
I:  If#= 6 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage


T:  Bus=02 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1199 ProdID=683c Rev=00.06
S:  Manufacturer=Sierra Wireless, Incorporated
S:  Product=MC7710
S:  SerialNumber=001027009999999
C:  #Ifs= 6 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 4 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 7 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option


T:  Bus=02 Lev=01 Prnt=01 Port=02 Cnt=02 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=0bda ProdID=8176 Rev=02.00
S:  Manufacturer=Realtek
S:  Product=802.11n WLAN Adapter
S:  SerialNumber=00e04c000001
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 4 Cls=ff(vend.) Sub=ff Prot=ff Driver=rtl8192cu

```


lsmod:
```

Module                  Size  Used by
ppp_deflate            12806  0
zlib_deflate           26445  1 ppp_deflate
bsd_comp               12785  0
ppp_async              17205  1
crc_ccitt              12627  1 ppp_async
qmi_wwan               12771  0
cdc_wdm                17663  1 qmi_wwan
usbnet                 26567  1 qmi_wwan
usb_storage            43583  0
xt_conntrack           12664  2
iptable_filter         12706  1
ipt_MASQUERADE         12663  1
iptable_nat            12706  1
nf_conntrack_ipv4      14071  3
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
nf_nat_ipv4            13095  1 iptable_nat
nf_nat                 24952  3 ipt_MASQUERADE,nf_nat_ipv4,iptable_nat
nf_conntrack           67003  6 ipt_MASQUERADE,nf_nat,nf_nat_ipv4,xt_conntrack,iptable_nat,nf_conntrack_ipv4
ip_tables              17791  2 iptable_filter,iptable_nat
x_tables               21974  4 ip_tables,ipt_MASQUERADE,xt_conntrack,iptable_filter
8021q                  23328  0
garp                   14018  1 8021q
option                 29746  1
usb_wwan               14830  1 option
usbserial              27395  4 option,usb_wwan
bridge                 84113  0
stp                    12848  2 garp,bridge
llc                    14160  3 stp,garp,bridge
arc4                   12543  2
kvm_intel             126842  0
kvm                   376505  1 kvm_intel
ie6xx_wdt              13145  0
gpio_sch               12928  0
i2c_isch               12639  0
rtl8192cu              66659  0
rtlwifi                69015  1 rtl8192cu
rtl8192c_common        47075  1 rtl8192cu
mac80211              526481  3 rtlwifi,rtl8192c_common,rtl8192cu
microcode              18286  0
cfg80211              436177  2 mac80211,rtlwifi
lpc_sch                12727  0
pch_can                17716  0
can_dev                14969  1 pch_can
gpio_pch               13017  0
pch_phub               17132  0
shpchp                 32129  0
bonding                97248  0
coretemp               13131  0
lp                     13299  0
parport                40753  1 lp
pch_gbe                37980  0
ptp_pch                14468  1 pch_gbe
sdhci_pci              18158  0
sdhci                  31824  1 sdhci_pci
ptp                    18189  1 ptp_pch
ahci                   25507  2
pps_core               13736  1 ptp
libahci                26108  1 a

```


modinfo sierra
```

filename:       /lib/modules/3.8.0-13-generic/kernel/drivers/usb/serial/sierra.ko
license:        GPL
description:    USB Driver for Sierra Wireless USB modems
author:         Kevin Lloyd, Elina Pasheva, Matthew Safar, Rory Filer
srcversion:     CD77F4B43EF77DBB7858D95
alias:          usb:v413Cp8133d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0F3Dp68A3d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0F3Dp68AAd*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v1199p68A3d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1199p6893d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1199p6892d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v1199p6891d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v1199p6890d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v1199p6880d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v1199p685Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1199p6859d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1199p6856d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1199p6855d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1199p6853d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1199p6852d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1199p6851d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1199p6850d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1199p683Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1199p683Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1199p683Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1199p683Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1199p683Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1199p6839d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1199p6838d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1199p6835d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1199p6834d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1199p6833d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1199p6832d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1199p6822d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1199p6821d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1199p6820d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1199p6816d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1199p6815d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1199p6813d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1199p6812d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1199p6809d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1199p6808d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1199p6805d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1199p6804d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1199p6803d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1199p6802d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1199p0029d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1199p0028d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1199p0027d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1199p0026d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1199p0025d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v1199p0023d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v1199p0301d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1199p0120d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1199p0112d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1199p0021d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1199p0019d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1199p0224d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1199p0024d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1199p0022d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1199p0220d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1199p0020d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1199p0218d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1199p0018d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1199p0017d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v03F0p1E1Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v03F0p211Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v03F0p1B1Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0F3Dp0112d*dc*dsc*dp*ic*isc*ip*in*
depends:        usbserial
intree:         Y
vermagic:       3.8.0-13-generic SMP mod_unload modversions 686
parm:           nmea:NMEA streaming (bool)

```


modinfo sierra_net
```

filename:       /lib/modules/3.8.0-13-generic/kernel/drivers/net/usb/sierra_net.ko
license:        GPL
version:        v.2.0
description:    USB-to-WWAN Driver for Sierra Wireless modems
author:         Paxton Smith, Matthew Safar, Rory Filer
srcversion:     47D3ECE6A1D8C35CB055D88
alias:          usb:v0F3Dp68AAd*dc*dsc*dp*ic*isc*ip*in0B*
alias:          usb:v0F3Dp68AAd*dc*dsc*dp*ic*isc*ip*in0A*
alias:          usb:v0F3Dp68AAd*dc*dsc*dp*ic*isc*ip*in07*
alias:          usb:v1199p68AAd*dc*dsc*dp*ic*isc*ip*in0B*
alias:          usb:v1199p68AAd*dc*dsc*dp*ic*isc*ip*in0A*
alias:          usb:v1199p68AAd*dc*dsc*dp*ic*isc*ip*in07*
alias:          usb:v0F3Dp68A3d*dc*dsc*dp*ic*isc*ip*in0B*
alias:          usb:v0F3Dp68A3d*dc*dsc*dp*ic*isc*ip*in0A*
alias:          usb:v0F3Dp68A3d*dc*dsc*dp*ic*isc*ip*in07*
alias:          usb:v1199p68A3d*dc*dsc*dp*ic*isc*ip*in0B*
alias:          usb:v1199p68A3d*dc*dsc*dp*ic*isc*ip*in0A*
alias:          usb:v1199p68A3d*dc*dsc*dp*ic*isc*ip*in07*
depends:        usbnet
intree:         Y
vermagic:       3.8.0-13-generic SMP mod_unload modversions 686

```


ls /dev/
```

alarm          cpu/             loop2               null    ram13   rtc@      snd/     tty15  tty27  tty39  tty50  tty62      ttyS15  ttyS27   ttyUSB1  vcs3   vga_arbiter
ashmem         cpu_dma_latency  loop3               oldmem  ram14   rtc0      sr0      tty16  tty28  tty4   tty51  tty63      ttyS16  ttyS28   ttyUSB2  vcs4   vhost-net
autofs         disk/            loop4               port    ram15   sda       stderr@  tty17  tty29  tty40  tty52  tty7       ttyS17  ttyS29   ttyUSB3  vcs5   watchdog
binder         ecryptfs         loop5               ppp     ram2    sda1      stdin@   tty18  tty3   tty41  tty53  tty8       ttyS18  ttyS3    ttyUSB4  vcs6   watchdog0
block/         fd@              loop6               psaux   ram3    sda2      stdout@  tty19  tty30  tty42  tty54  tty9       ttyS19  ttyS30   ttyUSB5  vcs7   zero
bsg/           full             loop7               ptmx    ram4    sda5      tty      tty2   tty31  tty43  tty55  ttyprintk  ttyS2   ttyS31   ttyUSB6  vcsa
btrfs-control  fuse             loop-control        ptp0    ram5    sdb       tty0     tty20  tty32  tty44  tty56  ttyS0      ttyS20  ttyS4    ttyUSB7  vcsa1
bus/           input/           mapper/             pts/    ram6    serial/   tty1     tty21  tty33  tty45  tty57  ttyS1      ttyS21  ttyS5    ttyUSB8  vcsa2
cdc-wdm0       kmsg             mcelog              ram0    ram7    sg0       tty10    tty22  tty34  tty46  tty58  ttyS10     ttyS22  ttyS6    uinput   vcsa3
cdrom@         kvm              mem                 ram1    ram8    sg1       tty11    tty23  tty35  tty47  tty59  ttyS11     ttyS23  ttyS7    urandom  vcsa4
char/          log=             net/                ram10   ram9    sg2       tty12    tty24  tty36  tty48  tty6   ttyS12     ttyS24  ttyS8    vcs      vcsa5
console        loop0            network_latency     ram11   random  shm@      tty13    tty25  tty37  tty49  tty60  ttyS13     ttyS25  ttyS9    vcs1     vcsa6
core@          loop1            network_throughput  ram12   rfkill  snapshot  tty14    tty26  tty38  tty5   tty61  ttyS14     ttyS26  ttyUSB0  vcs2     vcsa7

```


Network Manager has been removed.

dmesg```
[    0.000000] Initializing cgroup subsys cpuset[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.8.0-13-generic (buildd@akateko) (gcc version 4.7.2 (Ubuntu/Linaro 4.7.2-22ubuntu4) ) #23-Ubuntu SMP Mon Mar 18 18:11:51 UTC 2013 (Ubuntu 3.8.0-13.23-generic 3.8.3)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009afff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009b000-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000f0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000007ffdffff] usable
[    0.000000] BIOS-e820: [mem 0x000000007ffe0000-0x000000007fffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fff00000-0x00000000ffffffff] reserved
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI not present or invalid.
[    0.000000] e820: update [mem 0x00000000-0x0000ffff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] e820: last_pfn = 0x7ffe0 max_arch_pfn = 0x1000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 disabled
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] found SMP MP-table at [mem 0x000fe100-0x000fe10f] mapped at [c00fe100]
[    0.000000] initial memory mapped: [mem 0x00000000-0x01ffffff]
[    0.000000] Base memory trampoline at [c0097000] 97000 size 16384
[    0.000000] init_memory_mapping: [mem 0x00000000-0x37bfdfff]
[    0.000000]  [mem 0x00000000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0x379fffff] page 2M
[    0.000000]  [mem 0x37a00000-0x37bfdfff] page 4k
[    0.000000] kernel direct mapping tables up to 0x37bfdfff @ [mem 0x01ffa000-0x01ffffff]
[    0.000000] RAMDISK: [mem 0x3616a000-0x370acfff]
[    0.000000] ACPI BIOS Bug: Error: A valid RSDP was not found (20121018/tbxfroot-218)
[    0.000000] 1155MB HIGHMEM available.
[    0.000000] 891MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 37bfe000
[    0.000000]   low ram: 0 - 37bfe000
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00010000-0x00ffffff]
[    0.000000]   Normal   [mem 0x01000000-0x37bfdfff]
[    0.000000]   HighMem  [mem 0x37bfe000-0x7ffdffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00010000-0x0009afff]
[    0.000000]   node   0: [mem 0x00100000-0x7ffdffff]
[    0.000000] On node 0 totalpages: 524139
[    0.000000] free_area_init_node: node 0, pgdat c18f6140, node_mem_map f516a200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3947 pages, LIFO batch:0
[    0.000000]   Normal zone: 1752 pages used for memmap
[    0.000000]   Normal zone: 222502 pages, LIFO batch:31
[    0.000000]   HighMem zone: 2312 pages used for memmap
[    0.000000]   HighMem zone: 293594 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] SFI: Simple Firmware Interface v0.81 http://simplefirmware.org
[    0.000000] Intel MultiProcessor Specification v1.4
[    0.000000]     Virtual Wire compatibility mode.
[    0.000000] MPTABLE: OEM ID: Soekris 
[    0.000000] MPTABLE: Product ID: net6501     
[    0.000000] MPTABLE: APIC at: 0xFEE00000
[    0.000000] Processor #0 (Bootup-CPU)
[    0.000000] Processor #1
[    0.000000] IOAPIC[0]: apic_id 0, version 32, address 0xfec00000, GSI 0-23
[    0.000000] Processors: 2
[    0.000000] smpboot: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009b000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] e820: [mem 0x80000000-0xfebfffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 14 pages/cpu @f7bd5000 s35008 r0 d22336 u57344
[    0.000000] pcpu-alloc: s35008 r0 d22336 u57344 alloc=14*4096
[    0.000000] pcpu-alloc: [0] 0 [0] 1 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 520043
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-13-generic root=UUID=4ddf2df2-ae9a-4e0a-9111-28975b66ede2 ro
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] __ex_table already sorted, skipping sort
[    0.000000] Initializing CPU#0
[    0.000000] allocated 4193920 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00037bfe:0007ffe0)
[    0.000000] Memory: 2048504k/2097024k available (6249k kernel code, 48052k reserved, 2976k data, 784k init, 1183624k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff14000 - 0xfffff000   ( 940 kB)
[    0.000000]     pkmap   : 0xffc00000 - 0xffe00000   (2048 kB)
[    0.000000]     vmalloc : 0xf83fe000 - 0xffbfe000   ( 120 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xf7bfe000   ( 891 MB)
[    0.000000]       .init : 0xc1903000 - 0xc19c7000   ( 784 kB)
[    0.000000]       .data : 0xc161a470 - 0xc19024c0   (2976 kB)
[    0.000000]       .text : 0xc1000000 - 0xc161a470   (6249 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] 	RCU restricting CPUs from NR_CPUS=8 to nr_cpu_ids=2.
[    0.000000] NR_IRQS:2304 nr_irqs:512 16
[    0.000000] CPU 0 irqstacks, hard=f4c08000 soft=f4c0a000
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.000000] tsc: Detected 1600.046 MHz processor
[    0.004003] Calibrating delay loop (skipped), value calculated using timer frequency.. 3200.09 BogoMIPS (lpj=6400184)
[    0.004028] pid_max: default: 32768 minimum: 301
[    0.004115] Security Framework initialized
[    0.004146] AppArmor: AppArmor initialized
[    0.004157] Yama: becoming mindful.
[    0.004281] Mount-cache hash table entries: 512
[    0.004703] Initializing cgroup subsys cpuacct
[    0.004719] Initializing cgroup subsys memory
[    0.004744] Initializing cgroup subsys devices
[    0.004757] Initializing cgroup subsys freezer
[    0.004769] Initializing cgroup subsys blkio
[    0.004782] Initializing cgroup subsys perf_event
[    0.004797] Initializing cgroup subsys hugetlb
[    0.004864] CPU: Physical Processor ID: 0
[    0.004877] CPU: Processor Core ID: 0
[    0.004889] mce: CPU supports 5 MCE banks
[    0.004912] CPU0: Thermal monitoring enabled (TM1)
[    0.004927] process: using mwait in idle threads
[    0.004955] Last level iTLB entries: 4KB 32, 2MB 0, 4MB 0
[    0.004955] Last level dTLB entries: 4KB 64, 2MB 0, 4MB 8
[    0.004955] tlb_flushall_shift: 6
[    0.008120] Freeing SMP alternatives: 24k freed
[    0.011894] ftrace: allocating 26106 entries in 51 pages
[    0.032201] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    0.032613] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.073681] smpboot: CPU0: Genuine Intel(R) CPU        @ 1.60GHz (fam: 06, model: 26, stepping: 01)
[    0.179980] Performance Events: PEBS fmt0+, 8-deep LBR, Atom events, Intel PMU driver.
[    0.180000] ... version:                3
[    0.180000] ... bit width:              40
[    0.180000] ... generic registers:      2
[    0.180000] ... value mask:             000000ffffffffff
[    0.180000] ... max period:             000000007fffffff
[    0.180000] ... fixed-purpose events:   3
[    0.180000] ... event mask:             0000000700000003
[    0.180000] CPU 1 irqstacks, hard=f4cd6000 soft=f4cd8000
[    0.180000] smpboot: Booting Node   0, Processors  #1 OK
[    0.008000] Initializing CPU#1
[    0.008000] Disabled fast string operations
[    0.192056] Brought up 2 CPUs
[    0.192089] smpboot: Total of 2 processors activated (6400.18 BogoMIPS)
[    0.192254] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.192853] devtmpfs: initialized
[    0.192853] EVM: security.selinux
[    0.192853] EVM: security.SMACK64
[    0.192853] EVM: security.capability
[    0.196482] regulator-dummy: no parameters
[    0.196648] NET: Registered protocol family 16
[    0.196974] EISA bus registered
[    0.197487] PCI : PCI BIOS area is rw and x. Use pci=nobios if you want it NX.
[    0.197511] PCI: PCI BIOS revision 2.01 entry at 0xfac61, last bus=13
[    0.197522] PCI: Using configuration type 1 for base access
[    0.200522] bio: create slab <bio-0> at 0
[    0.200522] ACPI: Interpreter disabled.
[    0.204032] vgaarb: loaded
[    0.204683] SCSI subsystem initialized
[    0.204720] libata version 3.00 loaded.
[    0.204720] usbcore: registered new interface driver usbfs
[    0.204720] usbcore: registered new interface driver hub
[    0.204720] usbcore: registered new device driver usb
[    0.204720] PCI: Probing PCI hardware
[    0.204720] PCI: root bus 00: using default resources
[    0.204720] PCI: Probing PCI hardware (bus 00)
[    0.204720] PCI host bridge to bus 0000:00
[    0.204720] pci_bus 0000:00: root bus resource [io  0x0000-0xffff]
[    0.204720] pci_bus 0000:00: root bus resource [mem 0x00000000-0xffffffff]
[    0.204720] pci_bus 0000:00: No busn resource found for root bus, will use [bus 00-ff]
[    0.204720] pci 0000:00:00.0: [8086:4114] type 00 class 0x060000
[    0.204720] pci 0000:00:01.0: [8086:8183] type 00 class 0x060000
[    0.204720] pci 0000:00:17.0: [8086:8184] type 01 class 0x060400
[    0.204720] pci 0000:00:17.0: PME# supported from D0 D3hot D3cold
[    0.204720] pci 0000:00:18.0: [8086:8185] type 01 class 0x060400
[    0.204720] pci 0000:00:18.0: PME# supported from D0 D3hot D3cold
[    0.204720] pci 0000:00:19.0: [8086:8180] type 01 class 0x060400
[    0.204764] pci 0000:00:19.0: PME# supported from D0 D3hot D3cold
[    0.204802] pci 0000:00:1a.0: [8086:8181] type 01 class 0x060400
[    0.204911] pci 0000:00:1a.0: PME# supported from D0 D3hot D3cold
[    0.204952] pci 0000:00:1f.0: [8086:8186] type 00 class 0x060100
[    0.205144] pci 0000:01:00.0: [8086:8800] type 01 class 0x060400
[    0.205204] pci 0000:01:00.0: reg 38: [mem 0x00000000-0x0000ffff pref]
[    0.205288] pci 0000:01:00.0: supports D1
[    0.205294] pci 0000:01:00.0: PME# supported from D0 D1 D3hot D3cold
[    0.212034] pci 0000:00:17.0: PCI bridge to [bus 01-02]
[    0.212053] pci 0000:00:17.0:   bridge window [io  0x1000-0x1fff]
[    0.212063] pci 0000:00:17.0:   bridge window [mem 0xa0000000-0xa0ffffff]
[    0.212172] pci 0000:02:00.0: [8086:8801] type 00 class 0xff0000
[    0.212234] pci 0000:02:00.0: reg 14: [mem 0xa0000000-0xa00007ff]
[    0.212330] pci 0000:02:00.0: reg 30: [mem 0x98000000-0x9801ffff pref]
[    0.212462] pci 0000:02:00.1: [8086:8802] type 00 class 0x020000
[    0.212508] pci 0000:02:00.1: reg 10: [io  0x1000-0x101f]
[    0.212532] pci 0000:02:00.1: reg 14: [mem 0xa0000800-0xa00009ff]
[    0.212709] pci 0000:02:00.1: PME# supported from D0
[    0.212764] pci 0000:02:00.2: [8086:8803] type 00 class 0xff0000
[    0.212827] pci 0000:02:00.2: reg 14: [mem 0xa0000a00-0xa0000a3f]
[    0.213003] pci 0000:02:00.2: PME# supported from D0
[    0.213074] pci 0000:02:02.0: [8086:8804] type 00 class 0x0c0310
[    0.213120] pci 0000:02:02.0: reg 10: [mem 0xa0000b00-0xa0000bff]
[    0.213313] pci 0000:02:02.0: PME# supported from D0 D3hot
[    0.213369] pci 0000:02:02.1: [8086:8805] type 00 class 0x0c0310
[    0.213414] pci 0000:02:02.1: reg 10: [mem 0xa0000c00-0xa0000cff]
[    0.213608] pci 0000:02:02.1: PME# supported from D0 D3hot
[    0.213662] pci 0000:02:02.2: [8086:8806] type 00 class 0x0c0310
[    0.213708] pci 0000:02:02.2: reg 10: [mem 0xa0000d00-0xa0000dff]
[    0.213901] pci 0000:02:02.2: PME# supported from D0 D3hot
[    0.213967] pci 0000:02:02.3: [8086:8807] type 00 class 0x0c0320
[    0.214018] pci 0000:02:02.3: reg 10: [mem 0xa0000e00-0xa0000eff]
[    0.214226] pci 0000:02:02.3: PME# supported from D0 D3hot
[    0.214286] pci 0000:02:02.4: [8086:8808] type 00 class 0x0c03fe
[    0.214349] pci 0000:02:02.4: reg 14: [mem 0xa0002000-0xa0003fff]
[    0.214525] pci 0000:02:02.4: PME# supported from D0
[    0.214591] pci 0000:02:04.0: [8086:8809] type 00 class 0x080501
[    0.214637] pci 0000:02:04.0: reg 10: [mem 0xa0004000-0xa00041ff]
[    0.214877] pci 0000:02:04.1: [8086:880a] type 00 class 0x080501
[    0.214923] pci 0000:02:04.1: reg 10: [mem 0xa0004200-0xa00043ff]
[    0.215194] pci 0000:02:06.0: [8086:880b] type 00 class 0x010601
[    0.215315] pci 0000:02:06.0: reg 20: [io  0x1020-0x103f]
[    0.215340] pci 0000:02:06.0: reg 24: [mem 0xa0004400-0xa00047ff]
[    0.215365] pci 0000:02:06.0: reg 30: [mem 0x98000000-0x9801ffff pref]
[    0.215519] pci 0000:02:08.0: [8086:880c] type 00 class 0x0c0310
[    0.215564] pci 0000:02:08.0: reg 10: [mem 0xa0004800-0xa00048ff]
[    0.215758] pci 0000:02:08.0: PME# supported from D0 D3hot
[    0.215814] pci 0000:02:08.1: [8086:880d] type 00 class 0x0c0310
[    0.215859] pci 0000:02:08.1: reg 10: [mem 0xa0004900-0xa00049ff]
[    0.216069] pci 0000:02:08.1: PME# supported from D0 D3hot
[    0.216125] pci 0000:02:08.2: [8086:880e] type 00 class 0x0c0310
[    0.216171] pci 0000:02:08.2: reg 10: [mem 0xa0004a00-0xa0004aff]
[    0.216365] pci 0000:02:08.2: PME# supported from D0 D3hot
[    0.216426] pci 0000:02:08.3: [8086:880f] type 00 class 0x0c0320
[    0.216476] pci 0000:02:08.3: reg 10: [mem 0xa0004b00-0xa0004bff]
[    0.216685] pci 0000:02:08.3: PME# supported from D0 D3hot
[    0.216765] pci 0000:02:0a.0: [8086:8810] type 00 class 0xff0000
[    0.216833] pci 0000:02:0a.0: reg 14: [mem 0xa0004c00-0xa0004cff]
[    0.217073] pci 0000:02:0a.1: [8086:8811] type 00 class 0x070002
[    0.217119] pci 0000:02:0a.1: reg 10: [io  0x1040-0x1047]
[    0.217143] pci 0000:02:0a.1: reg 14: [mem 0xa0004d00-0xa0004d0f]
[    0.217319] pci 0000:02:0a.1: PME# supported from D0
[    0.217374] pci 0000:02:0a.2: [8086:8812] type 00 class 0x070002
[    0.217420] pci 0000:02:0a.2: reg 10: [io  0x1048-0x104f]
[    0.217444] pci 0000:02:0a.2: reg 14: [mem 0xa0004d10-0xa0004d1f]
[    0.217664] pci 0000:02:0a.3: [8086:8813] type 00 class 0x070002
[    0.217710] pci 0000:02:0a.3: reg 10: [io  0x1050-0x1057]
[    0.217734] pci 0000:02:0a.3: reg 14: [mem 0xa0004d20-0xa0004d2f]
[    0.217953] pci 0000:02:0a.4: [8086:8814] type 00 class 0x070002
[    0.217999] pci 0000:02:0a.4: reg 10: [io  0x1058-0x105f]
[    0.218023] pci 0000:02:0a.4: reg 14: [mem 0xa0004d30-0xa0004d3f]
[    0.218261] pci 0000:02:0c.0: [8086:8815] type 00 class 0xff0000
[    0.218329] pci 0000:02:0c.0: reg 14: [mem 0xa0004e00-0xa0004eff]
[    0.218568] pci 0000:02:0c.1: [8086:8816] type 00 class 0x0c8000
[    0.218631] pci 0000:02:0c.1: reg 14: [mem 0xa0004f00-0xa0004f1f]
[    0.218858] pci 0000:02:0c.2: [8086:8817] type 00 class 0x0c8000
[    0.218923] pci 0000:02:0c.2: reg 14: [mem 0xa0005000-0xa00050ff]
[    0.219142] pci 0000:02:0c.3: [8086:8818] type 00 class 0x0c0900
[    0.219205] pci 0000:02:0c.3: reg 14: [mem 0xa0005200-0xa00053ff]
[    0.219425] pci 0000:02:0c.4: [8086:8819] type 00 class 0xff0000
[    0.219489] pci 0000:02:0c.4: reg 14: [mem 0xa0005400-0xa00054ff]
[    0.219750] pci 0000:01:00.0: PCI bridge to [bus 02]
[    0.219773] pci 0000:01:00.0:   bridge window [io  0x1000-0x1fff]
[    0.219783] pci 0000:01:00.0:   bridge window [mem 0xa0000000-0xa0ffffff]
[    0.219888] pci 0000:03:00.0: [111d:803a] type 01 class 0x060400
[    0.220039] pci 0000:03:00.0: PME# supported from D0 D3hot D3cold
[    0.228023] pci 0000:00:18.0: PCI bridge to [bus 03-07]
[    0.228041] pci 0000:00:18.0:   bridge window [io  0x2000-0x3fff]
[    0.228051] pci 0000:00:18.0:   bridge window [mem 0xa1000000-0xa2ffffff]
[    0.228145] pci 0000:04:02.0: [111d:803a] type 01 class 0x060400
[    0.228297] pci 0000:04:02.0: PME# supported from D0 D3hot D3cold
[    0.228351] pci 0000:04:03.0: [111d:803a] type 01 class 0x060400
[    0.228502] pci 0000:04:03.0: PME# supported from D0 D3hot D3cold
[    0.228559] pci 0000:04:04.0: [111d:803a] type 01 class 0x060400
[    0.228709] pci 0000:04:04.0: PME# supported from D0 D3hot D3cold
[    0.228805] pci 0000:03:00.0: PCI bridge to [bus 04-07]
[    0.228828] pci 0000:03:00.0:   bridge window [io  0x2000-0x3fff]
[    0.228838] pci 0000:03:00.0:   bridge window [mem 0xa1000000-0xa2ffffff]
[    0.228967] pci 0000:05:00.0: [8086:10d3] type 00 class 0x020000
[    0.229005] pci 0000:05:00.0: reg 10: [mem 0xa1000000-0xa101ffff]
[    0.229058] pci 0000:05:00.0: reg 18: [io  0x2000-0x201f]
[    0.229088] pci 0000:05:00.0: reg 1c: [mem 0xa1020000-0xa1023fff]
[    0.229304] pci 0000:05:00.0: PME# supported from D0 D3hot
[    0.229382] pci 0000:04:02.0: PCI bridge to [bus 05]
[    0.229405] pci 0000:04:02.0:   bridge window [io  0x2000-0x2fff]
[    0.229415] pci 0000:04:02.0:   bridge window [mem 0xa1000000-0xa1ffffff]
[    0.229548] pci 0000:06:00.0: [8086:10d3] type 00 class 0x020000
[    0.229587] pci 0000:06:00.0: reg 10: [mem 0xa2000000-0xa201ffff]
[    0.229640] pci 0000:06:00.0: reg 18: [io  0x3000-0x301f]
[    0.229670] pci 0000:06:00.0: reg 1c: [mem 0xa2020000-0xa2023fff]
[    0.229886] pci 0000:06:00.0: PME# supported from D0 D3hot
[    0.229963] pci 0000:04:03.0: PCI bridge to [bus 06]
[    0.229985] pci 0000:04:03.0:   bridge window [io  0x3000-0x3fff]
[    0.229996] pci 0000:04:03.0:   bridge window [mem 0xa2000000-0xa2ffffff]
[    0.230087] pci 0000:04:04.0: PCI bridge to [bus 07]
[    0.230237] pci 0000:08:00.0: [111d:803a] type 01 class 0x060400
[    0.230370] pci 0000:08:00.0: PME# supported from D0 D3hot D3cold
[    0.236021] pci 0000:00:19.0: PCI bridge to [bus 08-0c]
[    0.236039] pci 0000:00:19.0:   bridge window [io  0x4000-0x5fff]
[    0.236049] pci 0000:00:19.0:   bridge window [mem 0xa3000000-0xa4ffffff]
[    0.236142] pci 0000:09:02.0: [111d:803a] type 01 class 0x060400
[    0.236295] pci 0000:09:02.0: PME# supported from D0 D3hot D3cold
[    0.236349] pci 0000:09:03.0: [111d:803a] type 01 class 0x060400
[    0.236499] pci 0000:09:03.0: PME# supported from D0 D3hot D3cold
[    0.236556] pci 0000:09:04.0: [111d:803a] type 01 class 0x060400
[    0.236706] pci 0000:09:04.0: PME# supported from D0 D3hot D3cold
[    0.236802] pci 0000:08:00.0: PCI bridge to [bus 09-0c]
[    0.236825] pci 0000:08:00.0:   bridge window [io  0x4000-0x5fff]
[    0.236836] pci 0000:08:00.0:   bridge window [mem 0xa3000000-0xa4ffffff]
[    0.236964] pci 0000:0a:00.0: [8086:10d3] type 00 class 0x020000
[    0.237002] pci 0000:0a:00.0: reg 10: [mem 0xa3000000-0xa301ffff]
[    0.237056] pci 0000:0a:00.0: reg 18: [io  0x4000-0x401f]
[    0.237086] pci 0000:0a:00.0: reg 1c: [mem 0xa3020000-0xa3023fff]
[    0.237301] pci 0000:0a:00.0: PME# supported from D0 D3hot
[    0.237378] pci 0000:09:02.0: PCI bridge to [bus 0a]
[    0.237400] pci 0000:09:02.0:   bridge window [io  0x4000-0x4fff]
[    0.237411] pci 0000:09:02.0:   bridge window [mem 0xa3000000-0xa3ffffff]
[    0.237544] pci 0000:0b:00.0: [8086:10d3] type 00 class 0x020000
[    0.237582] pci 0000:0b:00.0: reg 10: [mem 0xa4000000-0xa401ffff]
[    0.237636] pci 0000:0b:00.0: reg 18: [io  0x5000-0x501f]
[    0.237666] pci 0000:0b:00.0: reg 1c: [mem 0xa4020000-0xa4023fff]
[    0.237882] pci 0000:0b:00.0: PME# supported from D0 D3hot
[    0.237959] pci 0000:09:03.0: PCI bridge to [bus 0b]
[    0.237981] pci 0000:09:03.0:   bridge window [io  0x5000-0x5fff]
[    0.237992] pci 0000:09:03.0:   bridge window [mem 0xa4000000-0xa4ffffff]
[    0.238083] pci 0000:09:04.0: PCI bridge to [bus 0c]
[    0.238214] pci 0000:00:1a.0: PCI bridge to [bus 0d]
[    0.238264] pci_bus 0000:00: busn_res: [bus 00-ff] end is updated to 0d
[    0.241250] pci 0000:00:1f.0: default IRQ router [8086:8186]
[    0.241281] PCI: pci_cache_line_size set to 64 bytes
[    0.241582] e820: reserve RAM buffer [mem 0x0009b000-0x0009ffff]
[    0.241589] e820: reserve RAM buffer [mem 0x7ffe0000-0x7fffffff]
[    0.241843] NetLabel: Initializing
[    0.241856] NetLabel:  domain hash size = 128
[    0.241865] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.241900] NetLabel:  unlabeled traffic allowed by default
[    0.241976] Switching to clocksource refined-jiffies
[    0.258290] AppArmor: AppArmor Filesystem Enabled
[    0.258365] pnp: PnP ACPI: disabled
[    0.258379] PnPBIOS: Scanning system for PnP BIOS support...
[    0.258559] PnPBIOS: PnP BIOS support was not detected.
[    0.260197] pci 0000:02:00.0: no compatible bridge window for [mem 0x98000000-0x9801ffff pref]
[    0.260234] pci 0000:02:06.0: no compatible bridge window for [mem 0x98000000-0x9801ffff pref]
[    0.260328] pci 0000:00:17.0: bridge window [mem 0x00100000-0x002fffff pref] to [bus 01-02] add_size 200000
[    0.260398] pci 0000:00:18.0: bridge window [mem 0x00100000-0x000fffff pref] to [bus 03-07] add_size 200000
[    0.260466] pci 0000:00:19.0: bridge window [mem 0x00100000-0x000fffff pref] to [bus 08-0c] add_size 200000
[    0.260478] pci 0000:00:1a.0: bridge window [io  0x1000-0x0fff] to [bus 0d] add_size 1000
[    0.260486] pci 0000:00:1a.0: bridge window [mem 0x00100000-0x000fffff pref] to [bus 0d] add_size 200000
[    0.260494] pci 0000:00:1a.0: bridge window [mem 0x00100000-0x000fffff] to [bus 0d] add_size 200000
[    0.260508] pci 0000:00:17.0: res[15]=[mem 0x00100000-0x002fffff pref] get_res_add_size add_size 200000
[    0.260516] pci 0000:00:18.0: res[15]=[mem 0x00100000-0x000fffff pref] get_res_add_size add_size 200000
[    0.260523] pci 0000:00:19.0: res[15]=[mem 0x00100000-0x000fffff pref] get_res_add_size add_size 200000
[    0.260530] pci 0000:00:1a.0: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[    0.260537] pci 0000:00:1a.0: res[15]=[mem 0x00100000-0x000fffff pref] get_res_add_size add_size 200000
[    0.260545] pci 0000:00:1a.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[    0.260561] pci 0000:00:17.0: BAR 15: assigned [mem 0x80000000-0x803fffff pref]
[    0.260581] pci 0000:00:18.0: BAR 15: assigned [mem 0x80400000-0x805fffff pref]
[    0.260600] pci 0000:00:19.0: BAR 15: assigned [mem 0x80600000-0x807fffff pref]
[    0.260619] pci 0000:00:1a.0: BAR 14: assigned [mem 0x80800000-0x809fffff]
[    0.260635] pci 0000:00:1a.0: BAR 15: assigned [mem 0x80a00000-0x80bfffff pref]
[    0.260654] pci 0000:00:1a.0: BAR 13: assigned [io  0x6000-0x6fff]
[    0.260672] pci 0000:01:00.0: BAR 15: assigned [mem 0x80000000-0x800fffff pref]
[    0.260690] pci 0000:01:00.0: BAR 6: assigned [mem 0x80100000-0x8010ffff pref]
[    0.264018] pci 0000:02:00.0: BAR 6: assigned [mem 0x80000000-0x8001ffff pref]
[    0.264038] pci 0000:02:06.0: BAR 6: assigned [mem 0x80020000-0x8003ffff pref]
[    0.264055] pci 0000:01:00.0: PCI bridge to [bus 02]
[    0.264070] pci 0000:01:00.0:   bridge window [io  0x1000-0x1fff]
[    0.264090] pci 0000:01:00.0:   bridge window [mem 0xa0000000-0xa0ffffff]
[    0.264108] pci 0000:01:00.0:   bridge window [mem 0x80000000-0x800fffff pref]
[    0.264133] pci 0000:00:17.0: PCI bridge to [bus 01-02]
[    0.264147] pci 0000:00:17.0:   bridge window [io  0x1000-0x1fff]
[    0.264164] pci 0000:00:17.0:   bridge window [mem 0xa0000000-0xa0ffffff]
[    0.264181] pci 0000:00:17.0:   bridge window [mem 0x80000000-0x803fffff pref]
[    0.264204] pci 0000:04:02.0: PCI bridge to [bus 05]
[    0.264219] pci 0000:04:02.0:   bridge window [io  0x2000-0x2fff]
[    0.264239] pci 0000:04:02.0:   bridge window [mem 0xa1000000-0xa1ffffff]
[    0.264265] pci 0000:04:03.0: PCI bridge to [bus 06]
[    0.264280] pci 0000:04:03.0:   bridge window [io  0x3000-0x3fff]
[    0.264300] pci 0000:04:03.0:   bridge window [mem 0xa2000000-0xa2ffffff]
[    0.264326] pci 0000:04:04.0: PCI bridge to [bus 07]
[    0.264358] pci 0000:03:00.0: PCI bridge to [bus 04-07]
[    0.264373] pci 0000:03:00.0:   bridge window [io  0x2000-0x3fff]
[    0.264392] pci 0000:03:00.0:   bridge window [mem 0xa1000000-0xa2ffffff]
[    0.264419] pci 0000:00:18.0: PCI bridge to [bus 03-07]
[    0.264433] pci 0000:00:18.0:   bridge window [io  0x2000-0x3fff]
[    0.264450] pci 0000:00:18.0:   bridge window [mem 0xa1000000-0xa2ffffff]
[    0.264467] pci 0000:00:18.0:   bridge window [mem 0x80400000-0x805fffff pref]
[    0.264490] pci 0000:09:02.0: PCI bridge to [bus 0a]
[    0.264504] pci 0000:09:02.0:   bridge window [io  0x4000-0x4fff]
[    0.264524] pci 0000:09:02.0:   bridge window [mem 0xa3000000-0xa3ffffff]
[    0.264550] pci 0000:09:03.0: PCI bridge to [bus 0b]
[    0.264565] pci 0000:09:03.0:   bridge window [io  0x5000-0x5fff]
[    0.264585] pci 0000:09:03.0:   bridge window [mem 0xa4000000-0xa4ffffff]
[    0.264611] pci 0000:09:04.0: PCI bridge to [bus 0c]
[    0.264643] pci 0000:08:00.0: PCI bridge to [bus 09-0c]
[    0.264657] pci 0000:08:00.0:   bridge window [io  0x4000-0x5fff]
[    0.264677] pci 0000:08:00.0:   bridge window [mem 0xa3000000-0xa4ffffff]
[    0.264704] pci 0000:00:19.0: PCI bridge to [bus 08-0c]
[    0.264717] pci 0000:00:19.0:   bridge window [io  0x4000-0x5fff]
[    0.264735] pci 0000:00:19.0:   bridge window [mem 0xa3000000-0xa4ffffff]
[    0.264752] pci 0000:00:19.0:   bridge window [mem 0x80600000-0x807fffff pref]
[    0.264773] pci 0000:00:1a.0: PCI bridge to [bus 0d]
[    0.264787] pci 0000:00:1a.0:   bridge window [io  0x6000-0x6fff]
[    0.264804] pci 0000:00:1a.0:   bridge window [mem 0x80800000-0x809fffff]
[    0.264821] pci 0000:00:1a.0:   bridge window [mem 0x80a00000-0x80bfffff pref]
[    0.264867] pci 0000:00:17.0: PCI->APIC IRQ transform: INT A -> IRQ 16
[    0.264896] pci 0000:01:00.0: using bridge 0000:00:17.0 INT A to get IRQ 16
[    0.264909] pci 0000:01:00.0: PCI->APIC IRQ transform: INT A -> IRQ 16
[    0.264935] pci 0000:00:18.0: PCI->APIC IRQ transform: INT A -> IRQ 17
[    0.264998] pci 0000:00:19.0: PCI->APIC IRQ transform: INT A -> IRQ 18
[    0.265060] pci 0000:00:1a.0: PCI->APIC IRQ transform: INT A -> IRQ 19
[    0.265076] pci_bus 0000:00: resource 4 [io  0x0000-0xffff]
[    0.265083] pci_bus 0000:00: resource 5 [mem 0x00000000-0xffffffff]
[    0.265090] pci_bus 0000:01: resource 0 [io  0x1000-0x1fff]
[    0.265096] pci_bus 0000:01: resource 1 [mem 0xa0000000-0xa0ffffff]
[    0.265103] pci_bus 0000:01: resource 2 [mem 0x80000000-0x803fffff pref]
[    0.265110] pci_bus 0000:02: resource 0 [io  0x1000-0x1fff]
[    0.265116] pci_bus 0000:02: resource 1 [mem 0xa0000000-0xa0ffffff]
[    0.265123] pci_bus 0000:02: resource 2 [mem 0x80000000-0x800fffff pref]
[    0.265130] pci_bus 0000:03: resource 0 [io  0x2000-0x3fff]
[    0.265136] pci_bus 0000:03: resource 1 [mem 0xa1000000-0xa2ffffff]
[    0.265143] pci_bus 0000:03: resource 2 [mem 0x80400000-0x805fffff pref]
[    0.265149] pci_bus 0000:04: resource 0 [io  0x2000-0x3fff]
[    0.265156] pci_bus 0000:04: resource 1 [mem 0xa1000000-0xa2ffffff]
[    0.265162] pci_bus 0000:05: resource 0 [io  0x2000-0x2fff]
[    0.265169] pci_bus 0000:05: resource 1 [mem 0xa1000000-0xa1ffffff]
[    0.265175] pci_bus 0000:06: resource 0 [io  0x3000-0x3fff]
[    0.265182] pci_bus 0000:06: resource 1 [mem 0xa2000000-0xa2ffffff]
[    0.265189] pci_bus 0000:08: resource 0 [io  0x4000-0x5fff]
[    0.265195] pci_bus 0000:08: resource 1 [mem 0xa3000000-0xa4ffffff]
[    0.265202] pci_bus 0000:08: resource 2 [mem 0x80600000-0x807fffff pref]
[    0.265208] pci_bus 0000:09: resource 0 [io  0x4000-0x5fff]
[    0.265215] pci_bus 0000:09: resource 1 [mem 0xa3000000-0xa4ffffff]
[    0.265222] pci_bus 0000:0a: resource 0 [io  0x4000-0x4fff]
[    0.265228] pci_bus 0000:0a: resource 1 [mem 0xa3000000-0xa3ffffff]
[    0.265235] pci_bus 0000:0b: resource 0 [io  0x5000-0x5fff]
[    0.265241] pci_bus 0000:0b: resource 1 [mem 0xa4000000-0xa4ffffff]
[    0.265248] pci_bus 0000:0d: resource 0 [io  0x6000-0x6fff]
[    0.265254] pci_bus 0000:0d: resource 1 [mem 0x80800000-0x809fffff]
[    0.265261] pci_bus 0000:0d: resource 2 [mem 0x80a00000-0x80bfffff pref]
[    0.265344] NET: Registered protocol family 2
[    0.265687] TCP established hash table entries: 8192 (order: 4, 65536 bytes)
[    0.265760] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.265826] TCP: Hash tables configured (established 8192 bind 8192)
[    0.265892] TCP: reno registered
[    0.265907] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.265932] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.266077] NET: Registered protocol family 1
[    0.266187] pci 0000:01:00.0: using bridge 0000:00:17.0 INT D to get IRQ 19
[    0.266203] pci 0000:02:02.0: PCI->APIC IRQ transform: INT D -> IRQ 19
[    0.266292] pci 0000:01:00.0: using bridge 0000:00:17.0 INT D to get IRQ 19
[    0.266307] pci 0000:02:02.1: PCI->APIC IRQ transform: INT D -> IRQ 19
[    0.266368] pci 0000:01:00.0: using bridge 0000:00:17.0 INT D to get IRQ 19
[    0.266383] pci 0000:02:02.2: PCI->APIC IRQ transform: INT D -> IRQ 19
[    0.266440] pci 0000:01:00.0: using bridge 0000:00:17.0 INT D to get IRQ 19
[    0.266454] pci 0000:02:02.3: PCI->APIC IRQ transform: INT D -> IRQ 19
[    0.267550] pci 0000:01:00.0: using bridge 0000:00:17.0 INT A to get IRQ 16
[    0.267565] pci 0000:02:08.0: PCI->APIC IRQ transform: INT A -> IRQ 16
[    0.267622] pci 0000:01:00.0: using bridge 0000:00:17.0 INT A to get IRQ 16
[    0.267637] pci 0000:02:08.1: PCI->APIC IRQ transform: INT A -> IRQ 16
[    0.267692] pci 0000:01:00.0: using bridge 0000:00:17.0 INT A to get IRQ 16
[    0.267707] pci 0000:02:08.2: PCI->APIC IRQ transform: INT A -> IRQ 16
[    0.267763] pci 0000:01:00.0: using bridge 0000:00:17.0 INT A to get IRQ 16
[    0.267777] pci 0000:02:08.3: PCI->APIC IRQ transform: INT A -> IRQ 16
[    0.268544] PCI: CLS 32 bytes, default 64
[    0.268676] Trying to unpack rootfs image as initramfs...
[    0.948559] Freeing initrd memory: 15628k freed
[    0.969112] platform rtc_cmos: registered platform RTC device (no PNP device found)
[    0.969432] Initialise module verification
[    0.969432] audit: initializing netlink socket (disabled)
[    0.969432] type=2000 audit(1364636582.968:1): initialized
[    1.016915] bounce pool size: 64 pages
[    1.016915] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.020757] VFS: Disk quotas dquot_6.5.2
[    1.020757] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.021498] fuse init (API version 7.20)
[    1.021498] msgmni has been set to 1719
[    1.021498] Key type asymmetric registered
[    1.021498] Asymmetric key parser 'x509' registered
[    1.021498] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.024080] io scheduler noop registered
[    1.024098] io scheduler deadline registered (default)
[    1.024131] io scheduler cfq registered
[    1.025238] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.025285] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.025425] intel_idle: MWAIT substates: 0x3020220
[    1.025455] intel_idle: v0.4 model 0x26
[    1.025460] intel_idle: lapic_timer_reliable_states 0x2
[    1.025465] tsc: Marking TSC unstable due to TSC halts in idle states deeper than C2
[    1.025556] isapnp: Scanning for PnP cards...
[    1.025556] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.025556] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a TI16750
[    1.028421] pci 0000:01:00.0: using bridge 0000:00:17.0 INT D to get IRQ 19
[    1.028445] serial 0000:02:0a.1: PCI->APIC IRQ transform: INT D -> IRQ 19
[    1.028568] pci 0000:01:00.0: using bridge 0000:00:17.0 INT D to get IRQ 19
[    1.028587] serial 0000:02:0a.2: PCI->APIC IRQ transform: INT D -> IRQ 19
[    1.028703] pci 0000:01:00.0: using bridge 0000:00:17.0 INT D to get IRQ 19
[    1.028722] serial 0000:02:0a.3: PCI->APIC IRQ transform: INT D -> IRQ 19
[    1.028836] pci 0000:01:00.0: using bridge 0000:00:17.0 INT D to get IRQ 19
[    1.028855] serial 0000:02:0a.4: PCI->APIC IRQ transform: INT D -> IRQ 19
[    1.029360] Linux agpgart interface v0.103
[    1.034007] brd: module loaded
[    1.036388] loop: module loaded
[    1.037669] libphy: Fixed MDIO Bus: probed
[    1.037919] tun: Universal TUN/TAP device driver, 1.6
[    1.037934] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.038070] PPP generic driver version 2.4.2
[    1.038191] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.038208] ehci-pci: EHCI PCI platform driver
[    1.038271] pci 0000:01:00.0: using bridge 0000:00:17.0 INT D to get IRQ 19
[    1.038291] ehci-pci 0000:02:02.3: PCI->APIC IRQ transform: INT D -> IRQ 19
[    1.038352] ehci-pci 0000:02:02.3: setting latency timer to 64
[    1.038363] ehci-pci 0000:02:02.3: EHCI Host Controller
[    1.038396] ehci-pci 0000:02:02.3: new USB bus registered, assigned bus number 1
[    1.038502] ehci-pci 0000:02:02.3: cache line size of 32 is not supported
[    1.038532] ehci-pci 0000:02:02.3: irq 19, io mem 0xa0000e00
[    1.048085] ehci-pci 0000:02:02.3: USB 2.0 started, EHCI 1.00
[    1.048174] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.048193] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.048214] usb usb1: Product: EHCI Host Controller
[    1.048229] usb usb1: Manufacturer: Linux 3.8.0-13-generic ehci_hcd
[    1.048245] usb usb1: SerialNumber: 0000:02:02.3
[    1.048562] hub 1-0:1.0: USB hub found
[    1.048585] hub 1-0:1.0: 3 ports detected
[    1.048880] pci 0000:01:00.0: using bridge 0000:00:17.0 INT A to get IRQ 16
[    1.048900] ehci-pci 0000:02:08.3: PCI->APIC IRQ transform: INT A -> IRQ 16
[    1.048949] ehci-pci 0000:02:08.3: setting latency timer to 64
[    1.048960] ehci-pci 0000:02:08.3: EHCI Host Controller
[    1.048990] ehci-pci 0000:02:08.3: new USB bus registered, assigned bus number 2
[    1.049086] ehci-pci 0000:02:08.3: cache line size of 32 is not supported
[    1.049113] ehci-pci 0000:02:08.3: irq 16, io mem 0xa0004b00
[    1.060085] ehci-pci 0000:02:08.3: USB 2.0 started, EHCI 1.00
[    1.060163] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.060183] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.060203] usb usb2: Product: EHCI Host Controller
[    1.060218] usb usb2: Manufacturer: Linux 3.8.0-13-generic ehci_hcd
[    1.060235] usb usb2: SerialNumber: 0000:02:08.3
[    1.060519] hub 2-0:1.0: USB hub found
[    1.060541] hub 2-0:1.0: 3 ports detected
[    1.060855] ehci-platform: EHCI generic platform driver
[    1.060895] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.060969] pci 0000:01:00.0: using bridge 0000:00:17.0 INT D to get IRQ 19
[    1.060988] ohci_hcd 0000:02:02.0: PCI->APIC IRQ transform: INT D -> IRQ 19
[    1.061041] ohci_hcd 0000:02:02.0: setting latency timer to 64
[    1.061052] ohci_hcd 0000:02:02.0: OHCI Host Controller
[    1.061078] ohci_hcd 0000:02:02.0: new USB bus registered, assigned bus number 3
[    1.061130] ohci_hcd 0000:02:02.0: irq 19, io mem 0xa0000b00
[    1.120116] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.120137] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.120158] usb usb3: Product: OHCI Host Controller
[    1.120173] usb usb3: Manufacturer: Linux 3.8.0-13-generic ohci_hcd
[    1.120190] usb usb3: SerialNumber: 0000:02:02.0
[    1.120489] hub 3-0:1.0: USB hub found
[    1.120516] hub 3-0:1.0: 1 port detected
[    1.120725] pci 0000:01:00.0: using bridge 0000:00:17.0 INT D to get IRQ 19
[    1.120745] ohci_hcd 0000:02:02.1: PCI->APIC IRQ transform: INT D -> IRQ 19
[    1.120797] ohci_hcd 0000:02:02.1: setting latency timer to 64
[    1.120808] ohci_hcd 0000:02:02.1: OHCI Host Controller
[    1.120839] ohci_hcd 0000:02:02.1: new USB bus registered, assigned bus number 4
[    1.120891] ohci_hcd 0000:02:02.1: irq 19, io mem 0xa0000c00
[    1.180112] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.180134] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.180154] usb usb4: Product: OHCI Host Controller
[    1.180170] usb usb4: Manufacturer: Linux 3.8.0-13-generic ohci_hcd
[    1.180186] usb usb4: SerialNumber: 0000:02:02.1
[    1.180475] hub 4-0:1.0: USB hub found
[    1.180501] hub 4-0:1.0: 1 port detected
[    1.180700] pci 0000:01:00.0: using bridge 0000:00:17.0 INT D to get IRQ 19
[    1.180720] ohci_hcd 0000:02:02.2: PCI->APIC IRQ transform: INT D -> IRQ 19
[    1.180765] ohci_hcd 0000:02:02.2: setting latency timer to 64
[    1.180775] ohci_hcd 0000:02:02.2: OHCI Host Controller
[    1.180801] ohci_hcd 0000:02:02.2: new USB bus registered, assigned bus number 5
[    1.180860] ohci_hcd 0000:02:02.2: irq 19, io mem 0xa0000d00
[    1.240115] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.240137] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.240157] usb usb5: Product: OHCI Host Controller
[    1.240173] usb usb5: Manufacturer: Linux 3.8.0-13-generic ohci_hcd
[    1.240189] usb usb5: SerialNumber: 0000:02:02.2
[    1.240481] hub 5-0:1.0: USB hub found
[    1.240507] hub 5-0:1.0: 1 port detected
[    1.240707] pci 0000:01:00.0: using bridge 0000:00:17.0 INT A to get IRQ 16
[    1.240727] ohci_hcd 0000:02:08.0: PCI->APIC IRQ transform: INT A -> IRQ 16
[    1.240772] ohci_hcd 0000:02:08.0: setting latency timer to 64
[    1.240782] ohci_hcd 0000:02:08.0: OHCI Host Controller
[    1.240808] ohci_hcd 0000:02:08.0: new USB bus registered, assigned bus number 6
[    1.240858] ohci_hcd 0000:02:08.0: irq 16, io mem 0xa0004800
[    1.300125] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    1.300146] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.300167] usb usb6: Product: OHCI Host Controller
[    1.300182] usb usb6: Manufacturer: Linux 3.8.0-13-generic ohci_hcd
[    1.300199] usb usb6: SerialNumber: 0000:02:08.0
[    1.300505] hub 6-0:1.0: USB hub found
[    1.300532] hub 6-0:1.0: 1 port detected
[    1.300731] pci 0000:01:00.0: using bridge 0000:00:17.0 INT A to get IRQ 16
[    1.300750] ohci_hcd 0000:02:08.1: PCI->APIC IRQ transform: INT A -> IRQ 16
[    1.300797] ohci_hcd 0000:02:08.1: setting latency timer to 64
[    1.300807] ohci_hcd 0000:02:08.1: OHCI Host Controller
[    1.300832] ohci_hcd 0000:02:08.1: new USB bus registered, assigned bus number 7
[    1.300884] ohci_hcd 0000:02:08.1: irq 16, io mem 0xa0004900
[    1.360106] usb 1-3: new high-speed USB device number 2 using ehci-pci
[    1.360188] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    1.360208] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.360229] usb usb7: Product: OHCI Host Controller
[    1.360244] usb usb7: Manufacturer: Linux 3.8.0-13-generic ohci_hcd
[    1.360260] usb usb7: SerialNumber: 0000:02:08.1
[    1.360541] hub 7-0:1.0: USB hub found
[    1.360568] hub 7-0:1.0: 1 port detected
[    1.360853] pci 0000:01:00.0: using bridge 0000:00:17.0 INT A to get IRQ 16
[    1.360873] ohci_hcd 0000:02:08.2: PCI->APIC IRQ transform: INT A -> IRQ 16
[    1.360920] ohci_hcd 0000:02:08.2: setting latency timer to 64
[    1.360930] ohci_hcd 0000:02:08.2: OHCI Host Controller
[    1.360955] ohci_hcd 0000:02:08.2: new USB bus registered, assigned bus number 8
[    1.361005] ohci_hcd 0000:02:08.2: irq 16, io mem 0xa0004a00
[    1.379583] isapnp: No Plug & Play device found
[    1.420110] usb usb8: New USB device found, idVendor=1d6b, idProduct=0001
[    1.420127] usb usb8: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.420143] usb usb8: Product: OHCI Host Controller
[    1.420155] usb usb8: Manufacturer: Linux 3.8.0-13-generic ohci_hcd
[    1.420167] usb usb8: SerialNumber: 0000:02:08.2
[    1.420267] hub 8-0:1.0: USB hub found
[    1.420291] hub 8-0:1.0: 1 port detected
[    1.420473] uhci_hcd: USB Universal Host Controller Interface driver
[    1.420661] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.492131] usb 1-3: config 1 has an invalid interface number: 7 but max is 5
[    1.492140] usb 1-3: config 1 has no interface number 5
[    1.492181] usb 1-3: New USB device found, idVendor=1199, idProduct=683c
[    1.492181] usb 1-3: New USB device strings: Mfr=3, Product=2, SerialNumber=4
[    1.492181] usb 1-3: Product: MC7710
[    1.492181] usb 1-3: Manufacturer: Sierra Wireless, Incorporated
[    1.492183] usb 1-3: SerialNumber: 001027009999999
[    1.608117] usb 2-3: new high-speed USB device number 2 using ehci-pci
[    1.740152] usb 2-3: New USB device found, idVendor=0bda, idProduct=8176
[    1.740155] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.740172] usb 2-3: Product: 802.11n WLAN Adapter
[    1.740187] usb 2-3: Manufacturer: Realtek
[    1.740202] usb 2-3: SerialNumber: 00e04c000001
[    2.453008] i8042: No controller found
[    2.453172] mousedev: PS/2 mouse device common for all mice
[    2.456231] rtc_cmos rtc_cmos: rtc core: registered rtc_cmos as rtc0
[    2.456284] rtc0: alarms up to one day, 114 bytes nvram
[    2.456547] device-mapper: uevent: version 1.0.3
[    2.456659] device-mapper: ioctl: 4.23.1-ioctl (2012-12-18) initialised: dm-devel@redhat.com
[    2.456659] EISA: Probing bus 0 at eisa.0
[    2.456659] Cannot allocate resource for EISA slot 1
[    2.456659] Cannot allocate resource for EISA slot 2
[    2.456659] Cannot allocate resource for EISA slot 3
[    2.456659] Cannot allocate resource for EISA slot 4
[    2.456659] Cannot allocate resource for EISA slot 5
[    2.456659] Cannot allocate resource for EISA slot 6
[    2.456659] EISA: Detected 0 cards.
[    2.456659] cpufreq-nforce2: No nForce2 chipset.
[    2.456659] cpuidle: using governor ladder
[    2.456682] cpuidle: using governor menu
[    2.456696] ledtrig-cpu: registered to indicate activity on CPUs
[    2.456708] EFI Variables Facility v0.08 2004-May-17
[    2.456970] ashmem: initialized
[    2.456970] TCP: cubic registered
[    2.456970] NET: Registered protocol family 10
[    2.457301] NET: Registered protocol family 17
[    2.457346] Key type dns_resolver registered
[    2.457581] Using IPI No-Shortcut mode
[    2.457581] Loading module verification certificates
[    2.473622] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 8043a659876608115279d6fb52b550930f115846'
[    2.473675] registered taskstats version 1
[    2.480425] Key type trusted registered
[    2.486728] Key type encrypted registered
[    2.493578] rtc_cmos rtc_cmos: setting system clock to 2013-03-30 09:43:04 UTC (1364636584)
[    2.493578] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.493578] EDD information not available.
[    2.493578] Freeing unused kernel memory: 784k freed
[    2.496351] Write protecting the kernel text: 6252k
[    2.496541] Write protecting the kernel read-only data: 2432k
[    2.496555] NX-protecting the kernel data: 3988k
[    2.534756] udevd[95]: starting version 175
[    2.734378] Disabling lock debugging due to kernel taint
[    2.737738] ahci 0000:02:06.0: version 3.0
[    2.737775] pci 0000:01:00.0: using bridge 0000:00:17.0 INT B to get IRQ 17
[    2.737800] ahci 0000:02:06.0: PCI->APIC IRQ transform: INT B -> IRQ 17
[    2.737943] ahci 0000:02:06.0: irq 40 for MSI/MSI-X
[    2.738020] ahci: SSS flag set, parallel bus scan disabled
[    2.738103] ahci 0000:02:06.0: AHCI 0001.0100 32 slots 2 ports 3 Gbps 0x3 impl SATA mode
[    2.738131] ahci 0000:02:06.0: flags: ncq sntf stag pm led clo only pmp pio slum part ccc 
[    2.738161] ahci 0000:02:06.0: setting latency timer to 64
[    2.760208] scsi0 : ahci
[    2.778405] sdhci: Secure Digital Host Controller Interface driver
[    2.778429] sdhci: Copyright(c) Pierre Ossman
[    2.781631] scsi1 : ahci
[    2.781891] ata1: SATA max UDMA/133 abar m1024@0xa0004400 port 0xa0004500 irq 40
[    2.781921] ata2: SATA max UDMA/133 abar m1024@0xa0004400 port 0xa0004580 irq 40
[    2.791782] pps_core: LinuxPPS API ver. 1 registered
[    2.791807] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    2.840380] e1000e: Intel(R) PRO/1000 Network Driver - 2.1.4-k
[    2.840404] e1000e: Copyright(c) 1999 - 2012 Intel Corporation.
[    2.840496] e1000e 0000:05:00.0: Disabling ASPM L0s L1
[    2.840543] pcieport 0000:03:00.0: using bridge 0000:00:18.0 INT C to get IRQ 19
[    2.840567] e1000e 0000:05:00.0: PCI->APIC IRQ transform: INT C -> IRQ 19
[    2.840791] e1000e 0000:05:00.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    2.840969] e1000e 0000:05:00.0: irq 41 for MSI/MSI-X
[    2.840996] e1000e 0000:05:00.0: irq 42 for MSI/MSI-X
[    2.841021] e1000e 0000:05:00.0: irq 43 for MSI/MSI-X
[    2.842899] PTP clock support registered
[    2.861581] sdhci-pci 0000:02:04.0: SDHCI controller found [8086:8809] (rev 1)
[    2.861642] pci 0000:01:00.0: using bridge 0000:00:17.0 INT C to get IRQ 18
[    2.861664] sdhci-pci 0000:02:04.0: PCI->APIC IRQ transform: INT C -> IRQ 18
[    2.861759] sdhci-pci 0000:02:04.0: setting latency timer to 64
[    2.861775] mmc0: no vqmmc regulator found
[    2.861791] mmc0: no vmmc regulator found
[    2.861845] sdhci-pci 0000:02:04.0: setting latency timer to 64
[    2.892236] mmc0: SDHCI controller on PCI [0000:02:04.0] using DMA
[    2.892389] sdhci-pci 0000:02:04.1: SDHCI controller found [8086:880a] (rev 1)
[    2.892441] pci 0000:01:00.0: using bridge 0000:00:17.0 INT C to get IRQ 18
[    2.892460] sdhci-pci 0000:02:04.1: PCI->APIC IRQ transform: INT C -> IRQ 18
[    2.892540] sdhci-pci 0000:02:04.1: setting latency timer to 64
[    2.892552] mmc1: no vqmmc regulator found
[    2.892566] mmc1: no vmmc regulator found
[    2.892602] sdhci-pci 0000:02:04.1: setting latency timer to 64
[    2.895656] sdhci-pci 0000:02:04.0: setting latency timer to 64
[    2.924280] mmc1: SDHCI controller on PCI [0000:02:04.1] using DMA
[    2.925032] pci 0000:01:00.0: using bridge 0000:00:17.0 INT C to get IRQ 18
[    2.925060] ptp_pch 0000:02:0c.4: PCI->APIC IRQ transform: INT C -> IRQ 18
[    2.931557] sdhci-pci 0000:02:04.0: setting latency timer to 64
[    2.949570] pch_gbe: EG20T PCH Gigabit Ethernet Driver - version 1.01
[    2.949662] pci 0000:01:00.0: using bridge 0000:00:17.0 INT A to get IRQ 16
[    2.949686] pch_gbe 0000:02:00.1: PCI->APIC IRQ transform: INT A -> IRQ 16
[    2.949724] pch_gbe 0000:02:00.1: setting latency timer to 64
[    2.951877] pch_gbe: Error: busy bit is not cleared
[    2.953981] pch_gbe: Error: busy bit is not cleared
[    2.956053] pch_gbe: Error: busy bit is not cleared
[    2.962415] pch_gbe: pch-gbe.miim won't go Ready
[    2.964170] pch_gbe: pch-gbe.miim won't go Ready
[    2.966384] pch_gbe: pch-gbe.miim won't go Ready
[    2.967515] sdhci-pci 0000:02:04.0: setting latency timer to 64
[    2.968170] pch_gbe: pch-gbe.miim won't go Ready
[    2.970397] pch_gbe: pch-gbe.miim won't go Ready
[    2.972170] pch_gbe: pch-gbe.miim won't go Ready
[    2.974397] pch_gbe: pch-gbe.miim won't go Ready
[    2.976170] pch_gbe: pch-gbe.miim won't go Ready
[    2.978398] pch_gbe: pch-gbe.miim won't go Ready
[    2.982394] pch_gbe: pch-gbe.miim won't go Ready
[    2.984171] pch_gbe: pch-gbe.miim won't go Ready
[    2.986390] pch_gbe: pch-gbe.miim won't go Ready
[    2.988171] pch_gbe: pch-gbe.miim won't go Ready
[    2.990398] pch_gbe: pch-gbe.miim won't go Ready
[    2.992171] pch_gbe: pch-gbe.miim won't go Ready
[    2.994402] pch_gbe: pch-gbe.miim won't go Ready
[    2.996172] pch_gbe: pch-gbe.miim won't go Ready
[    2.998395] pch_gbe: pch-gbe.miim won't go Ready
[    3.002377] pch_gbe: pch-gbe.miim won't go Ready
[    3.003497] sdhci-pci 0000:02:04.0: setting latency timer to 64
[    3.004172] pch_gbe: pch-gbe.miim won't go Ready
[    3.006374] pch_gbe: pch-gbe.miim won't go Ready
[    3.008172] pch_gbe: pch-gbe.miim won't go Ready
[    3.009755] sdhci-pci 0000:02:04.1: setting latency timer to 64
[    3.010396] pch_gbe: pch-gbe.miim won't go Ready
[    3.012333] e1000e 0000:05:00.0 eth0: (PCI Express:2.5GT/s:Width x1) 00:00:24:cf:28:3c
[    3.012360] e1000e 0000:05:00.0 eth0: Intel(R) PRO/1000 Network Connection
[    3.012460] e1000e 0000:05:00.0 eth0: MAC: 3, PHY: 8, PBA No: FFFFFF-0FF
[    3.012532] e1000e 0000:06:00.0: Disabling ASPM L0s L1
[    3.012579] pcieport 0000:03:00.0: using bridge 0000:00:18.0 INT D to get IRQ 16
[    3.012600] e1000e 0000:06:00.0: PCI->APIC IRQ transform: INT D -> IRQ 16
[    3.012824] e1000e 0000:06:00.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    3.013005] e1000e 0000:06:00.0: irq 44 for MSI/MSI-X
[    3.013030] e1000e 0000:06:00.0: irq 45 for MSI/MSI-X
[    3.013053] e1000e 0000:06:00.0: irq 46 for MSI/MSI-X
[    3.012173] pch_gbe: pch-gbe.miim won't go Ready
[    3.014382] pch_gbe: pch-gbe.miim won't go Ready
[    3.018370] pch_gbe: pch-gbe.miim won't go Ready
[    3.020173] pch_gbe: pch-gbe.miim won't go Ready
[    3.022369] pch_gbe: pch-gbe.miim won't go Ready
[    3.024173] pch_gbe: pch-gbe.miim won't go Ready
[    3.026371] pch_gbe: pch-gbe.miim won't go Ready
[    3.028174] pch_gbe: pch-gbe.miim won't go Ready
[    3.030370] pch_gbe: pch-gbe.miim won't go Ready
[    3.032174] pch_gbe: pch-gbe.miim won't go Ready
[    3.034372] pch_gbe: pch-gbe.miim won't go Ready
[    3.038371] pch_gbe: pch-gbe.miim won't go Ready
[    3.040174] pch_gbe: pch-gbe.miim won't go Ready
[    3.042377] pch_gbe: pch-gbe.miim won't go Ready
[    3.043493] sdhci-pci 0000:02:04.1: setting latency timer to 64
[    3.044175] pch_gbe: pch-gbe.miim won't go Ready
[    3.046371] pch_gbe: pch-gbe.miim won't go Ready
[    3.048175] pch_gbe: pch-gbe.miim won't go Ready
[    3.050371] pch_gbe: pch-gbe.miim won't go Ready
[    3.052175] pch_gbe: pch-gbe.miim won't go Ready
[    3.054372] pch_gbe: pch-gbe.miim won't go Ready
[    3.056175] pch_gbe: pch-gbe.miim won't go Ready
[    3.058377] pch_gbe: pch-gbe.miim won't go Ready
[    3.062373] pch_gbe: pch-gbe.miim won't go Ready
[    3.064176] pch_gbe: pch-gbe.miim won't go Ready
[    3.066373] pch_gbe: pch-gbe.miim won't go Ready
[    3.068176] pch_gbe: pch-gbe.miim won't go Ready
[    3.070458] pch_gbe: pch-gbe.miim won't go Ready
[    3.072176] pch_gbe: pch-gbe.miim won't go Ready
[    3.074375] pch_gbe: pch-gbe.miim won't go Ready
[    3.078379] pch_gbe: pch-gbe.miim won't go Ready
[    3.079487] sdhci-pci 0000:02:04.1: setting latency timer to 64
[    3.080177] pch_gbe: pch-gbe.miim won't go Ready
[    3.082374] pch_gbe: pch-gbe.miim won't go Ready
[    3.084177] pch_gbe: pch-gbe.miim won't go Ready
[    3.086373] pch_gbe: pch-gbe.miim won't go Ready
[    3.088177] pch_gbe: pch-gbe.miim won't go Ready
[    3.090374] pch_gbe: pch-gbe.miim won't go Ready
[    3.092178] pch_gbe: pch-gbe.miim won't go Ready
[    3.094374] pch_gbe: pch-gbe.miim won't go Ready
[    3.096178] pch_gbe: pch-gbe.miim won't go Ready
[    3.100235] ata1: SATA link down (SStatus 0 SControl 300)
[    3.098377] pch_gbe: pch-gbe.miim won't go Ready
[    3.102375] pch_gbe: pch-gbe.miim won't go Ready
[    3.104178] pch_gbe: pch-gbe.miim won't go Ready
[    3.106375] pch_gbe: pch-gbe.miim won't go Ready
[    3.108179] pch_gbe: pch-gbe.miim won't go Ready
[    3.110375] pch_gbe: pch-gbe.miim won't go Ready
[    3.112179] pch_gbe: pch-gbe.miim won't go Ready
[    3.115473] sdhci-pci 0000:02:04.1: setting latency timer to 64
[    3.114385] pch_gbe: pch-gbe.miim won't go Ready
[    3.116179] pch_gbe: pch-gbe.miim won't go Ready
[    3.118376] pch_gbe: pch-gbe.miim won't go Ready
[    3.122375] pch_gbe: pch-gbe.miim won't go Ready
[    3.124180] pch_gbe: pch-gbe.miim won't go Ready
[    3.126425] pch_gbe: pch-gbe.miim won't go Ready
[    3.128722] e1000e 0000:06:00.0 eth1: (PCI Express:2.5GT/s:Width x1) 00:00:24:cf:28:3d
[    3.128750] e1000e 0000:06:00.0 eth1: Intel(R) PRO/1000 Network Connection
[    3.128852] e1000e 0000:06:00.0 eth1: MAC: 3, PHY: 8, PBA No: FFFFFF-0FF
[    3.128915] e1000e 0000:0a:00.0: Disabling ASPM L0s L1
[    3.128960] pcieport 0000:08:00.0: using bridge 0000:00:19.0 INT C to get IRQ 16
[    3.128981] e1000e 0000:0a:00.0: PCI->APIC IRQ transform: INT C -> IRQ 16
[    3.129204] e1000e 0000:0a:00.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    3.129385] e1000e 0000:0a:00.0: irq 47 for MSI/MSI-X
[    3.129410] e1000e 0000:0a:00.0: irq 48 for MSI/MSI-X
[    3.129434] e1000e 0000:0a:00.0: irq 49 for MSI/MSI-X
[    3.128180] pch_gbe: pch-gbe.miim won't go Ready
[    3.130387] pch_gbe: pch-gbe.miim won't go Ready
[    3.132180] pch_gbe: pch-gbe.miim won't go Ready
[    3.134378] pch_gbe: pch-gbe.miim won't go Ready
[    3.138377] pch_gbe: pch-gbe.miim won't go Ready
[    3.140181] pch_gbe: pch-gbe.miim won't go Ready
[    3.142377] pch_gbe: pch-gbe.miim won't go Ready
[    3.144181] pch_gbe: pch-gbe.miim won't go Ready
[    3.146377] pch_gbe: pch-gbe.miim won't go Ready
[    3.148181] pch_gbe: pch-gbe.miim won't go Ready
[    3.150378] pch_gbe: pch-gbe.miim won't go Ready
[    3.152181] pch_gbe: pch-gbe.miim won't go Ready
[    3.154378] pch_gbe: pch-gbe.miim won't go Ready
[    3.158378] pch_gbe: pch-gbe.miim won't go Ready
[    3.160182] pch_gbe: pch-gbe.miim won't go Ready
[    3.162378] pch_gbe: pch-gbe.miim won't go Ready
[    3.164182] pch_gbe: pch-gbe.miim won't go Ready
[    3.166378] pch_gbe: pch-gbe.miim won't go Ready
[    3.168182] pch_gbe: pch-gbe.miim won't go Ready
[    3.170378] pch_gbe: pch-gbe.miim won't go Ready
[    3.172183] pch_gbe: pch-gbe.miim won't go Ready
[    3.172193] pch_gbe 0000:02:00.1: PHY initialize error
[    3.174398] pch_gbe: pch-gbe.miim won't go Ready
[    3.176183] pch_gbe: pch-gbe.miim won't go Ready
[    3.178379] pch_gbe: pch-gbe.miim won't go Ready
[    3.182379] pch_gbe: pch-gbe.miim won't go Ready
[    3.184183] pch_gbe: pch-gbe.miim won't go Ready
[    3.184238] pch_gbe: probe of 0000:02:00.1 failed with error -11
[    3.244314] e1000e 0000:0a:00.0 eth2: (PCI Express:2.5GT/s:Width x1) 00:00:24:cf:28:3e
[    3.244344] e1000e 0000:0a:00.0 eth2: Intel(R) PRO/1000 Network Connection
[    3.244442] e1000e 0000:0a:00.0 eth2: MAC: 3, PHY: 8, PBA No: FFFFFF-0FF
[    3.244499] e1000e 0000:0b:00.0: Disabling ASPM L0s L1
[    3.244544] pcieport 0000:08:00.0: using bridge 0000:00:19.0 INT D to get IRQ 17
[    3.244564] e1000e 0000:0b:00.0: PCI->APIC IRQ transform: INT D -> IRQ 17
[    3.244779] e1000e 0000:0b:00.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    3.244952] e1000e 0000:0b:00.0: irq 50 for MSI/MSI-X
[    3.244977] e1000e 0000:0b:00.0: irq 51 for MSI/MSI-X
[    3.245001] e1000e 0000:0b:00.0: irq 52 for MSI/MSI-X
[    3.360296] e1000e 0000:0b:00.0 eth3: (PCI Express:2.5GT/s:Width x1) 00:00:24:cf:28:3f
[    3.360324] e1000e 0000:0b:00.0 eth3: Intel(R) PRO/1000 Network Connection
[    3.360422] e1000e 0000:0b:00.0 eth3: MAC: 3, PHY: 8, PBA No: FFFFFF-0FF
[    3.592257] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    3.592251] ata2.00: ATA-9: Samsung SSD 840 Series, DXT06B0Q, max UDMA/133
[    3.592254] ata2.00: 488397168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    3.592279] ata2.00: configured for UDMA/133
[    3.592438] scsi 1:0:0:0: Direct-Access     ATA      Samsung SSD 840  DXT0 PQ: 0 ANSI: 5
[    3.592868] sd 1:0:0:0: [sda] 488397168 512-byte logical blocks: (250 GB/232 GiB)
[    3.592884] sd 1:0:0:0: Attached scsi generic sg0 type 0
[    3.593126] sd 1:0:0:0: [sda] Write Protect is off
[    3.593126] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    3.593126] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    3.596576]  sda: sda1 sda2 < sda5 >
[    3.597001] sd 1:0:0:0: [sda] Attached SCSI disk
[    3.681850] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    3.681875] EXT4-fs (sda1): write access will be enabled during recovery
[    4.147673] EXT4-fs (sda1): orphan cleanup on readonly fs
[    4.148340] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 11405403
[    4.149451] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 11403764
[    4.149451] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1310731
[    4.149451] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1310730
[    4.149451] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1310729
[    4.149451] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1310728
[    4.149451] EXT4-fs (sda1): ext4_orphan_cleanup: deleting unreferenced inode 1310727
[    4.149451] EXT4-fs (sda1): 7 orphan inodes deleted
[    4.149451] EXT4-fs (sda1): recovery complete
[    4.176310] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    4.650235] Adding 2095100k swap on /dev/sda5.  Priority:-1 extents:1 across:2095100k SS
[    4.671176] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[    5.941737] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    5.941759] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[    5.941776] IPv6: ADDRCONF(NETDEV_UP): eth2: link is not ready
[    5.941791] IPv6: ADDRCONF(NETDEV_UP): eth3: link is not ready
[    6.182692] udevd[470]: starting version 175
[    6.330139] lp: driver loaded but no devices found
[    6.396140] coretemp coretemp.0: Unable to read TjMax from CPU 0
[    6.464894] bonding: Ethernet Channel Bonding Driver: v3.7.1 (April 27, 2011)
[    6.624999] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    6.630472] init: avahi-cups-reload main process (510) terminated with status 1
[    6.771464] ACPI Exception: AE_BAD_PARAMETER, Thread 4140325296 could not acquire Mutex [0x1] (20121018/utmutex-278)
[    6.771725] ACPI Exception: AE_BAD_PARAMETER, Thread 4140325296 could not acquire Mutex [0x1] (20121018/utmutex-278)
[    6.771890] ACPI Exception: AE_BAD_PARAMETER, Thread 4140325296 could not acquire Mutex [0x1] (20121018/utmutex-278)
[    6.797711] pci 0000:01:00.0: using bridge 0000:00:17.0 INT A to get IRQ 16
[    6.797728] pch_gpio 0000:02:00.2: PCI->APIC IRQ transform: INT A -> IRQ 16
[    6.903603] CAN device driver interface
[    6.975964] pci 0000:01:00.0: using bridge 0000:00:17.0 INT C to get IRQ 18
[    6.975977] pch_can 0000:02:0c.3: PCI->APIC IRQ transform: INT C -> IRQ 18
[    6.976145] pch_can 0000:02:0c.3: irq 53 for MSI/MSI-X
[    6.976185] pch_can 0000:02:0c.3 (unregistered net_device): PCH CAN opened with MSI
[    6.976222] pch_can 0000:02:0c.3: setting latency timer to 64
[    7.224032] usbcore: registered new interface driver usbserial
[    7.230044] usbcore: registered new interface driver usbserial_generic
[    7.230255] usbserial: USB Serial support registered for generic
[    7.302590] usbcore: registered new interface driver sierra
[    7.302647] usbserial: USB Serial support registered for Sierra USB modem
[    7.302719] sierra 1-3:1.0: Sierra USB modem converter detected
[    7.371438] usb 1-3: Sierra USB modem converter now attached to ttyUSB0
[    7.373413] sierra 1-3:1.1: Sierra USB modem converter detected
[    7.386974] usb 1-3: Sierra USB modem converter now attached to ttyUSB1
[    7.391300] sierra 1-3:1.2: Sierra USB modem converter detected
[    7.394761] usb 1-3: Sierra USB modem converter now attached to ttyUSB2
[    7.395243] sierra 1-3:1.3: Sierra USB modem converter detected
[    7.399610] usb 1-3: Sierra USB modem converter now attached to ttyUSB3
[    7.402179] sierra 1-3:1.4: Sierra USB modem converter detected
[    7.406514] usb 1-3: Sierra USB modem converter now attached to ttyUSB4
[    7.411197] sierra 1-3:1.7: Sierra USB modem converter detected
[    7.418507] usb 1-3: Sierra USB modem converter now attached to ttyUSB5
[    7.588578] microcode: CPU0 sig=0x20661, pf=0x2, revision=0x104
[    7.609997] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[    7.710462] cfg80211: Calling CRDA to update world regulatory domain
[    8.559450] rtl8192cu: Chip version 0x10
[    8.889389] microcode: CPU1 sig=0x20661, pf=0x2, revision=0x104
[    9.030808] rtl8192cu: MAC address: 90:f6:52:15:2a:10
[    9.030822] rtl8192cu: Board Type 0
[    9.031051] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[    9.031149] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw.bin
[    9.032362] usbcore: registered new interface driver rtl8192cu
[    9.089582] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[    9.090929] rtlwifi: wireless switch is on
[    9.142405] cfg80211: World regulatory domain updated:
[    9.142418] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    9.142427] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.142434] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    9.142442] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[    9.142450] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.142457] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.142506] cfg80211: Calling CRDA for country: US
[    9.173226] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    9.189127] bonding: bond0: Setting MII monitoring interval to 100.
[    9.226834] bonding: bond0: setting mode to 802.3ad (4).
[    9.257269] bonding: bond0: Setting LACP rate to fast (1).
[    9.266357] IPv6: ADDRCONF(NETDEV_UP): bond0: link is not ready
[    9.296685] cfg80211: Regulatory domain changed to country: US
[    9.296695] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[    9.296704] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[    9.296711] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[    9.296719] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.296726] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.296733] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[    9.296740] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[    9.375668] bonding: bond0: Adding slave eth3.
[    9.453957] bonding: bond0: enslaving eth3 as a backup interface with a down link.
[    9.456927] bonding: bond0: Adding slave eth2.
[    9.514383] e1000e: eth1 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[    9.514400] e1000e 0000:06:00.0 eth1: 10/100 speed: disabling TSO
[    9.537934] bonding: bond0: enslaving eth2 as a backup interface with a down link.
[    9.538033] IPv6: ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[    9.760414] Bridge firewalling registered
[   10.365847] init: udev-fallback-graphics main process (1380) terminated with status 1
[   10.666335] device eth0 entered promiscuous mode
[   10.753234] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   10.773062] IPv6: ADDRCONF(NETDEV_UP): br0: link is not ready
[   10.904029] bonding: bond0: Setting MII monitoring interval to 100.
[   10.927382] bonding: unable to update mode of bond0 because interface is up.
[   10.937021] bonding: bond0: Unable to update LACP rate because interface is up.
[   12.329888] e1000e: eth0 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[   12.329905] e1000e 0000:05:00.0 eth0: 10/100 speed: disabling TSO
[   12.330156] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   12.330212] br0: port 1(eth0) entered forwarding state
[   12.330243] br0: port 1(eth0) entered forwarding state
[   12.330389] IPv6: ADDRCONF(NETDEV_CHANGE): br0: link becomes ready
[   12.673880] e1000e: eth2 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[   12.764801] bonding: bond0: link status definitely up for interface eth2, 1000 Mbps full duplex.
[   12.764876] IPv6: ADDRCONF(NETDEV_CHANGE): bond0: link becomes ready
[   12.849887] e1000e: eth3 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[   12.864819] bonding: bond0: link status definitely up for interface eth3, 1000 Mbps full duplex.
[   27.361708] br0: port 1(eth0) entered forwarding state
[  131.031817] rtl8192cu: MAC auto ON okay!
[  131.074598] rtl8192cu: Tx queue select: 0x05
[  131.496586] device wlan0 entered promiscuous mode
[  131.499017] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  131.504079] cfg80211: Calling CRDA for country: EU
[  131.521862] cfg80211: Regulatory domain changed to country: EU
[  131.521873] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  131.521882] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  131.521889] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  131.521896] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[  131.521903] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[  131.530218] 8021q: 802.1Q VLAN Support v1.8
[  131.530260] 8021q: adding VLAN 0 to HW filter on device eth0
[  131.531807] 8021q: adding VLAN 0 to HW filter on device eth1
[  131.531807] 8021q: adding VLAN 0 to HW filter on device eth2
[  131.531807] 8021q: adding VLAN 0 to HW filter on device eth3
[  131.531807] 8021q: adding VLAN 0 to HW filter on device bond0
[  131.535028] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  131.535104] br0: port 2(wlan0) entered forwarding state
[  131.535147] br0: port 2(wlan0) entered forwarding state
[  146.537170] br0: port 2(wlan0) entered forwarding state
[  155.723177] perl[2991]: segfault at 74a9b473 ip b69c7a81 sp bfc4fc14 error 4 in Scan.so[b66ab000+4e7000]
[ 3135.331999] usb 1-1: new high-speed USB device number 3 using ehci-pci
[ 3135.467217] usb 1-1: New USB device found, idVendor=12d1, idProduct=1505
[ 3135.467217] usb 1-1: New USB device strings: Mfr=3, Product=2, SerialNumber=0
[ 3135.467217] usb 1-1: Product: HUAWEI Mobile
[ 3135.467217] usb 1-1: Manufacturer: Huawei Technologies
[ 3135.489317] Initializing USB Mass Storage driver...
[ 3135.504135] scsi2 : usb-storage 1-1:1.0
[ 3135.509480] scsi3 : usb-storage 1-1:1.1
[ 3135.509754] usbcore: registered new interface driver usb-storage
[ 3135.509761] USB Mass Storage support registered.
[ 3136.509606] scsi 3:0:0:0: Direct-Access     HUAWEI   TF CARD Storage  2.31 PQ: 0 ANSI: 2
[ 3137.635762] usb 1-1: USB disconnect, device number 3
[ 3137.663615] sd 3:0:0:0: Attached scsi generic sg1 type 0
[ 3137.676338] sd 3:0:0:0: [sdb] READ CAPACITY failed
[ 3137.676350] sd 3:0:0:0: [sdb]  
[ 3137.676358] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 3137.676366] sd 3:0:0:0: [sdb] Sense not available.
[ 3137.676417] sd 3:0:0:0: [sdb] Write Protect is off
[ 3137.676428] sd 3:0:0:0: [sdb] Mode Sense: 00 00 00 00
[ 3137.676477] sd 3:0:0:0: [sdb] Asking for cache data failed
[ 3137.676496] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[ 3137.677061] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[ 3143.088469] usb 1-1: new high-speed USB device number 4 using ehci-pci
[ 3143.224388] usb 1-1: New USB device found, idVendor=12d1, idProduct=1506
[ 3143.224388] usb 1-1: New USB device strings: Mfr=4, Product=3, SerialNumber=0
[ 3143.224449] usb 1-1: Product: HUAWEI Mobile
[ 3143.224459] usb 1-1: Manufacturer: Huawei Technologies
[ 3143.229353] scsi4 : usb-storage 1-1:1.5
[ 3143.232966] scsi5 : usb-storage 1-1:1.6
[ 3143.397853] usbcore: registered new interface driver cdc_wdm
[ 3143.434963] usbcore: registered new interface driver option
[ 3143.435053] usbserial: USB Serial support registered for GSM modem (1-port)
[ 3143.435625] option 1-1:1.0: GSM modem (1-port) converter detected
[ 3143.437842] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB6
[ 3143.439000] option 1-1:1.3: GSM modem (1-port) converter detected
[ 3143.441612] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB7
[ 3143.441721] option 1-1:1.4: GSM modem (1-port) converter detected
[ 3143.454667] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB8
[ 3143.481967] qmi_wwan 1-1:1.1: cdc-wdm0: USB WDM device
[ 3143.482512] qmi_wwan 1-1:1.1 wwan0: register 'qmi_wwan' at usb-0000:02:02.3-1, WWAN/QMI device, 02:50:f3:00:00:00
[ 3143.485784] usbcore: registered new interface driver qmi_wwan
[ 3144.229066] scsi 4:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[ 3144.238717] scsi 5:0:0:0: Direct-Access     HUAWEI   TF CARD Storage  2.31 PQ: 0 ANSI: 2
[ 3144.242710] sr0: scsi-1 drive
[ 3144.242721] cdrom: Uniform CD-ROM driver Revision: 3.20
[ 3144.243120] sr 4:0:0:0: Attached scsi CD-ROM sr0
[ 3144.243441] sr 4:0:0:0: Attached scsi generic sg1 type 5
[ 3144.244143] sd 5:0:0:0: Attached scsi generic sg2 type 0
[ 3144.249317] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[ 3193.941935] dhclient[12327]: segfault at 200 ip b7453b29 sp bfee7350 error 4 in libc-2.17.so[b740b000+1ad000]
[ 3194.778006] PPP BSD Compression module registered
[ 3194.784537] PPP Deflate Compression module registered
[ 3310.167948] ip_tables: (C) 2000-2006 Netfilter Core Team
[ 3396.617960] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[ 3713.476159] usb 1-1: USB disconnect, device number 4
[ 3713.476366] option1 ttyUSB6: option_instat_callback: error -108
[ 3713.485494] option1 ttyUSB6: GSM modem (1-port) converter now disconnected from ttyUSB6
[ 3713.485544] option 1-1:1.0: device disconnected
[ 3713.485694] qmi_wwan 1-1:1.1 wwan0: unregister 'qmi_wwan' usb-0000:02:02.3-1, WWAN/QMI device
[ 3713.547732] option1 ttyUSB7: GSM modem (1-port) converter now disconnected from ttyUSB7
[ 3713.547795] option 1-1:1.3: device disconnected
[ 3713.548362] option1 ttyUSB8: GSM modem (1-port) converter now disconnected from ttyUSB8
[ 3713.548420] option 1-1:1.4: device disconnected
[ 3905.788131] usb 1-1: new high-speed USB device number 5 using ehci-pci
[ 3905.920153] usb 1-1: New USB device found, idVendor=12d1, idProduct=1505
[ 3905.920153] usb 1-1: New USB device strings: Mfr=3, Product=2, SerialNumber=0
[ 3905.920157] usb 1-1: Product: HUAWEI Mobile
[ 3905.920164] usb 1-1: Manufacturer: Huawei Technologies
[ 3905.925283] scsi6 : usb-storage 1-1:1.0
[ 3905.925530] scsi7 : usb-storage 1-1:1.1
[ 3906.924363] scsi 7:0:0:0: Direct-Access     HUAWEI   TF CARD Storage  2.31 PQ: 0 ANSI: 2
[ 3908.008323] usb 1-1: USB disconnect, device number 5
[ 3908.038873] sd 7:0:0:0: Attached scsi generic sg1 type 0
[ 3908.052543] sd 7:0:0:0: [sdb] READ CAPACITY failed
[ 3908.052557] sd 7:0:0:0: [sdb]  
[ 3908.052565] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
[ 3908.052573] sd 7:0:0:0: [sdb] Sense not available.
[ 3908.052634] sd 7:0:0:0: [sdb] Write Protect is off
[ 3908.052647] sd 7:0:0:0: [sdb] Mode Sense: 44 45 56 54
[ 3908.052707] sd 7:0:0:0: [sdb] No Caching mode page present
[ 3908.052726] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 3908.053950] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[ 3913.508607] usb 1-1: new high-speed USB device number 6 using ehci-pci
[ 3913.640633] usb 1-1: New USB device found, idVendor=12d1, idProduct=1506
[ 3913.640633] usb 1-1: New USB device strings: Mfr=4, Product=3, SerialNumber=0
[ 3913.640640] usb 1-1: Product: HUAWEI Mobile
[ 3913.640647] usb 1-1: Manufacturer: Huawei Technologies
[ 3913.645369] option 1-1:1.0: GSM modem (1-port) converter detected
[ 3913.645369] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB6
[ 3913.645369] qmi_wwan 1-1:1.1: cdc-wdm0: USB WDM device
[ 3913.645369] qmi_wwan 1-1:1.1 wwan0: register 'qmi_wwan' at usb-0000:02:02.3-1, WWAN/QMI device, 02:50:f3:00:00:00
[ 3913.648705] option 1-1:1.3: GSM modem (1-port) converter detected
[ 3913.649772] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB7
[ 3913.650026] option 1-1:1.4: GSM modem (1-port) converter detected
[ 3913.650265] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB8
[ 3913.651543] scsi8 : usb-storage 1-1:1.5
[ 3913.651543] scsi9 : usb-storage 1-1:1.6
[ 3914.648853] scsi 9:0:0:0: Direct-Access     HUAWEI   TF CARD Storage  2.31 PQ: 0 ANSI: 2
[ 3914.648853] scsi 8:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[ 3914.653335] sd 9:0:0:0: Attached scsi generic sg1 type 0
[ 3914.660677] sr0: scsi-1 drive
[ 3914.661064] sr 8:0:0:0: Attached scsi CD-ROM sr0
[ 3914.661459] sr 8:0:0:0: Attached scsi generic sg2 type 5
[ 3914.662637] sd 9:0:0:0: [sdb] Attached SCSI removable disk
[ 3929.370291] dhclient[18776]: segfault at 200 ip b73d2b29 sp bfb87a90 error 4 in libc-2.17.so[b738a000+1ad000]
[ 4189.705925] usb 2-3: USB disconnect, device number 2
[ 4189.720418] rtlwifi: reg 0x102, usbctrl_vendorreq TimeOut! status:0xffffffed value=0x8080740
[ 4189.720418] rtlwifi: reg 0x422, usbctrl_vendorreq TimeOut! status:0xffffffed value=0xd3c000
[ 4189.720418] rtlwifi: reg 0x542, usbctrl_vendorreq TimeOut! status:0xffffffed value=0xd30000
[ 4189.720418] rtlwifi: reg 0x608, usbctrl_vendorreq TimeOut! status:0xffffffed value=0xf0002a0e
[ 4189.745122] br0: port 2(wlan0) entered disabled state
[ 4189.746450] device wlan0 left promiscuous mode
[ 4189.746450] br0: port 2(wlan0) entered disabled state
[ 4197.282346] usb 1-1: USB disconnect, device number 6
[ 4197.286316] option1 ttyUSB6: option_instat_callback: error -108
[ 4197.286854] option1 ttyUSB6: GSM modem (1-port) converter now disconnected from ttyUSB6
[ 4197.286895] option 1-1:1.0: device disconnected
[ 4197.287029] qmi_wwan 1-1:1.1 wwan0: unregister 'qmi_wwan' usb-0000:02:02.3-1, WWAN/QMI device
[ 4197.307141] option1 ttyUSB7: GSM modem (1-port) converter now disconnected from ttyUSB7
[ 4197.307192] option 1-1:1.3: device disconnected
[ 4197.307517] option1 ttyUSB8: GSM modem (1-port) converter now disconnected from ttyUSB8
[ 4197.307561] option 1-1:1.4: device disconnected
[ 4285.255856] usb 2-3: new high-speed USB device number 3 using ehci-pci
[ 4285.387869] usb 2-3: New USB device found, idVendor=0bda, idProduct=8176
[ 4285.387869] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 4285.387876] usb 2-3: Product: 802.11n WLAN Adapter
[ 4285.387883] usb 2-3: Manufacturer: Realtek
[ 4285.387890] usb 2-3: SerialNumber: 00e04c000001
[ 4285.389080] rtl8192cu: Chip version 0x10
[ 4285.535908] rtl8192cu: MAC address: 90:f6:52:15:2a:10
[ 4285.535908] rtl8192cu: Board Type 0
[ 4285.535908] rtlwifi: rx_max_size 15360, rx_urb_num 8, in_ep 1
[ 4285.535944] rtl8192cu: Loading firmware rtlwifi/rtl8192cufw.bin
[ 4285.536487] ieee80211 phy1: Selected rate control algorithm 'rtl_rc'
[ 4285.540596] rtlwifi: wireless switch is on
[ 4313.646534] sierra ttyUSB5: Sierra USB modem converter now disconnected from ttyUSB5
[ 4313.646534] sierra 1-3:1.7: device disconnected
[ 4313.756575] usbserial: USB Serial deregistering driver Sierra USB modem
[ 4313.756575] sierra ttyUSB4: Sierra USB modem converter now disconnected from ttyUSB4
[ 4313.758969] sierra ttyUSB3: Sierra USB modem converter now disconnected from ttyUSB3
[ 4313.759173] sierra ttyUSB2: Sierra USB modem converter now disconnected from ttyUSB2
[ 4313.759321] sierra ttyUSB1: Sierra USB modem converter now disconnected from ttyUSB1
[ 4313.759459] sierra ttyUSB0: Sierra USB modem converter now disconnected from ttyUSB0
[ 4313.759501] usbcore: deregistering interface driver sierra
[ 4313.759588] sierra 1-3:1.4: device disconnected
[ 4313.759659] sierra 1-3:1.3: device disconnected
[ 4313.759724] sierra 1-3:1.2: device disconnected
[ 4313.759788] sierra 1-3:1.1: device disconnected
[ 4313.759855] sierra 1-3:1.0: device disconnected
[ 4313.966612] option 1-3:1.0: GSM modem (1-port) converter detected
[ 4313.966937] usb 1-3: GSM modem (1-port) converter now attached to ttyUSB0
[ 4313.967161] option 1-3:1.1: GSM modem (1-port) converter detected
[ 4313.967423] usb 1-3: GSM modem (1-port) converter now attached to ttyUSB1
[ 4313.967638] option 1-3:1.2: GSM modem (1-port) converter detected
[ 4313.967887] usb 1-3: GSM modem (1-port) converter now attached to ttyUSB2
[ 4313.968102] option 1-3:1.3: GSM modem (1-port) converter detected
[ 4313.968393] usb 1-3: GSM modem (1-port) converter now attached to ttyUSB3
[ 4313.968609] option 1-3:1.4: GSM modem (1-port) converter detected
[ 4313.970450] usb 1-3: GSM modem (1-port) converter now attached to ttyUSB4
[ 4313.970674] option 1-3:1.7: GSM modem (1-port) converter detected
[ 4313.970960] usb 1-3: GSM modem (1-port) converter now attached to ttyUSB5
[ 4465.939134] usb 1-1: new high-speed USB device number 7 using ehci-pci
[ 4466.071158] usb 1-1: New USB device found, idVendor=12d1, idProduct=1505
[ 4466.071158] usb 1-1: New USB device strings: Mfr=3, Product=2, SerialNumber=0
[ 4466.071164] usb 1-1: Product: HUAWEI Mobile
[ 4466.071171] usb 1-1: Manufacturer: Huawei Technologies
[ 4466.076281] scsi10 : usb-storage 1-1:1.0
[ 4466.076562] scsi11 : usb-storage 1-1:1.1
[ 4467.075366] scsi 11:0:0:0: Direct-Access     HUAWEI   TF CARD Storage  2.31 PQ: 0 ANSI: 2
[ 4467.077267] sd 11:0:0:0: Attached scsi generic sg1 type 0
[ 4467.085095] sd 11:0:0:0: [sdb] Attached SCSI removable disk
[ 4468.175329] usb 1-1: USB disconnect, device number 7
[ 4473.683619] usb 1-1: new high-speed USB device number 8 using ehci-pci
[ 4473.815652] usb 1-1: New USB device found, idVendor=12d1, idProduct=1506
[ 4473.815652] usb 1-1: New USB device strings: Mfr=4, Product=3, SerialNumber=0
[ 4473.815652] usb 1-1: Product: HUAWEI Mobile
[ 4473.815657] usb 1-1: Manufacturer: Huawei Technologies
[ 4473.820620] option 1-1:1.0: GSM modem (1-port) converter detected
[ 4473.821008] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB6
[ 4473.821008] qmi_wwan 1-1:1.1: cdc-wdm0: USB WDM device
[ 4473.823902] qmi_wwan 1-1:1.1 wwan0: register 'qmi_wwan' at usb-0000:02:02.3-1, WWAN/QMI device, 02:50:f3:00:00:00
[ 4473.824337] option 1-1:1.3: GSM modem (1-port) converter detected
[ 4473.825255] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB7
[ 4473.825497] option 1-1:1.4: GSM modem (1-port) converter detected
[ 4473.825975] usb 1-1: GSM modem (1-port) converter now attached to ttyUSB8
[ 4473.825975] scsi12 : usb-storage 1-1:1.5
[ 4473.828394] scsi13 : usb-storage 1-1:1.6
[ 4474.827855] scsi 13:0:0:0: Direct-Access     HUAWEI   TF CARD Storage  2.31 PQ: 0 ANSI: 2
[ 4474.827855] scsi 12:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[ 4474.832476] sd 13:0:0:0: Attached scsi generic sg1 type 0
[ 4474.841889] sr0: scsi-1 drive
[ 4474.842389] sr 12:0:0:0: Attached scsi CD-ROM sr0
[ 4474.842809] sr 12:0:0:0: Attached scsi generic sg2 type 5
[ 4474.844935] sd 13:0:0:0: [sdb] Attached SCSI removable disk
[ 4498.906836] dhclient[1840]: segfault at 200 ip b7444b29 sp bfb6b190 error 4 in libc-2.17.so[b73fc000+1ad000]
[ 5763.151550] init: Disconnected from system bus
[ 5763.155411] init: whoopsie main process ended, respawning
[ 5763.673933] bonding: bond0: Removing slave eth2.
[ 5763.674009] bonding: bond0: releasing active interface eth2
[ 5763.986026] bonding: bond0: Removing slave eth3.
[ 5763.986101] bonding: bond0: Removing an active aggregator
[ 5763.986116] bonding: bond0: releasing active interface eth3
[ 5763.986126] bonding: bond0: Warning: clearing HW address of bond0 while it still has VLANs.
[ 5763.986132] bonding: bond0: When re-adding slaves, make sure the bond's HW address matches its VLANs'.
[ 5765.108067] dhclient[6173]: segfault at 200 ip b73fcb29 sp bf962060 error 4 in libc-2.17.so[b73b4000+1ad000]
[ 5765.746245] init: deluged main process (6144) terminated with status 1
[ 5765.746341] init: deluged main process ended, respawning
[ 5766.437908] init: deluged main process (6181) terminated with status 1
[ 5766.437908] init: deluged main process ended, respawning
[ 5767.055635] init: deluged main process (6203) terminated with status 1
[ 5767.056514] init: deluged main process ended, respawning
[ 5767.674734] init: deluged main process (6207) terminated with status 1
[ 5767.674734] init: deluged main process ended, respawning
[ 5768.289931] init: deluged main process (6211) terminated with status 1
[ 5768.289931] init: deluged main process ended, respawning
[ 5768.902654] init: deluged main process (6215) terminated with status 1
[ 5768.902654] init: deluged respawning too fast, stopped
[ 5961.589303] init: ttyS0 main process ended, respawning
[ 6070.688660] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 6070.688678] 8021q: adding VLAN 0 to HW filter on device eth1
[ 6070.997031] bonding: bond0: Adding slave eth2.
[ 6071.076133] 8021q: adding VLAN 0 to HW filter on device eth2
[ 6071.076960] bonding: bond0: enslaving eth2 as a backup interface with a down link.
[ 6072.436633] e1000e: eth1 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[ 6072.436653] e1000e 0000:06:00.0 eth1: 10/100 speed: disabling TSO
[ 6072.436913] IPv6: ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[ 6072.531645] bonding: bond0: Adding slave eth3.
[ 6072.612379] 8021q: adding VLAN 0 to HW filter on device eth3
[ 6072.613214] bonding: bond0: enslaving eth3 as a backup interface with a down link.
[ 6073.712513] bonding: bond0: Setting MII monitoring interval to 100.
[ 6073.714003] bonding: unable to update mode of bond0 because interface is up.
[ 6073.717657] bonding: bond0: Unable to update LACP rate because interface is up.
[ 6074.324722] e1000e: eth2 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[ 6074.423632] bonding: bond0: link status definitely up for interface eth2, 1000 Mbps full duplex.
[ 6075.724830] e1000e: eth3 NIC Link is Up 1000 Mbps Full Duplex, Flow Control: Rx/Tx
[ 6075.823734] bonding: bond0: link status definitely up for interface eth3, 1000 Mbps full duplex.
[ 7081.390039] ------------[ cut here ]------------
[ 7081.390061] WARNING: at /build/buildd/linux-3.8.0/net/sched/sch_generic.c:254 dev_watchdog+0x1e7/0x1f0()
[ 7081.390068] NETDEV WATCHDOG: wwan0 (qmi_wwan): transmit queue 0 timed out
[ 7081.390073] Modules linked in: ipt_MASQUERADE(F) iptable_nat(F) nf_nat_ipv4(F) nf_nat(F) nf_conntrack_ipv4(F) nf_defrag_ipv4(F) xt_conntrack(F) nf_conntrack(F) iptable_filter(F) ip_tables(F) x_tables(F) ppp_deflate(F) zlib_deflate(F) bsd_comp(F) ppp_async(F) crc_ccitt(F) option qmi_wwan cdc_wdm usb_wwan usbnet usb_storage(F) 8021q(F) garp(F) bridge(F) stp(F) llc(F) kvm_intel kvm arc4(F) ie6xx_wdt i2c_isch gpio_sch rtl8192cu rtlwifi rtl8192c_common mac80211 cfg80211 microcode(F) usbserial pch_can can_dev pch_phub gpio_pch lpc_sch shpchp bonding(F) coretemp lp(F) parport(F) pch_gbe ptp_pch sdhci_pci ptp e1000e(F) pps_core sdhci ahci(F) libahci(F) [last unloaded: sierra]
[ 7081.390199] Pid: 0, comm: swapper/1 Tainted: GF            3.8.0-13-generic #23-Ubuntu
[ 7081.390204] Call Trace:
[ 7081.390220]  [<c104a4b2>] warn_slowpath_common+0x72/0xa0
[ 7081.390231]  [<c1549727>] ? dev_watchdog+0x1e7/0x1f0
[ 7081.390240]  [<c1549727>] ? dev_watchdog+0x1e7/0x1f0
[ 7081.390251]  [<c104a583>] warn_slowpath_fmt+0x33/0x40
[ 7081.390261]  [<c1549727>] dev_watchdog+0x1e7/0x1f0
[ 7081.390274]  [<c1058c3d>] call_timer_fn+0x2d/0xe0
[ 7081.390285]  [<c12a6347>] ? aa_free_task_context+0x57/0x90
[ 7081.390296]  [<c1070522>] ? hrtimer_run_pending+0x42/0xf0
[ 7081.390305]  [<c1549540>] ? dev_graft_qdisc+0x70/0x70
[ 7081.390315]  [<c105a601>] run_timer_softirq+0x181/0x220
[ 7081.390325]  [<c1549540>] ? dev_graft_qdisc+0x70/0x70
[ 7081.390335]  [<c1052573>] __do_softirq+0xa3/0x1b0
[ 7081.390344]  [<c10524d0>] ? local_bh_enable+0x90/0x90
[ 7081.390354]  [<c10524d0>] ? local_bh_enable+0x90/0x90
[ 7081.390359]  <IRQ>  [<c10527e5>] ? irq_exit+0x95/0xa0
[ 7081.390377]  [<c16197ce>] ? smp_apic_timer_interrupt+0x5e/0x8d
[ 7081.390387]  [<c107e530>] ? sched_clock_local+0x60/0x1b0
[ 7081.390398]  [<c1612380>] ? apic_timer_interrupt+0x34/0x3c
[ 7081.390409]  [<c109007b>] ? proc_sched_set_task+0x6b/0x70
[ 7081.390420]  [<c14e6f2a>] ? poll_idle+0x3a/0x90
[ 7081.390430]  [<c14e6b15>] ? cpuidle_enter+0x15/0x20
[ 7081.390440]  [<c14e73fe>] ? cpuidle_wrap_enter+0x2e/0x90
[ 7081.390450]  [<c14e7472>] ? cpuidle_enter_tk+0x12/0x20
[ 7081.390460]  [<c14e6b00>] ? nforce2_target+0x1b0/0x1b0
[ 7081.390470]  [<c14e7021>] ? cpuidle_enter_state+0x11/0x50
[ 7081.390479]  [<c14e70eb>] ? cpuidle_idle_call+0x8b/0x200
[ 7081.390490]  [<c101900a>] ? cpu_idle+0xaa/0xe0
[ 7081.390500]  [<c1602c9d>] ? start_secondary+0x1d9/0x1df
[ 7081.390507] ---[ end trace 2dfbfd79c83504bc ]---



```

---

### Post by bmork on 2013-04-03
> **BhimaPandava said:**
> In regards to my MC7710 having a odd device ID, I am not sure but I suspect this is because it is an engineering sample which I came by on happenstance.


Aw, right. Thanks for clarifying.  I should have noticed the serial number...


> 
  So I do not think changing the drivers based on this MC7710 is really the best idea. I am more than happy to make whatever changes on my system that are required... but I am not sure how to make them.


The procedure for changing PID is documented here: [http://forum.sierrawireless.com/viewtopic.php?f=117&t=6759](http://forum.sierrawireless.com/viewtopic.php?f=117&t=6759)

But do note that there is a reason for password protecting these commands.  They are intended for OEMs only.  Never attempt this unless you know your system will accept the new PID.  Many laptops will not, in which case you may have to remove the card and reset it using some other system.

I am only mentioning this for others reading this.  I assume that your Soekris system will accept any card regardless of PID.


> ```

S:  SerialNumber=001027009999999

```

There is a high probability that your operator will refuse this card because of that test IMEI. This indicates a non approved card.  And even if the operator allows it, there is a good chance of duplicates here...  That serial number does not look like a unique one.

Personally I would have thrown this card in the garbage and bought a real one from an authorized reseller.  My experience is that they sell the real cards cheaper than any of the current eBay offers anyway...  And you will probably get excellent technical support as well.

Sorry.

---

### Post by BhimaPandava on 2013-04-03
Thanks!  Based on your advice, I think I have made at least some progress... but I am still not able to connect to the internet.
Because of your comments about many ISPs not allowing engineering samples to connect, I am wondering if this is what I am experiencing. 

I was able to change the PID, and then with minicom configure a correct profile, turn the modem on, and connect.

The status is currently

```
AT!GSTATUS?#!GSTATUS:
Current Time:  3154             Temperature: 41
Bootup Time:   1                Mode:        ONLINE
System mode:   GSM              PS state:    Attached
GSM band:      DCS1800
GSM channel:   695
GMM (PS) state:REGISTERED       NORMAL SERVICE
MM (CS) state: IDLE             NORMAL SERVICE


Serving Cell:  695 (GSM 1800   )
RX level (dBm):-78.9375         LAC:         2F09 (12041)
GPRS State:    GPRS READY       Cell ID:     00001BB6 (7094)


OK
at!scpaddr=1
!SCPADDR: 1,"10.66.189.104"

```

And this IP address appears in my ifconfig for wwan0:

```

wwan0     Link encap:Ethernet  HWaddr 42:87:eb:54:01:07          inet addr:10.66.189.104  Bcast:10.66.189.255  Mask:255.255.255.0
          inet6 addr: fe80::4087:ebff:fe54:107/64 Scope:Link
          UP BROADCAST RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:170 errors:0 dropped:25 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:712 (712.0 B)  TX bytes:52579 (52.5 KB)
```

however, I am unable to ping anything (8.8.8.8 for example).
So now I am wondering if this is what you were describing looks like... or if I have just missed some important step.

---

### Post by bmork on 2013-04-03
> **BhimaPandava said:**
> Thanks!  Based on your advice, I think I have made at least some progress... but I am still not able to connect to the internet.
Because of your comments about many ISPs not allowing engineering samples to connect, I am wondering if this is what I am experiencing. 

I was able to change the PID, and then with minicom configure a correct profile, turn the modem on, and connect.

The status is currently

```
AT!GSTATUS?#!GSTATUS:
Current Time:  3154             Temperature: 41
Bootup Time:   1                Mode:        ONLINE
System mode:   GSM              PS state:    Attached
GSM band:      DCS1800
GSM channel:   695
GMM (PS) state:REGISTERED       NORMAL SERVICE
MM (CS) state: IDLE             NORMAL SERVICE


Serving Cell:  695 (GSM 1800   )
RX level (dBm):-78.9375         LAC:         2F09 (12041)
GPRS State:    GPRS READY       Cell ID:     00001BB6 (7094)


OK
at!scpaddr=1
!SCPADDR: 1,"10.66.189.104"

```

And this IP address appears in my ifconfig for wwan0:

```

wwan0     Link encap:Ethernet  HWaddr 42:87:eb:54:01:07          inet addr:10.66.189.104  Bcast:10.66.189.255  Mask:255.255.255.0
          inet6 addr: fe80::4087:ebff:fe54:107/64 Scope:Link
          UP BROADCAST RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:170 errors:0 dropped:25 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:712 (712.0 B)  TX bytes:52579 (52.5 KB)
```

however, I am unable to ping anything (8.8.8.8 for example).
So now I am wondering if this is what you were describing looks like... or if I have just missed some important step.

This all looks good.  Is routing OK?  What does "ip route" say?  The netmask looks weird for a mobile broadband modem.   How did you configure these addresses?  I assume this didn't come from the DHCP server in the modem?

---

### Post by BhimaPandava on 2013-04-03
Hi Bjørn,  I got that IP address by using minicom
```
at+cfun=1at+cgdcont=1,"IP","drei.at"
at!scdftprof=1
at!scprof=1,"",0,0,0,0
at!scact=1,1
at!scpaddr=1
```

Which, after reading your advice more closely, is using Direct IP and not qmi (I think). Therefore, I reset the modem and have been trying to use qmicli.  So far this has failed and I think it could be due to the fact that my ISP won't let the device connect. However, I am not really sure what my ISP refusing to allow the device to connect to their network looks like and I haven't seen an error which makes me certain this is what is going on.  Also I have discovered a way to change the IMEI, and I can get a new IMEI number from the person who gave me the device, but it requires the use of the "[COLOR=#222225][FONT=Arial]Qualcomm Product Support Tool" which is windows only. Unfortunately I don't own anything which both has a Mini-PCIe socket and supports running Windows in a VM (as you are probably aware the Soekris devices don't have provisions for displays).[/FONT][/COLOR]

The basic connection command qmicli -d /dev/cdc-wdm0 --wds-start-network --client-no-release-cid fails with error: couldn't start network: QMI protocol error (14): 'CallFailed'call end reason (1): generic-unspecified
verbose call end reason (0,26): [(null)] (null).

The output with the verbose switch is: 

```
[03 Apr 2013, 20:43:53] [Debug] QMI Device at '/dev/cdc-wdm0' ready
[03 Apr 2013, 20:43:53] [Debug] [/dev/cdc-wdm0] Assuming service 'wds' is supported...
[03 Apr 2013, 20:43:53] [Debug] [/dev/cdc-wdm0] Allocating new client ID...
[03 Apr 2013, 20:43:53] [Debug] [/dev/cdc-wdm0] Sent message...
<<<<<< RAW:
<<<<<<   length = 16
<<<<<<   data   = 01:0F:00:00:00:00:00:01:22:00:04:00:01:01:00:01


[03 Apr 2013, 20:43:53] [Debug] [/dev/cdc-wdm0] Sent message (translated)...
<<<<<< QMUX:
<<<<<<   length  = 15
<<<<<<   flags   = 0x00
<<<<<<   service = "ctl"
<<<<<<   client  = 0
<<<<<< QMI:
<<<<<<   flags       = "none"
<<<<<<   transaction = 1
<<<<<<   tlv_length  = 4
<<<<<<   message     = "Allocate CID" (0x0022)
<<<<<< TLV:
<<<<<<   type       = "Service" (0x01)
<<<<<<   length     = 1
<<<<<<   value      = 01
<<<<<<   translated = wds


[03 Apr 2013, 20:43:53] [Debug] [/dev/cdc-wdm0] Received message...
>>>>>> RAW:
>>>>>>   length = 24
>>>>>>   data   = 01:17:00:80:00:00:01:01:22:00:0C:00:02:04:00:00:00:00:00:01:02:00:01:05


[03 Apr 2013, 20:43:53] [Debug] [/dev/cdc-wdm0] Received message (translated)...
>>>>>> QMUX:
>>>>>>   length  = 23
>>>>>>   flags   = 0x80
>>>>>>   service = "ctl"
>>>>>>   client  = 0
>>>>>> QMI:
>>>>>>   flags       = "response"
>>>>>>   transaction = 1
>>>>>>   tlv_length  = 12
>>>>>>   message     = "Allocate CID" (0x0022)
>>>>>> TLV:
>>>>>>   type       = "Result" (0x02)
>>>>>>   length     = 4
>>>>>>   value      = 00:00:00:00
>>>>>>   translated = SUCCESS
>>>>>> TLV:
>>>>>>   type       = "Allocation Info" (0x01)
>>>>>>   length     = 2
>>>>>>   value      = 01:05
>>>>>>   translated = [ service = 'wds' cid = '5' ]


[03 Apr 2013, 20:43:53] [Debug] [/dev/cdc-wdm0] Registered 'wds' (version unknown) client with ID '5'
[03 Apr 2013, 20:43:53] [Debug] Asynchronously starting network...
[03 Apr 2013, 20:43:53] [Debug] [/dev/cdc-wdm0] Sent message...
<<<<<< RAW:
<<<<<<   length = 39
<<<<<<   data   = 01:26:00:00:01:05:00:01:00:20:00:1A:00:14:17:00:2D:2D:63:6C:69:65:6E:74:2D:6E:6F:2D:72:65:6C:65:61:73:65:2D:63:69:64


[03 Apr 2013, 20:43:53] [Debug] [/dev/cdc-wdm0] Sent message (translated)...
<<<<<< QMUX:
<<<<<<   length  = 38
<<<<<<   flags   = 0x00
<<<<<<   service = "wds"
<<<<<<   client  = 5
<<<<<< QMI:
<<<<<<   flags       = "none"
<<<<<<   transaction = 1
<<<<<<   tlv_length  = 26
<<<<<<   message     = "Start Network" (0x0020)
<<<<<< TLV:
<<<<<<   type       = "APN" (0x14)
<<<<<<   length     = 23
<<<<<<   value      = 2D:2D:63:6C:69:65:6E:74:2D:6E:6F:2D:72:65:6C:65:61:73:65:2D:63:69:64
<<<<<<   translated = --client-no-release-cid


[03 Apr 2013, 20:43:53] [Debug] [/dev/cdc-wdm0] Received message...
>>>>>> RAW:
>>>>>>   length = 32
>>>>>>   data   = 01:1F:00:80:01:05:02:01:00:20:00:13:00:02:04:00:01:00:0E:00:10:02:00:01:00:11:04:00:00:00:1A:00


[03 Apr 2013, 20:43:53] [Debug] [/dev/cdc-wdm0] Received message (translated)...
>>>>>> QMUX:
>>>>>>   length  = 31
>>>>>>   flags   = 0x80
>>>>>>   service = "wds"
>>>>>>   client  = 5
>>>>>> QMI:
>>>>>>   flags       = "response"
>>>>>>   transaction = 1
>>>>>>   tlv_length  = 19
>>>>>>   message     = "Start Network" (0x0020)
>>>>>> TLV:
>>>>>>   type       = "Result" (0x02)
>>>>>>   length     = 4
>>>>>>   value      = 01:00:0E:00
>>>>>>   translated = FAILURE: CallFailed
>>>>>> TLV:
>>>>>>   type       = "Call End Reason" (0x10)
>>>>>>   length     = 2
>>>>>>   value      = 01:00
>>>>>>   translated = generic-unspecified
>>>>>> TLV:
>>>>>>   type       = "Verbose Call End Reason" (0x11)
>>>>>>   length     = 4
>>>>>>   value      = 00:00:1A:00
>>>>>>   translated = [ type = '(null)' reason = '26' ]


error: couldn't start network: QMI protocol error (14): 'CallFailed'
call end reason (1): generic-unspecified
verbose call end reason (0,26): [(null)] (null)
[03 Apr 2013, 20:43:53] [Debug] [/dev/cdc-wdm0] Unregistered 'wds' client with ID '5'
[03 Apr 2013, 20:43:53] [Debug] [/dev/cdc-wdm0] Sent message...
<<<<<< RAW:
<<<<<<   length = 17
<<<<<<   data   = 01:10:00:00:00:00:00:02:23:00:05:00:01:02:00:01:05


[03 Apr 2013, 20:43:53] [Debug] [/dev/cdc-wdm0] Sent message (translated)...
<<<<<< QMUX:
<<<<<<   length  = 16
<<<<<<   flags   = 0x00
<<<<<<   service = "ctl"
<<<<<<   client  = 0
<<<<<< QMI:
<<<<<<   flags       = "none"
<<<<<<   transaction = 2
<<<<<<   tlv_length  = 5
<<<<<<   message     = "Release CID" (0x0023)
<<<<<< TLV:
<<<<<<   type       = "Release Info" (0x01)
<<<<<<   length     = 2
<<<<<<   value      = 01:05
<<<<<<   translated = [ service = 'wds' cid = '5' ]


[03 Apr 2013, 20:43:53] [Debug] [/dev/cdc-wdm0] Received message...
>>>>>> RAW:
>>>>>>   length = 24
>>>>>>   data   = 01:17:00:80:00:00:01:02:23:00:0C:00:02:04:00:00:00:00:00:01:02:00:01:05


[03 Apr 2013, 20:43:53] [Debug] [/dev/cdc-wdm0] Received message (translated)...
>>>>>> QMUX:
>>>>>>   length  = 23
>>>>>>   flags   = 0x80
>>>>>>   service = "ctl"
>>>>>>   client  = 0
>>>>>> QMI:
>>>>>>   flags       = "response"
>>>>>>   transaction = 2
>>>>>>   tlv_length  = 12
>>>>>>   message     = "Release CID" (0x0023)
>>>>>> TLV:
>>>>>>   type       = "Result" (0x02)
>>>>>>   length     = 4
>>>>>>   value      = 00:00:00:00
>>>>>>   translated = SUCCESS
>>>>>> TLV:
>>>>>>   type       = "Release Info" (0x01)
>>>>>>   length     = 2
>>>>>>   value      = 01:05
>>>>>>   translated = [ service = 'wds' cid = '5' ]


[03 Apr 2013, 20:43:54] [Debug] Client released
```



  What I am doing now is itterating through all the possible qmicli commands, in an attempt to more clearly understand things.  Many of the commands return promising results, while others fail.  This makes me think that your supposition that I have old firmware is correct.. but I am not sure how to update it or even where to find a current version.

Here are some of the commands I have tried, in case you find them informative.

```

qmicli -d /dev/cdc-wdm0    --dms-uim-get-pin-status
[/dev/cdc-wdm0] PIN status retrieved successfully
[/dev/cdc-wdm0] PIN1:
    Status: disabled
    Verify: 3
    Unblock: 10
[/dev/cdc-wdm0] PIN2:
    Status: enabled-not-verified
    Verify: 3
    Unblock: 10

qmicli -d /dev/cdc-wdm0    --dms-uim-get-iccid
[/dev/cdc-wdm0] UIM ICCID retrieved:
    ICCID: '8943102100921038202'



qmicli -d /dev/cdc-wdm0    --dms-uim-get-imsi
[/dev/cdc-wdm0] UIM IMSI retrieved:
    IMSI: '232106922753935'

qmicli -d /dev/cdc-wdm0    --dms-uim-get-state
[/dev/cdc-wdm0] UIM state retrieved:
    State: 'initialization-completed'

qmicli -d /dev/cdc-wdm0 --dms-get-hardware-revision
[/dev/cdc-wdm0] Hardware revision retrieved:
    Revision: '203F0000'



qmicli -d /dev/cdc-wdm0 --dms-get-operating-mode
[/dev/cdc-wdm0] Operating mode retrieved:
    Mode: 'online'
    HW restricted: 'no'

qmicli -d /dev/cdc-wdm0    --dms-get-prl-version
error: couldn't get the PRL version: QMI protocol error (25): 'DeviceUnsupported'

qmicli -d /dev/cdc-wdm0 --dms-get-activation-state
error: couldn't get the state of the service activation: QMI protocol error (71): 'InvalidQmiCommand'


qmicli -d /dev/cdc-wdm0  --dms-get-band-capabilities
[/dev/cdc-wdm0] Device band capabilities retrieved:
    Bands: 'gsm-dcs-1800, gsm-900-extended, gsm-900-primary, gsm-850, gsm-pcs-1900, wcdma-2100, wcdma-pcs-1900, wcdma-1700-us, wcdma-850-us'



qmicli -d /dev/cdc-wdm0    --nas-get-signal-strength[/dev/cdc-wdm0] Successfully got signal strength
Current:
    Network 'umts': '-81 dBm'
RSSI:
    Network 'umts': '-81 dBm'
ECIO:
    Network 'umts': '-6.0 dBm'

qmicli -d /dev/cdc-wdm0    --nas-get-signal-info
error: couldn't get signal info: QMI protocol error (71): 'InvalidQmiCommand'

qmicli -d /dev/cdc-wdm0    --nas-get-home-network
[/dev/cdc-wdm0] Successfully got home network:
    Home network:
        MCC: '232'
        MNC: '10'
        Description: '3 AT'

qmicli -d /dev/cdc-wdm0    --nas-get-serving-system
[03 Apr 2013, 20:46:44] -Warning ** Cannot read the 'Detailed Service Status' TLV: expected '5' bytes, but only got '4' bytes
[/dev/cdc-wdm0] Successfully got serving system:
    Registration state: 'registered'
    CS: 'attached'
    PS: 'attached'
    Selected network: '3gpp'
    Radio interfaces: '1'
        [0]: 'umts'
    Roaming status: 'off'
    Data service capabilities: '1'
        [0]: 'wcdma'
    Current PLMN:
        MCC: '232'
        MNC: '10'
        Description: '3 AT'
    Roaming indicators: '1'
        [0]: 'off' (umts)
    3GPP daylight saving time adjustment: '1' hours
    3GPP location area code: '0'
    3GPP cell ID: '14497301'

qmicli -d /dev/cdc-wdm0    --nas-get-system-info
error: couldn't get system info: QMI protocol error (71): 'InvalidQmiCommand'

qmicli -d /dev/cdc-wdm0    --nas-get-technology-preference
error: couldn't get technology preference: QMI protocol error (71): 'InvalidQmiCommand'

qmicli -d /dev/cdc-wdm0    --nas-get-system-selection-preference
[/dev/cdc-wdm0] Successfully got system selection preference
    Emergency mode: 'no'
    Mode preference: 'umts'
    Band preference: 'gsm-dcs-1800, gsm-900-extended, gsm-900-primary, wcdma-2100'
    LTE band preference: '(null)'
    Roaming preference: 'any'
    Network selection preference: 'automatic'

qmicli -d /dev/cdc-wdm0    --nas-network-scan
[/dev/cdc-wdm0] Successfully scanned networks

qmicli -d /dev/cdc-wdm0 --wds-start-network=drei.at
error: couldn't start network: QMI protocol error (14): 'CallFailed'
call end reason (1): generic-unspecified
verbose call end reason (2,204): [internal] unknown-cause


```

---

### Post by bmork on 2013-04-05
> **BhimaPandava said:**
> Hi Bjørn,  I got that IP address by using minicom
```
at+cfun=1at+cgdcont=1,"IP","drei.at"
at!scdftprof=1
at!scprof=1,"",0,0,0,0
at!scact=1,1
at!scpaddr=1
```

Which, after reading your advice more closely, is using Direct IP and not qmi (I think).

Well, that was an assumption.  I haven't really verified it.  Sierra Wireless could have implemented support for these commands regardless of mode I guess, and your success with them supports that.


> 
Also I have discovered a way to change the IMEI, and I can get a new  IMEI number from the person who gave me the device, but it requires the  use of the "[COLOR=#222225][FONT=Arial]Qualcomm  Product Support Tool" which is windows only. Unfortunately I don't own  anything which both has a Mini-PCIe socket and supports running Windows  in a VM (as you are probably aware the Soekris devices don't have  provisions for displays).[/FONT][/COLOR]


No need to fiddle with that.  I believe the output you posted proves me wrong.  Your operator does accept this IMEI.

> 
 This makes me think that your supposition that I have old firmware is  correct.. but I am not sure how to update it or even where to find a  current version.

 
Firmware is only available through the official support channels. Sierra Wireless provides a Linux SDK with a sample application for firmware management, so upgrading the card in a Soekris system should be possible.  But I don't think any of the missing commands really matters. Many of them are unsupported in newer firmware as well.


> 
```

qmicli -d /dev/cdc-wdm0    --nas-get-home-network
[/dev/cdc-wdm0] Successfully got home network:
    Home network:
        MCC: '232'
        MNC: '10'
        Description: '3 AT'

qmicli -d /dev/cdc-wdm0    --nas-get-serving-system
[03 Apr 2013, 20:46:44] -Warning ** Cannot read the 'Detailed Service Status' TLV: expected '5' bytes, but only got '4' bytes
[/dev/cdc-wdm0] Successfully got serving system:
    Registration state: 'registered'
    CS: 'attached'
    PS: 'attached'
    Selected network: '3gpp'
    Radio interfaces: '1'
        [0]: 'umts'
    Roaming status: 'off'
    Data service capabilities: '1'
        [0]: 'wcdma'
    Current PLMN:
        MCC: '232'
        MNC: '10'
        Description: '3 AT'
    Roaming indicators: '1'
        [0]: 'off' (umts)
    3GPP daylight saving time adjustment: '1' hours
    3GPP location area code: '0'
    3GPP cell ID: '14497301'


```

This looks all good and shows that my worries were wrong.  You are definitely registered with your home network, despite the test IMEI. So that should not be a problem for you after all.


> 
```

qmicli -d /dev/cdc-wdm0 --wds-start-network=drei.at
error: couldn't start network: QMI protocol error (14): 'CallFailed'
call end reason (1): generic-unspecified
verbose call end reason (2,204): [internal] unknown-cause

```

That's not very informational.  I have no idea why this happens and how to avoid it.

Eyyyh!  I think I found the problem looking at the details another time:

```


<<<<<<   flags       = "none" <<<<<<   transaction = 1 <<<<<<   tlv_length  = 26 <<<<<<   message     = "Start Network" (0x0020) <<<<<< TLV: <<<<<<   type       = "APN" (0x14) <<<<<<   length     = 23 <<<<<<   value      = 2D:2D:63:6C:69:65:6E:74:2D:6E:6F:2D:72:65:6C:65:61:73:65:2D:63:69:64 <<<<<<   translated = --client-no-release-cid

```

Your APN configuration is wrong.  You are using the text "--client-no-release-cid" as your APN instead of "drei.at".  That is not likely to work :)

---

### Post by BhimaPandava on 2013-04-05
OK great!  That's good news... mostly.

Unfortunately, I am still unable to use the connection on the MC7710 that I establish using qmi commands.  So I feel that I must have missed something important somewhere in the process.  I'd like to start again from the beginning.  Don't forget that I have 2 modems installed, one is a USB Huawei e372 and the other is the MC7710.  Also, I have been connecting at boot with the e372 using sakis3g & utmskeeper.  When I try to use the MC7710, I have been simply disconnecting the e372 with sakis3g.

In particular I am confused about ifconfig & dhcp addresses.  As adding wwan declarations in etc/network/interfaces causes the networking service restart to hang waiting forever to get a dhcp address... z.b. "localhost dhclient: DHCPDISCOVER onwwan0 to 255.255.255.255 port 67 interval 19 (xid=0x3c20275a)".

So from the top:

The MC7710 is installed and I installed the drivers / kernel modules.

lsmod shows: qcserial, option, usb_wwan, usbserial, qmi_wwan, cdc_wdm (among others).
usb-devices shows qmi-wwan interfaces for both devices.
/dev/ includes both cdc-wdm0 & cdc-wdm1
qmicli -d /dev/cdc-wdm1 --dms-get-ids confirms that wdm0 is the e372 and wdm1 is the MC7710.

With no wwan entries in etc/network/interfaces, using the qmi-network script appears to be occasionally successful but I am confused by the "source not found" warning. (etc/qmi-network.conf contains: "APN=drei.at")

```


qmi-network /dev/cdc-wdm1 start
Loading profile...
/usr/bin/qmi-network: 38: /usr/bin/qmi-network: **source: not found**
Starting network with 'qmicli -d /dev/cdc-wdm1 --wds-start-network=  --client-no-release-cid'...
Saving state... (CID: 14)
Saving state... (PDH: 38852936)
Network started successfully
Saving state... (CID: 14)Saving state... (PDH: 38852936)
Network started successfully
```

Then "dhcpcd wwan1" occasionally returns: "dhcpcd.sh: interface wwan1 has been configured with new IP=10.72.182.97" although it too has hung waiting for a dhcp address pretty often.

and ifconfig wwan1 returns:
```

           wwan1     Link encap:Ethernet  HWaddr 16:75:d7:53:4e:01
          inet addr:10.72.182.97  Bcast:10.72.182.99  Mask:255.255.255.252
          inet6 addr: fe80::1475:d7ff:fe53:4e01/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:676 (676.0 B)  TX bytes:2190 (2.1 KB)

```

However, I still can't use the connection.. ping 8.8.8.8 fails with "connect: Network is unreachable".  I tried clearing iptables, just in case, but it did not help.

Also using qmi-network & dhcpcd on the e372 occasionally works and then I can use that connection.  However, I have not worked out how to make them automatically connect with it using qmi instead of ppp at boot time.

Still, I'm quite pleased with the progress I've been able to make so far, thanks to your help!

---

### Post by bmork on 2013-04-06
> **BhimaPandava said:**
> OK great!  That's good news... mostly.

Unfortunately, I am still unable to use the connection on the MC7710 that I establish using qmi commands.  So I feel that I must have missed something important somewhere in the process.  I'd like to start again from the beginning.  Don't forget that I have 2 modems installed, one is a USB Huawei e372 and the other is the MC7710.  Also, I have been connecting at boot with the e372 using sakis3g & utmskeeper.  When I try to use the MC7710, I have been simply disconnecting the e372 with sakis3g.

In particular I am confused about ifconfig & dhcp addresses.  As adding wwan declarations in etc/network/interfaces causes the networking service restart to hang waiting forever to get a dhcp address... z.b. "localhost dhclient: DHCPDISCOVER onwwan0 to 255.255.255.255 port 67 interval 19 (xid=0x3c20275a)".


Yes, you will most likely want some monitoring daemon of some sort to manage those interfaces.  The modems will respond to dhcp requests, but only after the connection is up.  So you need something that is aware of this.

> 

So from the top:

The MC7710 is installed and I installed the drivers / kernel modules.

lsmod shows: qcserial, option, usb_wwan, usbserial, qmi_wwan, cdc_wdm (among others).
usb-devices shows qmi-wwan interfaces for both devices.
/dev/ includes both cdc-wdm0 & cdc-wdm1
qmicli -d /dev/cdc-wdm1 --dms-get-ids confirms that wdm0 is the e372 and wdm1 is the MC7710.

With no wwan entries in etc/network/interfaces, using the qmi-network script appears to be occasionally successful but I am confused by the "source not found" warning. (etc/qmi-network.conf contains: "APN=drei.at")

```


qmi-network /dev/cdc-wdm1 start
Loading profile...
/usr/bin/qmi-network: 38: /usr/bin/qmi-network: **source: not found**
Starting network with 'qmicli -d /dev/cdc-wdm1 --wds-start-network=  --client-no-release-cid'...

```


Right.  So the bogus APN is related to the** source: not found** warning.  Are you using some strange shell for /bin/sh?  It seems that the script is unable to read the /etc/qmi-network.conf file.

> 
```

Saving state... (CID: 14)
Saving state... (PDH: 38852936)
Network started successfully
Saving state... (CID: 14)Saving state... (PDH: 38852936)
Network started successfully
```


OK?  So it connects using the " --client-no-release-cid" as APN?  I don't think that helps, though, as I believe the connection will be dropped when the CID is released. You really need to fix whatever prevents the proper APN from being set.

> 
Then "dhcpcd wwan1" occasionally returns: "dhcpcd.sh: interface wwan1 has been configured with new IP=10.72.182.97" although it too has hung waiting for a dhcp address pretty often.

and ifconfig wwan1 returns:
```

           wwan1     Link encap:Ethernet  HWaddr 16:75:d7:53:4e:01
          inet addr:10.72.182.97  Bcast:10.72.182.99  Mask:255.255.255.252
          inet6 addr: fe80::1475:d7ff:fe53:4e01/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:676 (676.0 B)  TX bytes:2190 (2.1 KB)

```

However, I still can't use the connection.. ping 8.8.8.8 fails with "connect: Network is unreachable".  I tried clearing iptables, just in case, but it did not help.


Which is likely because the connection dropped right after the interface was configured.  You need to monitor the connection and keep it up, possibly restarting the dhcp client if a new address is required.  There is no way to do this using plain ifupdown scripts.  You need some monitoring application.

> 
Also using qmi-network & dhcpcd on the e372 occasionally works and then I can use that connection.  However, I have not worked out how to make them automatically connect with it using qmi instead of ppp at boot time.

Still, I'm quite pleased with the progress I've been able to make so far, thanks to your help!

The real answer is using ModemManager or some other smart daemon.

Simply automatically connect on boot can be done by writing the appropriate scripts (possibly using qmi-network directly) and call them prior to configuring the interface, using 'pre-up' commands.

But this will not solve the task of keeping the connection up and running.

---

### Post by BhimaPandava on 2013-04-07
That is a sort of an unsurprising problem (which I understand) with an unexpected response.

I have been tinkering with the fish shell and one of my co-workers often uses zsh. However, I have simply installed them and haven't even changed the default away from bash. We just call them manually when we want to use them.  Thinking about when things work and when they don't, I am unable to confirm if I have been running fish when they fail or if I am still in bash when they work. (I'm assuming their mere presence in the system isn't a big deal). I will have to test this theory to have a more reliable understanding.

I have the impression that Modem Manager is intended to be used, with a GUI, in combination with Network Manager.  Also, I read somewhere that Network Manager was designed for use cases like laptops and wasn't really intended to be used in headless servers... although thinking about it, I guess there aren't many people trying to set up servers in locations out in the field with terrible internet service... so perhaps that advice doesn't really cover my use case. 

Searching around, I have been unable to find a usable example of using Modem Manager from the command line... so I am beginning to suspect that "using Modem Manager" winds up meaning "using Network Manager in combination Modem Manager", is that the case?  This evening I will try to install Network Manager & Modem Manager and do all of this in the "Network Manager"... but I am not sure if that is an appropriate long term solution (or even why it wouldn't be).

---

### Post by bmork on 2013-04-07
> **BhimaPandava said:**
> I have the impression that Modem Manager is intended to be used, with a GUI, in combination with Network Manager.  Also, I read somewhere that Network Manager was designed for use cases like laptops and wasn't really intended to be used in headless servers... although thinking about it, I guess there aren't many people trying to set up servers in locations out in the field with terrible internet service... so perhaps that advice doesn't really cover my use case. 

Neither ModemManager nor NetworkManager require a GUI.  They are dbus based daemons.   The use cases definitely includes more than just laptops, but of course not complex routers or really advanced server setups.  Should still fit most 3G/LTE modem use cases.

> 
Searching around, I have been unable to find a usable example of using Modem Manager from the command line... so I am beginning to suspect that "using Modem Manager" winds up meaning "using Network Manager in combination Modem Manager", is that the case?  This evening I will try to install Network Manager & Modem Manager and do all of this in the "Network Manager"... but I am not sure if that is an appropriate long term solution (or even why it wouldn't be).

There are command line utilites for both (mmcli and nmcli).

If you don't want to go with this option, then maybe side looking at the even smaller embedded systems is an idea?  There is quite a lot of work going on adding QMI support to OpenWRT at the moment.  It looks very promising.

---

### Post by BhimaPandava on 2013-04-09
I am unable to find mmcli, it wasn't installed with either network-manager or modemmanager packages.  I also can't really compile the whole modemmanger because it has all the GUI stuff... and trying to compile it sends me into a rabbit hole of missing dependancies.

Having now compiled the modem manager the resultant mmcli does not appear to understand the local dbus setup (as in it can't find it).

Also, I obtained a mini-PCIe to USB adapter and I am able to easily connect to the internet with this MC7710 from within a Ubuntu 13.04 desktop VM.  However, I did have to go through a short wizard which obviously a desktop GUI applet thing.  However, surely this created the correct configuration somewhere... no?  If I could find them, could I use them in my headless server?

---

### Post by BhimaPandava on 2013-04-14
Just an update my current confused status.  After getting the modem working in an Ubuntu 13.04 Desktop VM, I have discovered that it only connected at the slowest protocol in "roaming" mode and after a few minutes will not connect at all anymore. Now, I am wondering if this is not due to oddball IMEI that Bjørn noted earlier.

---

