---
title: "BCM4311 problems"
date: 2009-02-03
forum: Networking &amp; Wireless
---

### Post by Calmatory on 2009-02-03
HP530 with BCM4311 fails to connect to router.

ifup wlan0:
```

asdman@asdman-laptop:~$ sudo ifup wlan0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1a:73:9e:01:6b
Sending on   LPF/wlan0/00:1a:73:9e:01:6b
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

lshw -C network:
```
asdman@asdman-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 01
       serial: 00:1b:38:82:dc:38
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A ip=192.168.0.11 latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:73:9e:01:6b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```

iwconfig:
```
asdman@asdman-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"wlanman"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

iwlist scanning:
```
asdman@asdman-laptop:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

```


A laptop next to me running Vista works flawlessly with the wireless, so the problem shouldn't be the router settings.

---

### Post by Ayuthia on 2009-02-03
Have you installed the firmware via System->Administration->Hardware Drivers or installed b43-fwcutter (Same as going through Hardware Drivers)?

EDIT:  It looks like you did.  Can you check the results of:
```
lsmod|grep -e b43 -e wl
```

It might be that Network Manager is conflicting with the Terminal commands.

---

### Post by Calmatory on 2009-02-03
```
asdman@asdman-laptop:~$ lsmod|grep -e b43 -e wl
b43                   131356  0 
ssb                    40580  1 b43
rfkill                 17176  3 b43,rfkill_input
mac80211              216820  1 b43
led_class              12164  1 b43
input_polldev          11912  1 b43

```

---

### Post by Ayuthia on 2009-02-03
Is there anything in dmesg:
```
dmesg|grep b43
```
Also does it work if you switch over to the wl module:
```
sudo modprobe -r b43 ssb wl
sudo modprobe wl
sudo ifconfig eth1 up
sudo iwlist scan
```

---

### Post by Calmatory on 2009-02-03
Plenty of stuff:

```
[  515.146099] b43-pci-bridge 0000:10:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  515.146116] b43-pci-bridge 0000:10:00.0: setting latency timer to 64
[  515.253243] b43-phy0: Broadcom 4311 WLAN found
[  519.563492] input: b43-phy0 as /devices/virtual/input/input8
[  519.652072] firmware: requesting b43/ucode5.fw
[  519.655621] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[  519.655632] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[  519.697143] input: b43-phy0 as /devices/virtual/input/input9
[  519.756063] firmware: requesting b43/ucode5.fw
[  519.758902] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[  519.758912] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[  635.823744] input: b43-phy0 as /devices/virtual/input/input10
[  635.888062] firmware: requesting b43/ucode5.fw
[  635.891861] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[  635.891870] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[  635.969399] input: b43-phy0 as /devices/virtual/input/input11
[  636.032059] firmware: requesting b43/ucode5.fw
[  636.034705] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[  636.034714] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[  636.072873] input: b43-phy0 as /devices/virtual/input/input12
[  636.140049] firmware: requesting b43/ucode5.fw
[  636.142735] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[  636.142745] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[  698.099594] input: b43-phy0 as /devices/virtual/input/input13
[  698.164071] firmware: requesting b43/ucode5.fw
[  698.166979] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[  698.166989] b43-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[  755.099834] b43-pci-bridge 0000:10:00.0: PCI INT A disabled
[  765.170926] b43-pci-bridge 0000:10:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  765.170943] b43-pci-bridge 0000:10:00.0: setting latency timer to 64
[  765.264175] b43-phy1: Broadcom 4311 WLAN found
[  765.429373] input: b43-phy1 as /devices/virtual/input/input14
[  765.516091] firmware: requesting b43/ucode5.fw
[  765.518848] b43-phy1 ERROR: Firmware file "b43/ucode5.fw" not found
[  765.518859] b43-phy1 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[  765.592297] input: b43-phy1 as /devices/virtual/input/input15
[  765.664081] firmware: requesting b43/ucode5.fw
[  765.669668] b43-phy1 ERROR: Firmware file "b43/ucode5.fw" not found
[  765.669678] b43-phy1 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[  765.709620] input: b43-phy1 as /devices/virtual/input/input16
[  765.772078] firmware: requesting b43/ucode5.fw
[  765.774913] b43-phy1 ERROR: Firmware file "b43/ucode5.fw" not found
[  765.774923] b43-phy1 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[  769.563627] input: b43-phy1 as /devices/virtual/input/input17
[  769.628062] firmware: requesting b43/ucode5.fw
[  769.631915] b43-phy1 ERROR: Firmware file "b43/ucode5.fw" not found
[  769.631925] b43-phy1 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[  769.676103] input: b43-phy1 as /devices/virtual/input/input18
[  769.744065] firmware: requesting b43/ucode5.fw
[  769.747709] b43-phy1 ERROR: Firmware file "b43/ucode5.fw" not found
[  769.747719] b43-phy1 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[  795.156054] input: b43-phy1 as /devices/virtual/input/input19
[  795.220050] firmware: requesting b43/ucode5.fw
[  795.222777] b43-phy1 ERROR: Firmware file "b43/ucode5.fw" not found
[  795.222787] b43-phy1 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[  795.310664] input: b43-phy1 as /devices/virtual/input/input20
[  795.376064] firmware: requesting b43/ucode5.fw
[  795.378461] b43-phy1 ERROR: Firmware file "b43/ucode5.fw" not found
[  795.378470] b43-phy1 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[  795.412188] input: b43-phy1 as /devices/virtual/input/input21
[  795.476046] firmware: requesting b43/ucode5.fw
[  795.478758] b43-phy1 ERROR: Firmware file "b43/ucode5.fw" not found
[  795.478769] b43-phy1 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[  821.536685] input: b43-phy1 as /devices/virtual/input/input22
[  821.608046] firmware: requesting b43/ucode5.fw
[  821.610853] b43-phy1 ERROR: Firmware file "b43/ucode5.fw" not found
[  821.610863] b43-phy1 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[  830.084035] input: b43-phy1 as /devices/virtual/input/input23
[  830.148048] firmware: requesting b43/ucode5.fw
[  830.150751] b43-phy1 ERROR: Firmware file "b43/ucode5.fw" not found
[  830.150761] b43-phy1 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[  835.502319] input: b43-phy1 as /devices/virtual/input/input24
[  835.568055] firmware: requesting b43/ucode5.fw
[  835.570873] b43-phy1 ERROR: Firmware file "b43/ucode5.fw" not found
[  835.570883] b43-phy1 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[ 1206.334991] input: b43-phy1 as /devices/virtual/input/input25
[ 1206.400049] firmware: requesting b43/ucode5.fw
[ 1206.402749] b43-phy1 ERROR: Firmware file "b43/ucode5.fw" not found
[ 1206.402759] b43-phy1 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[ 1417.331619] input: b43-phy1 as /devices/virtual/input/input26
[ 1417.396804] firmware: requesting b43/ucode5.fw
[ 1417.399353] b43-phy1 ERROR: Firmware file "b43/ucode5.fw" not found
[ 1417.399363] b43-phy1 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[ 1525.752332] b43-phy2: Broadcom 4311 WLAN found
[ 1525.950389] input: b43-phy2 as /devices/virtual/input/input27
[ 1526.044091] firmware: requesting b43/ucode5.fw
[ 1526.046968] b43-phy2 ERROR: Firmware file "b43/ucode5.fw" not found
[ 1526.046978] b43-phy2 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[ 1526.172329] input: b43-phy2 as /devices/virtual/input/input28
[ 1526.236352] firmware: requesting b43/ucode5.fw
[ 1526.239005] b43-phy2 ERROR: Firmware file "b43/ucode5.fw" not found
[ 1526.239015] b43-phy2 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[ 1526.297543] input: b43-phy2 as /devices/virtual/input/input29
[ 1526.368059] firmware: requesting b43/ucode5.fw
[ 1526.372792] b43-phy2 ERROR: Firmware file "b43/ucode5.fw" not found
[ 1526.372802] b43-phy2 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[ 1530.142005] input: b43-phy2 as /devices/virtual/input/input30
[ 1530.256065] firmware: requesting b43/ucode5.fw
[ 1530.269963] b43-phy2 ERROR: Firmware file "b43/ucode5.fw" not found
[ 1530.269973] b43-phy2 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[ 1530.377945] input: b43-phy2 as /devices/virtual/input/input31
[ 1530.496067] firmware: requesting b43/ucode5.fw
[ 1530.498915] b43-phy2 ERROR: Firmware file "b43/ucode5.fw" not found
[ 1530.498925] b43-phy2 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the latest firmware (version 4).
[ 1589.335724] input: b43-phy2 as /devices/virtual/input/input32
[ 1589.408063] firmware: requesting b43/ucode5.fw
[ 1589.410800] firmware: requesting b43/pcm5.fw
[ 1589.416217] firmware: requesting b43/b0g0initvals5.fw
[ 1589.420975] firmware: requesting b43/b0g0bsinitvals5.fw
[ 1589.540075] b43-phy2: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1589.710389] Registered led device: b43-phy2::tx
[ 1589.710657] Registered led device: b43-phy2::rx
[ 1589.710839] Registered led device: b43-phy2::radio
[ 1590.368088] b43-phy2: Radio hardware status changed to DISABLED
[ 1590.468053] b43-phy2: Radio turned on by software
[ 1590.468062] b43-phy2: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
[ 1943.198341] input: b43-phy2 as /devices/virtual/input/input33
[ 1943.408077] b43-phy2: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 1943.546378] Registered led device: b43-phy2::tx
[ 1943.546891] Registered led device: b43-phy2::rx
[ 1943.547317] Registered led device: b43-phy2::radio
[ 1944.220063] b43-phy2: Radio hardware status changed to DISABLED
[ 3759.938994] input: b43-phy2 as /devices/virtual/input/input34
[ 3760.215434] b43-phy2: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 3760.376429] Registered led device: b43-phy2::tx
[ 3760.378008] Registered led device: b43-phy2::rx
[ 3760.378521] Registered led device: b43-phy2::radio
[ 3760.960147] b43-phy2: Radio hardware status changed to DISABLED
[ 3770.856039] b43-phy2: Radio turned on by software
[ 3770.856049] b43-phy2: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
[ 3818.847959] input: b43-phy2 as /devices/virtual/input/input35
[ 3819.120214] b43-phy2: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 3819.263461] Registered led device: b43-phy2::tx
[ 3819.263971] Registered led device: b43-phy2::rx
[ 3819.264424] Registered led device: b43-phy2::radio
[ 3819.872043] b43-phy2: Radio hardware status changed to DISABLED
[ 3912.627915] input: b43-phy2 as /devices/virtual/input/input36
[ 3912.841747] b43-phy2: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 3912.983624] Registered led device: b43-phy2::tx
[ 3912.984971] Registered led device: b43-phy2::rx
[ 3912.985229] Registered led device: b43-phy2::radio
[ 3913.644042] b43-phy2: Radio hardware status changed to DISABLED
[ 3950.868034] b43-phy2: Radio turned on by software
[ 3950.868043] b43-phy2: The hardware RF-kill button still turns the radio physically off. Press the button to turn it on.
[ 6573.787331] input: b43-phy2 as /devices/virtual/input/input37
[ 6574.084398] b43-phy2: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[ 6574.234379] Registered led device: b43-phy2::tx
[ 6574.234925] Registered led device: b43-phy2::rx
[ 6574.235352] Registered led device: b43-phy2::radio
[ 6574.808037] b43-phy2: Radio hardware status changed to DISABLED

```

and it seems that the wl module does not work either.

---

### Post by Ayuthia on 2009-02-03
You are missing the firmware.  You can install it by either going into System->Administration->Hardware Drivers or through Synaptic by installing b43-fwcutter.

---

### Post by Calmatory on 2009-02-03
No I am not.

I tried to install via apt-get, but it said I already (obviously, using b43 driver) have the package. So I thought that the dmesg info was outdated due to my old experiments. I rebooted and this is what I get now:

```
asdman@asdman-laptop:~$ dmesg | grep b43
[    3.488211] b43-pci-bridge 0000:10:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    3.488224] b43-pci-bridge 0000:10:00.0: setting latency timer to 64
[   16.535379] b43-phy0: Broadcom 4311 WLAN found
[   21.913844] input: b43-phy0 as /devices/virtual/input/input8
[   22.000094] firmware: requesting b43/ucode5.fw
[   22.064177] firmware: requesting b43/pcm5.fw
[   22.068297] firmware: requesting b43/b0g0initvals5.fw
[   22.072649] firmware: requesting b43/b0g0bsinitvals5.fw
[   22.192067] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   22.362207] Registered led device: b43-phy0::tx
[   22.362235] Registered led device: b43-phy0::rx
[   22.362259] Registered led device: b43-phy0::radio
[   22.932060] b43-phy0: Radio hardware status changed to DISABLED
asdman@asdman-laptop:~$ 

```

Oh, and now my nm-applet shows "Device is unmanaged" under "wireless". All greyed out though, even without Ethernet cable. Guess we are close. :)

If I comment the ```
auto wlan0
iface wlan0 inet dhcp
``` lines in /etc/network/interfaces I get this:
```
asdman@asdman-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...
Ignoring unknown interface wlan0=wlan0.

```
if they remain uncommented:
```
asdman@asdman-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                                                       Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:1a:73:9e:01:6b
Sending on   LPF/wlan0/00:1a:73:9e:01:6b
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

Could this possibly indicate something?
```

asdman@asdman-laptop:~$ sudo ifup wlan0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/
[b]
wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
[/b]

```

Edit: It seems that "Device is unmanaged" refers to [ifupdown]->managed field in /etc/NetworkManager/nm-system-settings.conf. Using true instead of false just removes the "Device is unmanaged" text but seems to have no other consequences.

---

### Post by Ayuthia on 2009-02-03
Sorry.  I did not read far enough down on the dmesg.  It also says that the hardware rf kill switch is physically off.  Have you checked that?

---

### Post by Calmatory on 2009-02-04
Problem got solved. 

Yes, it seems that the radio was disabled from BIOS. I do not know why, but it seems that reverting to default settings will disable it.

Thank you for your help. :)

---

