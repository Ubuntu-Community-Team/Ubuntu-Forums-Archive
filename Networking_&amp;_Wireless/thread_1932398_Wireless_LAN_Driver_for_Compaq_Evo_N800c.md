---
title: "Wireless LAN Driver for Compaq Evo N800c"
date: 2012-02-27
forum: Networking &amp; Wireless
---

### Post by jrahman on 2012-02-27
Hi, I am new in Ubuntu (but not in Linux).
I just installed latest Ubuntu (11.10) on a Compaq Evo N800c laptop. Everything working fine except for Wireless LAN.

This laptop has a semi-integrated wireless module, they call it "Multiport", which supports  802.11b, more information is here: [[COLOR="Green"]**_802.11b MultiPort Module_**[/COLOR]]("http://h18000.www1.hp.com/products/quickspecs/11344_na/11344_na.html") (go down the page and serach for this section).

Is there any driver I could find for this WLAN device to work in Ubuntu ? Note, the wired ethernet connection is woking perfect. which is built in to the laptop.

Thanks.

---

### Post by chili555 on 2012-02-27
Please open a terminal and run and post:```
lspci -nn | grep 0280
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by jrahman on 2012-02-27
lspci -nn | grep 0280 returns nothing.

However, there are some information after running "lspci -nn"

```

jrahman@CompaqUbuntu:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge [8086:1a30] (rev 04)
00:01.0 PCI bridge [0604]: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge [8086:1a31] (rev 04)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 42)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801CAM ISA Bridge (LPC) [8086:248c] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801CAM IDE U100 Controller [8086:248a] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801CA/CAM AC'97 Audio Controller [8086:2485] (rev 02)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500] [1002:4c57]
02:04.0 Communication controller [0780]: Agere Systems LT WinModem [11c1:0450] (rev 02)
02:06.0 CardBus bridge [0607]: Texas Instruments PCI1410 PC card Cardbus Controller [104c:ac50] (rev 02)
02:08.0 Ethernet controller [0200]: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller [8086:1031] (rev 42)
02:0e.0 USB Controller [0c03]: NEC Corporation USB [1033:0035] (rev 41)
02:0e.1 USB Controller [0c03]: NEC Corporation USB [1033:0035] (rev 41)
02:0e.2 USB Controller [0c03]: NEC Corporation USB 2.0 [1033:00e0] (rev 02)

```

---

### Post by chili555 on 2012-02-28
There is no wireless device there. I noticed this in the data you linked:> 802.11b MultiPort Module
	Form Factor 	Compaq "MultiPort" 	 
Weight 	0.22 lb (100 g) (maximum)
Operating Temperature 	Operating 	14° to 149° F (–10° to 65° C)
Storage Temperature 	Non-operating 	–40° to 176° F (–40° to 80° C)
Humidity 	Operating 	10% to 90%
Non-operating 	5% to 95%
Altitude 	Operating 	0 to 15,000 ft (4,572 m)
Non-operating 	0 to 40,000 ft (12,192 m)
[COLOR="Red"]Plug and Play 	**USB** 1.1 compliant[/COLOR]
Microsoft Windows Plug and Play compliant
RF Network Standard 	IEEE 802 Part 11b (802.11b)
<snip>I wonder if it is actually connected to a USB port internally. That's a bit rare but not unknown. Let's have a look at:```
lsusb
```Thanks.

---

### Post by jrahman on 2012-02-28
The lsusb returns as below.
Notice the second last line: **[COLOR="DarkGreen"]Compaq Computer Corp. Wireless LAN MultiPort W200[/COLOR]**
```

jrahman@CompaqUbuntu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 001 Device 003: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 002 Device 002: ID 049f:0076 Compaq Computer Corp. Wireless LAN MultiPort W200
Bus 001 Device 005: ID 04b3:310b IBM Corp. Red Wheel Mouse

```

---

### Post by chili555 on 2012-02-29
> ID 049f:0076 Compaq Computer Corp. Wireless LAN MultiPort W200Your device uses the driver orinoco_usb which is already installed:> $ modinfo orinoco_usb 
filename:       /lib/modules/3.0.0-16-generic/kernel/drivers/net/wireless/orinoco/orinoco_usb.ko
license:        Dual MPL/GPL
description:    Driver for Orinoco wireless LAN cards using EZUSB bridge
author:         Manuel Estrada Sainz
[COLOR="Red"]firmware:       orinoco_ezusb_fw[/COLOR]
srcversion:     9A0C9BDFA0E2C5F908ED115
alias:          usb:v0D4Ep047Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v1630pFF81d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0BF8p1002d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0681p0012d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04E8p7011d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04E8p5B11d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v04E8p5002d0000dc*dsc*dp*ic*isc*ip*
alias:          usb:v0E7Cp0300d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v05CCp3100d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0D4Ep1001d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0D4Ep1000d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0D9Ep0300d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0D98p0300d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v047Ep0300d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p000Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p000Bd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0411p0006d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v[COLOR="Red"]049F[/COLOR]p[COLOR="Red"]0076[/COLOR]d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v049Fp0082d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v049Fp001Fd*dc*dsc*dp*ic*isc*ip*
depends:        orinoco
vermagic:       3.0.0-16-generic SMP mod_unload modversions 686 
parm:           debug:Debug enabled or not (int)It requires firmware which is *not* installed by default. With the ethernet hooked up, please run each of these commands in order. You may copy and paste into the terminal. Proofread carefully at each step:```
wget http://replay.waybackmachine.org/20061206062642/http://www.agere.com/mobility/docs/windows_drivers_sr02-2.3.zip
unzip windows_drivers_sr02-2.3.zip WLAGS51.SYS
dd if=WLAGS51.SYS of=orinoco_ezusb_fw skip=10312 count=436 bs=16
sudo cp orinoco_ezusb_fw /lib/firmware
```Now detach the ethernet cable and reboot. Please give us your report.

---

### Post by jrahman on 2012-02-29
Thanks for a great help, Finally, I could activate the Multiport wireless device. 
However, I can't still connect to the network (my router).
I know this is a separate issue than activating the Multiport device, but I need your help.

I have done the followings to create the Wireless connection:
1. System Settings-->Wireless-->Network Name (chose "dlink", this my SSID)
2. Then opened configuration window by clicking the "Configure..." button
3. Configuration parameters are:[INDENT]     a. Connect Automatically checked
    b. SSID = dlink (my network name)
    c. Mode = Infrastructure
    d. BSSID = (none)
    e. Device MAC address = Address of the Multiport (acquired from ifconfig)
     f. Cloned MAC address = (none)
     g. MTU = Automatic[/INDENT]

---

### Post by chili555 on 2012-02-29
Let's have a look at:```
rfkill list all
sudo iwlist wlan0 scan
```We are close!

---

### Post by jrahman on 2012-03-01
Thanks again for your time.

Note that, the **ifconfig** shows that the Muliport WLAN is recognized as "**[COLOR="Blue"]eth1[/COLOR]**" NOT "**[COLOR="blue"]wlan0[/COLOR]**"
```

jrahman@CompaqUbuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:08:02:62:fb:49  
          inet addr:192.168.0.103  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::208:2ff:fe62:fb49/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:91354 errors:0 dropped:0 overruns:0 frame:0
          TX packets:119030 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13058711 (13.0 MB)  TX bytes:149093074 (149.0 MB)

eth1      Link encap:Ethernet  HWaddr 00:0b:cd:8c:e6:d2  
          inet6 addr: fe80::20b:cdff:fe8c:e6d2/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:5791 (5.7 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:44160 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44160 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:144007695 (144.0 MB)  TX bytes:144007695 (144.0 MB)

```

Here are the returns from two commands:

First command: **[COLOR="Blue"]rfkill list all[/COLOR]**
```

jrahman@CompaqUbuntu:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

Second command: **[COLOR="Blue"]sudo iwlist eth1 scan[/COLOR]**
(**Cell01** is my router, "**dlink**")
```

jrahman@CompaqUbuntu:~$ sudo iwlist eth1 scan
[sudo] password for jrahman: 
eth1      Scan completed :
          Cell 01 - Address: 00:24:01:E3:01:F9
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-33 dBm  
                    Encryption key:off
                    ESSID:"dlink"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000035c3c9cd
                    Extra: Last beacon: 176ms ago
                    IE: Unknown: 0005646C696E6B
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 2A0102
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
                    IE: Unknown: DD1E00904C334E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C3406051B00000000000000000000000000000000000000
                    IE: Unknown: 3D1606051B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010004000000
                    IE: Unknown: DD7B0050F204104A00011010440001021041000100103B00010310470010565AA94967C14C0EAA8FF349E6F5931110210006442D4C696E6B1023000D442D4C696E6B20526F75746572102400074449522D363135104200046E6F6E651054000800060050F204000110110006442D4C696E6B100800020084103C000101
          Cell 02 - Address: 5C:D9:98:6F:32:EE
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"svinka"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000002726afa4fa2
                    Extra: Last beacon: 356ms ago
                    IE: Unknown: 00067376696E6B61
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010000004000
                    IE: Unknown: DD9E0050F204104A0001101044000102103B00010310470010000000000000100000005CD9986F32EE10210006442D4C696E6B1023000D442D4C696E6B20526F75746572102400074449522D363135104200046E6F6E651054000800060050F204000110110016442D4C696E6B2053797374656D73204449522D363135100800020086103C000103104900140024E26002000101600000020001600100020001
          Cell 03 - Address: 00:13:F7:AB:E0:A2
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"SHAVER"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000390396bce0d
                    Extra: Last beacon: 328ms ago
                    IE: Unknown: 0006534841564552
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030102
                    IE: Unknown: 2A0103
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK


```

---

### Post by chili555 on 2012-03-01
Network Manager is designed to *disallow* a wireless connection if wired is available; yours obviously is because it's connected and you have an IP address:> eth0      Link encap:Ethernet  HWaddr 00:08:02:62:fb:49  
          inet addr:[COLOR="Red"]192.168.0.103[/COLOR]  Bcast:192.168.0.255  Mask:255.255.255.0Please detach the cable, wait a few moments for NM to notice the change in state and see if you see your network listed as available when you click the NM icon. Does it connect?

All of your readings look solid.

---

### Post by jrahman on 2012-03-01
No luck yet, even after disconnecting the cable,
One interesting fact: when I enable or disable the wireless device by toggling Fn2 key (this laptop has this wireless enable switch), I could see the changes in the list under All Settings list of System Settings-->Network. When disabled, "Wireless" is disappeared from the list and appears again when toggled back to enabled.

Here is the [COLOR=Blue]ifconfig[/COLOR] return:
```
jrahman@JamilCompaqUbuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:08:02:62:fb:49  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr 00:0b:cd:8c:e6:d2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1296 (1.2 KB)  TX bytes:1296 (1.2 KB)
```

---

### Post by chili555 on 2012-03-02
> When disabled, "Wireless" is disappeared from the list and appears again when toggled back to enabled.That's a very good sign. Let's see what the message logs say about all this. With the ethernet cable detached, please run and post:```
dmesg | grep orinoco
sudo cat /var/log/syslog | grep etwork | tail -n20
```Thanks.

---

### Post by jrahman on 2012-03-02
***Only wireless device connected (network cable disconnected)***
Returns from [COLOR=Blue]**dmesg | grep orinoco**[/COLOR]:
```

jrahman@CompaqUbuntu:~$ dmesg | grep orinoco 
 [   19.610583] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al) 
 [   19.651622] orinoco_usb 0.15 (Manuel Estrada Sainz) 
 [   23.734083] usbcore: registered new interface driver orinoco_usb 
 [ 1366.576710] orinoco_usb: ezusb_bulk_in_callback: short read, ignoring 
 [ 1366.576721] orinoco_usb: ezusb_submit_in_urb submit failed -19 
 [ 1366.590316] orinoco_usb: Disconnected 
 [ 2952.522634] orinoco_usb: ezusb_bulk_in_callback: short read, ignoring 
 [ 2952.522644] orinoco_usb: ezusb_submit_in_urb submit failed -19 
 [ 2952.534237] orinoco_usb: Disconnected 
 [ 7124.479370] orinoco_usb: ezusb_bulk_in_callback: short read, ignoring 
 [ 7124.479381] orinoco_usb: ezusb_submit_in_urb submit failed -19 
 [ 7124.490001] orinoco_usb: Disconnected
 
```Returns from [COLOR=Blue]**sudo cat /var/log/syslog | grep Network**[/COLOR] (deliberately didn't put [COLOR=Blue]***tail -n20***[/COLOR], to see more lines).

Notes:

[LIST]
[*]Wireless connection name: Wireless Connection 1
[*]Network ID: eth1 (not wlan0)
[*]SSID; dlink (my router)
[/LIST]
```

 Mar  2 20:22:04 CompaqUbuntu NetworkManager[500]: <info> found WiFi radio killswitch rfkill4 (at /sys/devices/pci0000:00/0000:00:1e.0/0000:02:0e.0/usb2/2-3/ieee80211/phy4/rfkill4) (driver (unknown)) 
 Mar  2 20:22:04 CompaqUbuntu NetworkManager[500]: <info> (eth1): driver supports SSID scans (scan_capa 0x01). 
 Mar  2 20:22:04 CompaqUbuntu NetworkManager[500]: <info> (eth1): new 802.11 WiFi device (driver: 'usb' ifindex: 7) 
 Mar  2 20:22:04 CompaqUbuntu NetworkManager[500]: <info> (eth1): exported as /org/freedesktop/NetworkManager/Devices/5 
 Mar  2 20:22:04 CompaqUbuntu NetworkManager[500]: <info> (eth1): now managed 
 Mar  2 20:22:04 CompaqUbuntu NetworkManager[500]: <info> (eth1): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2] 
 Mar  2 20:22:04 CompaqUbuntu NetworkManager[500]: <info> (eth1): bringing up device. 
 Mar  2 20:22:04 CompaqUbuntu NetworkManager[500]: <info> (eth1): preparing device. 
 Mar  2 20:22:04 CompaqUbuntu NetworkManager[500]: <info> (eth1): deactivating device (reason 'managed') [2] 
 Mar  2 20:22:04 CompaqUbuntu NetworkManager[500]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:0e.0/usb2/2-3/net/eth1, iface: eth1) 
 Mar  2 20:22:04 CompaqUbuntu NetworkManager[500]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:1e.0/0000:02:0e.0/usb2/2-3/net/eth1, iface: eth1): no ifupdown configuration found. 
 Mar  2 20:22:05 CompaqUbuntu NetworkManager[500]: <info> (eth1): supplicant interface state: starting -> ready 
 Mar  2 20:22:05 CompaqUbuntu NetworkManager[500]: <info> (eth1): device state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42] 
 Mar  2 20:22:05 CompaqUbuntu NetworkManager[500]: <info> (eth1): supplicant interface state: ready -> inactive 
 Mar  2 20:22:05 CompaqUbuntu NetworkManager[500]: <info> Auto-activating connection 'Wireless connection 1'. 
 Mar  2 20:22:05 CompaqUbuntu NetworkManager[500]: <info> Activation (eth1) starting connection 'Wireless connection 1' 
 Mar  2 20:22:05 CompaqUbuntu NetworkManager[500]: <info> (eth1): device state change: disconnected -> prepare (reason 'none') [30 40 0] 
 Mar  2 20:22:05 CompaqUbuntu NetworkManager[500]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
 Mar  2 20:22:05 CompaqUbuntu NetworkManager[500]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
 Mar  2 20:22:05 CompaqUbuntu NetworkManager[500]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
 Mar  2 20:22:05 CompaqUbuntu NetworkManager[500]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
 Mar  2 20:22:05 CompaqUbuntu NetworkManager[500]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
 Mar  2 20:22:05 CompaqUbuntu NetworkManager[500]: <info> (eth1): device state change: prepare -> config (reason 'none') [40 50 0] 
 Mar  2 20:22:05 CompaqUbuntu NetworkManager[500]: <info> Activation (eth1/wireless): connection 'Wireless connection 1' requires no security.  No secrets needed. 
 Mar  2 20:22:05 CompaqUbuntu NetworkManager[500]: <info> Config: added 'ssid' value 'dlink' 
 Mar  2 20:22:05 CompaqUbuntu NetworkManager[500]: <info> Config: added 'scan_ssid' value '1' 
 Mar  2 20:22:05 CompaqUbuntu NetworkManager[500]: <info> Config: added 'key_mgmt' value 'NONE' 
 Mar  2 20:22:05 CompaqUbuntu NetworkManager[500]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
 Mar  2 20:22:05 CompaqUbuntu NetworkManager[500]: <info> Config: set interface ap_scan to 1 
 Mar  2 20:22:05 CompaqUbuntu NetworkManager[500]: <info> (eth1): supplicant interface state: inactive -> scanning 
 Mar  2 20:22:06 CompaqUbuntu NetworkManager[500]: <info> (eth1): supplicant interface state: scanning -> associating 
 Mar  2 20:22:11 CompaqUbuntu NetworkManager[500]: <info> (eth1): supplicant interface state: associating -> scanning 
 Mar  2 20:22:11 CompaqUbuntu NetworkManager[500]: <info> (eth1): supplicant interface state: scanning -> associating 
 Mar  2 20:22:16 CompaqUbuntu NetworkManager[500]: <info> (eth1): supplicant interface state: associating -> scanning 
 Mar  2 20:22:17 CompaqUbuntu NetworkManager[500]: <info> (eth1): supplicant interface state: scanning -> associating 
 Mar  2 20:22:22 CompaqUbuntu NetworkManager[500]: <info> (eth1): supplicant interface state: associating -> scanning 
 Mar  2 20:22:23 CompaqUbuntu NetworkManager[500]: <info> (eth1): supplicant interface state: scanning -> associating 
 Mar  2 20:22:28 CompaqUbuntu NetworkManager[500]: <info> (eth1): supplicant interface state: associating -> scanning 
 Mar  2 20:22:29 CompaqUbuntu NetworkManager[500]: <info> (eth1): supplicant interface state: scanning -> associating 
 Mar  2 20:22:34 CompaqUbuntu NetworkManager[500]: <info> (eth1): supplicant interface state: associating -> scanning 
 Mar  2 20:22:34 CompaqUbuntu NetworkManager[500]: <info> (eth1): supplicant interface state: scanning -> associating 
 Mar  2 20:22:39 CompaqUbuntu NetworkManager[500]: <info> (eth1): supplicant interface state: associating -> scanning 
 Mar  2 20:22:40 CompaqUbuntu NetworkManager[500]: <info> (eth1): supplicant interface state: scanning -> associating 
 Mar  2 20:22:45 CompaqUbuntu NetworkManager[500]: <info> (eth1): supplicant interface state: associating -> scanning 
 Mar  2 20:22:46 CompaqUbuntu NetworkManager[500]: <info> (eth1): supplicant interface state: scanning -> associating 
 Mar  2 20:22:51 CompaqUbuntu NetworkManager[500]: <info> (eth1): supplicant interface state: associating -> scanning 
 Mar  2 20:22:51 CompaqUbuntu NetworkManager[500]: <info> (eth1): supplicant interface state: scanning -> associating 
 Mar  2 20:22:56 CompaqUbuntu NetworkManager[500]: <info> (eth1): supplicant interface state: associating -> scanning 
 Mar  2 20:22:57 CompaqUbuntu NetworkManager[500]: <info> (eth1): supplicant interface state: scanning -> associating 
 Mar  2 20:23:02 CompaqUbuntu NetworkManager[500]: <info> (eth1): supplicant interface state: associating -> scanning 
 Mar  2 20:23:03 CompaqUbuntu NetworkManager[500]: <info> (eth1): supplicant interface state: scanning -> associating 
 Mar  2 20:23:05 CompaqUbuntu NetworkManager[500]: <warn> Activation (eth1/wireless): association took too long, failing activation. 
 Mar  2 20:23:05 CompaqUbuntu NetworkManager[500]: <info> (eth1): device state change: config -> failed (reason 'supplicant-timeout') [50 120 11] 
 Mar  2 20:23:05 CompaqUbuntu NetworkManager[500]: <warn> Activation (eth1) failed for access point (dlink) 
 Mar  2 20:23:05 CompaqUbuntu NetworkManager[500]: <info> Marking connection 'Wireless connection 1' invalid. 
 Mar  2 20:23:05 CompaqUbuntu NetworkManager[500]: <warn> Activation (eth1) failed. 
 Mar  2 20:23:05 CompaqUbuntu NetworkManager[500]: <info> (eth1): device state change: failed -> disconnected (reason 'none') [120 30 0] 
 Mar  2 20:23:05 CompaqUbuntu NetworkManager[500]: <info> (eth1): deactivating device (reason 'none') [0] 
 Mar  2 20:23:05 CompaqUbuntu NetworkManager[500]: <info> (eth1): supplicant interface state: associating -> disconnected 
 Mar  2 20:23:05 CompaqUbuntu NetworkManager[500]: <warn> Couldn't disconnect supplicant interface: This interface is not connected. 
 

```

---

### Post by chili555 on 2012-03-03
Frankly, I am kind of stumped. This is actually the very first time I've encountered this driver and even Google is bereft of clues. 

What, if any, settings have you set in Network Manager? None, I hope. If you have manually set any details, delete them all and delete 'Auto dlink' if it appears, from the wireless tab. If Network Manager and the driver work as expected, no manual settings are needed. I am fearful that any manually added settings that are inadvertantly incorrect may be hindering connection. 

These look ominous:> [ 1366.576710] orinoco_usb: ezusb_bulk_in_callback: short read, ignoring 
 [ 1366.576721] orinoco_usb: ezusb_submit_in_urb submit failed -19 
 [ 1366.590316] orinoco_usb: Disconnected However, this all looks just fine!>  <info> Config: set interface ap_scan to 1 
  <info> (eth1): supplicant interface state: inactive -> scanning 
  <info> (eth1): supplicant interface state: scanning -> associating However, it never quite makes a connection.

There is an updated driver which you can install (with the ethernet attached):```
sudo apt-get install linux-backports-modules-cw-3.1-oneiric-generic
```If that doesn't help, we may need to try ndiswrapper.

---

### Post by jrahman on 2012-03-03
> 
If that doesn't help, we may need to try ndiswrapper.


Unfortunately, the update driver didn't bring any luck :-(
Could you please forward me the instructions for ndiswrapper ?

Thanks a lot for all the helps you provided.

---

### Post by chili555 on 2012-03-04
Before we tackle the ndiswrapper project, let's try newer firmware. Please download the attached file to your desktop. Right-click it and select *Extract Here*. Now open a terminal and back up the current firmware:```
sudo mv /lib/firmware/orinoco_ezusb_fw /lib/firmware/orinoco_ezusb_fw.bak
```Now we copy over the newer firmware:```
sudo cp Desktop/orinoco_ezusb_fw /lib/firmware/
```Now unload and reload the driver:```
sudo modprobe -rv orinoco_usb
sudo modprobe orinoco_usb
```You may also try a reboot.

Any improvement?

---

### Post by jrahman on 2012-03-04
I have installed the latest driver you sent.
Unfortunately, situation is more worst, I can't:
1. see any LED of the Multiport wireless module
2. toggle the wireless module activation by Fn2 key
3. see any "Wireless" under System Settings-->Network list
4. see any eth1 (which is wireless module ID) from *[COLOR=Blue]**ifconfig**[/COLOR]*

```

jrahman@JamilCompaqUbuntu:/lib/firmware$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:08:02:62:fb:49  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:48 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4000 (4.0 KB)  TX bytes:4000 (4.0 KB)

```

---

### Post by chili555 on 2012-03-04
Ouch! Are there any clues in the message logs?```
dmesg | grep -e Firm -e orin
```Is the firmware in place with the correct permissions?```
ls -al /lib/firmware | grep orin
```Thanks.

---

### Post by jrahman on 2012-03-04
> 
Is the firmware in place with the correct permissions?
Here is the *[COLOR=Blue]**ls**[/COLOR]* return:
```
jrahman@CompaqUbuntu:~$ ls -al /lib/firmware | grep orinoco 
 -rw-r--r--  1 root root    6976 2012-03-04 16:09 orinoco_ezusb_fw 
 -rw-r--r--  1 root root    6976 2012-02-29 13:34 orinoco_ezusb_fw.bak
 
```Here is the ***[COLOR=Blue]dmesg | grep -e Firm -e orinoco[/COLOR]***      return
(notice, there are two different versions of USB fw, ***[COLOR=Blue]highlighted blue[/COLOR]***) <-- do they make any conflict ?
```
jrahman@CompaqUbuntu:~$ dmesg | grep -e Firm -e orinoco
 598.150257] orinoco_usb: ezusb_bulk_in_callback: short read, ignoring 
 ....
 ....
 [  599.695244] orinoco_usb: ezusb_bulk_in_callback: short read, ignoring 
 [  599.696245] orinoco_usb: ezusb_bulk_in_callback: short read, ignoring 
 [  599.697245] orinoco_usb: ezusb_bulk_in_callback: short read, ignoring 
 [  599.697263] orinoco_usb: ezusb_access_ltv: Unexpected context state 3 
 [  599.697272] orinoco_usb: Access failed, resetting (state 3, reply_count 63) 
 [  599.697279] orinoco_usb: ctx failed 
 [  599.698253] orinoco_usb: ezusb_bulk_in_callback: short read, ignoring 
 [  599.699250] orinoco_usb: ezusb_bulk_in_callback: short read, ignoring 
 [  599.699261] orinoco_usb: ezusb_submit_in_urb submit failed -19 
 [  599.702052] orinoco_usb: Failed to reset 
 [  599.702067] eth1: orinoco_reset: Error -19 performing hard reset 
 [  599.702422] orinoco_usb: Called, CTX not terminating, but device gone 
 [  599.708364] orinoco_usb: Disconnected 
 ***[COLOR=Blue][  601.188413] usb 2-3: Firmware determined as Lucent/Agere 8.58 [/COLOR]***
 ***[COLOR=Blue][ 601.764457] usb 2-3: Firmware determined as Lucent/Agere 9.48 [/COLOR]***
 [  602.066232] orinoco_usb: ezusb_bulk_in_callback: short read, ignoring 
 [  602.066243] orinoco_usb: ezusb_submit_in_urb submit failed -19 
 [  602.083357] orinoco_usb: Disconnected 
 [  752.325354] usbcore: deregistering interface driver orinoco_usb 
 [  768.355174] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al) 
 [  768.358235] orinoco_usb 0.15 (Manuel Estrada Sainz) 
 [  768.358312] usbcore: registered new interface driver orinoco_usb 
 [  776.645135] orinoco_usb: EZUSB_REQUEST_TRIGER failed retval -110 
 [  776.645148] orinoco_usb: Cannot reset the device 
 [  776.645193] orinoco_usb: probe of 2-3:1.0 failed with error -14 
 [  789.225114] orinoco_usb: EZUSB_REQUEST_TRIGER failed retval -110 
 [  789.225126] orinoco_usb: Cannot reset the device 
 [  789.225173] orinoco_usb: probe of 2-3:1.0 failed with error -14 
 [  798.929130] orinoco_usb: EZUSB_REQUEST_TRIGER failed retval -110 
 [  798.929142] orinoco_usb: Cannot reset the device 
 [  798.929194] orinoco_usb: probe of 2-3:1.0 failed with error -14 
 [  809.221113] orinoco_usb: EZUSB_REQUEST_TRIGER failed retval -110 
 [  809.221125] orinoco_usb: Cannot reset the device 
 [  809.221176] orinoco_usb: probe of 2-3:1.0 failed with error -14 
 [11244.049111] orinoco_usb: EZUSB_REQUEST_TRIGER failed retval -110 
 [11244.049123] orinoco_usb: Cannot reset the device 
 [11244.049176] orinoco_usb: probe of 2-3:1.0 failed with error -14 
 [11250.889127] orinoco_usb: EZUSB_REQUEST_TRIGER failed retval -110 
 [11250.889140] orinoco_usb: Cannot reset the device 
 [11250.889193] orinoco_usb: probe of 2-3:1.0 failed with error -14 
 
```

---

### Post by chili555 on 2012-03-05
Wow! That's wierd. I've never seen that but, as I've said, this is actually the very first time I've encountered this driver. Let's further rename the old firmware and see if it helps. If not, we move on to ndiswrapper.```
sudo mv /lib/firmware/orinoco_ezusb_fw.bak /lib/firmware/orin.old
```Reboot and do:```
dmesg > jrahman.txt
zip jrahman.zip jrahman.txt
```In your home directory, you will find a file called jrahman.zip. Please attach it to your reply using the paperclip tool at the top of the reply box.

---

### Post by jrahman on 2012-03-05
The dmesg returns is attached in the .zip file.
Thanks again for your time and patience.

...Moments later, found that the **[COLOR="Blue"]*Orinoco*[/COLOR]** information are missing from the "***[COLOR="blue"]dmesg[/COLOR]***" (in the .zip file). However, later found the ***[COLOR="blue"]Orinoco[/COLOR]*** related message is being populated as appended below:

```
jrahman@CompaqUbuntu:~/Desktop$ dmesg | grep orinoco
[  623.159068] orinoco 0.15 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[  623.176967] orinoco_usb 0.15 (Manuel Estrada Sainz)
[  624.321105] orinoco_usb: EZUSB_REQUEST_TRIGER failed retval -110
[  624.321117] orinoco_usb: Cannot reset the device
[  624.321167] orinoco_usb: probe of 2-3:1.0 failed with error -14
[  624.323601] usbcore: registered new interface driver orinoco_usb
```

---

### Post by chili555 on 2012-03-06
> ...Moments later, found that the Orinoco information are missing from the "dmesg" (in the .zip file). However, later found the Orinoco related message is being populated as appended below:I don't really understand this. There is no sign of your device *at all* in the file you sent. 

I am starting to suspect that the native driver is not going to work in my lifetime. I will prepare instructions for ndiswrapper. Do you have the original XP wireless driver files, by chance? ndiswrapper is always a bit riskier when we grab the files off the internet.

---

### Post by chili555 on 2012-03-06
First, please verify that ndiswrapper is installed by default. Please open a terminal and run:```
sudo dpkg -s ndiswrapper-common
```

We hope we see:> Package: ndiswrapper-common
Status: install ok installed
Next, download the attached file to your desktop. Right-click it and select Extract Here. Now back in the terminal, do:```
cd Desktop/USB
sudo su
ndiswrapper -i WLAGS51B.INF
modprobe ndiswrapper
echo ndiswrapper >> /etc/modules
echo "blacklist orinoco_usb" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and let us have your report.

Of course, if you have OEM driver files, adjust as needed.

---

### Post by jrahman on 2012-03-06
> I don't really understand this. There is no sign of your device at all in the file you sent. 

Sorry for making confusion. What I wanted to mean, when I captured "dmesg" returns, I didn't see any "orinoco" information inside the return (which I zipped and attached). But later, after I had zipped the message, I ran another "dmesg" with "grep" pipe for "orinoco", where I got some information about "orinoco".

Thanks.

---

### Post by jrahman on 2012-03-06
> First, please verify that ndiswrapper is installed by default. Please open a terminal and run:

Unfortunately, ndiswrapper was not installed :-(
I just installed....
```
jrahman@CompaqUbuntu:~$ sudo dpkg -s ndiswrapper-common
Package: ndiswrapper-common
Status: install ok installed
Priority: optional
Section: misc
Installed-Size: 96
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Source: ndiswrapper
Version: 1.56+r2729-1
Replaces: ndiswrapper-utils
Suggests: ndiswrapper-source
Description: Common scripts required to use the utilities for ndiswrapper
 Some vendors do not release specifications of the hardware or provide a
 Linux driver for their wireless network cards. This project implements
 Windows kernel API and NDIS (Network Driver Interface Specification) API
 within Linux kernel. A Windows driver for wireless network card is then
 linked to this implementation so that the driver runs natively, as though
 it is in Windows, without binary emulation.
 .
 This package contains wrapper scripts to call out to the proper
 versions of whatever -utils-X.X package is installed.
Original-Maintainer: Julian Andres Klode <jak@debian.org>
Homepage: http://ndiswrapper.sourceforge.net/
```

Later, when I ran your suggested command, I get error as below :-(
```
root@CompaqUbuntu:/home/jrahman/Desktop/USB# ndiswrapper -i WLAGS51B.INF
Error: [COLOR="Red"]**unable to find a version of ndiswrapper!**[/COLOR]

```

---

### Post by chili555 on 2012-03-07
> What I wanted to mean, when I captured "dmesg" returns, I didn't see any "orinoco" information inside the returnIt is often useful to see the USB bus get recognized or not, see ACPI errors or warnings, etc. I hope you would never redact the results of a requested diagnostic unless, of course, if there was personally identifiable information.

I don't think you installed enough. Please also install ndiswrapper-utils. Then try again.

---

### Post by jrahman on 2012-03-07
> It is often useful to see the USB bus get recognized or not, see ACPI errors or warnings, etc. I hope you would never redact the results of a requested diagnostic unless, of course, if there was personally identifiable information.

I don't think you installed enough. Please also install ndiswrapper-utils. Then try again

I really appreciate your patience and effort to resolve this issue. One thing could assure you that I never edited any of the diagnostic message content.

Anyway, I failed to install **[COLOR="Blue"]ndiswrapper-utils[/COLOR]**, the error is as below:
```
jrahman@CompaqUbuntu:~$ sudo apt-get install ndiswrapper-utils
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Package ndiswrapper-utils is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However, the following packages replace it:
  ndiswrapper-common

E: Package 'ndiswrapper-utils' has no installation candidate
```

---

### Post by chili555 on 2012-03-07
Do you have your Ubuntu install disk? On my disc, I browsed to pool > main > n > ndiswrapper and the .deb files you need are there. Please see attached. I suggest you copy both to your desktop and then, in a terminal, do:```
sudo dpkg -i Desktop/ndis*.deb
```Then proceed as previously.

If that doesn't work, you might try:```
sudo apt-get remove --purge ndiswrapper-common
sudo apt-get install ndisgtk
```ndisgtk will install everything needed in the correct, matching versions.

---

### Post by jrahman on 2012-03-08
> **chili555 said:**
> Do you have your Ubuntu install disk? On my disc, I browsed to pool > main > n > ndiswrapper and the .deb files you need are there. Please see attached. I suggest you copy both to your desktop and then, in a terminal, do:```
sudo dpkg -i Desktop/ndis*.deb
```Then proceed as previously.

If that doesn't work, you might try:```
sudo apt-get remove --purge ndiswrapper-common
sudo apt-get install ndisgtk
```ndisgtk will install everything needed in the correct, matching versions.

Following your instructions as above, I finished installing ndiswrapper package from Ubuntu install CD and restarted the laptop without ejecting the CD from the drive, [COLOR=Red]**it was a mistake **[/COLOR]:-(. As the laptop's first boot order is set to the CD drive, the install CD started and opened the first window where I had to select and click the Install Ubuntu button....

**My steps, results and comments:**

[LIST=1]
[*]Without choosing any install option, ejected the CD and did power cycle the laptop to restart. Now I found a new problem, it doesn't boot up Ubuntu, but Windows XP was OK
[*]Then decided to reinstall Ubuntu and start everything from scratch
[*]Using install CD, I chose "[COLOR=Blue]**Upgrade Ubuntu 11.10 to Ubuntu 11.10**[/COLOR]", NOT a fresh install by removing all previously installed packages and software
[*]After upgrade install, Ubuntu started properly and found all my previous documents and other software were existed
[*]I followed again your steps for installing ndiswrapper and everything were installed without any error
[*]Restarted the laptop, Ubuntu started
[*]After Ubuntu started, when I toggle the Fn2 key to activate wireless, I could see the green LED of the Multiport module turns on [COLOR=Red]**but moments later Ubuntu crashes**[/COLOR] to a black screen dumping lots of error message
[*]If I restart the laptop (keeping the same state of the wireless as activated) Ubuntu doesn't start and halts with a blank (purple) screen, at that state, if I toggle Fn2 switch to deactivate wireless and restart the laptop, Ubuntu starts fine
[*]Again, after Ubuntu started toggling Fn2 key to wireless activated crashes Ubuntu
[*]After reproducing the crash, I'll post the system logs tonight (**[COLOR=Blue]I believe, it is somewhere under /var/logs ?)[/COLOR]**
[/LIST]

---

### Post by chili555 on 2012-03-08
Did you blacklist the native driver as I suggested above?> cd Desktop/USB
sudo su
ndiswrapper -i WLAGS51B.INF
modprobe ndiswrapper
echo ndiswrapper >> /etc/modules
[COLOR="Red"]echo "blacklist orinoco_usb" >> /etc/modprobe.d/blacklist.conf[/COLOR]
exitThe log will be in /var/log/syslog. You can do:```
sudo tail -n5 /var/log/syslog > syslog.txt
```Note the timestamp in syslog.txt. Now press the Fn+F2 key and let it lock up. After a reboot, check the log again:```
sudo less /var/log/syslog
```The arrow keys will allow you to scroll back and forth to see what happens after the timestamp you noted. If needed, you can copy and paste from the terminal to a text document and post it here so we can analyze it. Get out of 'less' with Ctrl+c.

Here is a sample from my computer showing the timestamp:> Mar  8 [COLOR="Red"]11:32:09[/COLOR] LAPTOP60 wpa_supplicant[11169]: CTRL-EVENT-CONNECTED - Connection to 99:13:10:62:88:77 completed (reauth) [id=0 id_str=]So, if I were looking for an issue, I'd start at the first entries after 11:32:09.

---

### Post by jrahman on 2012-03-08
> **chili555 said:**
> Did you blacklist the native driver as I suggested above?

Yes I did.

However, **[COLOR=Blue]lsusb[/COLOR]** doesn't show anymore "[COLOR=Blue]**Compaq Multiport**[/COLOR]", which I believe caused due to blacklist of native driver.
```
jrahman@compaqubuntu:~/Desktop$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 001 Device 003: ID 0409:0058 NEC Corp. HighSpeed Hub
Bus 001 Device 004: ID 04b3:310b IBM Corp. Red Wheel Mouse

```Anyway, [COLOR=Blue]**syslog**[/COLOR] is attached as zipped file.
Notes:
1. I toggled the Fn2 switch to activate wireless (cable was already disconnected) at around 22:38 PM
2. Moment later Ubuntu was crashed\
3. Right after the crash I power cycled the laptop to start the Ubuntu
4. You could see that syslog has some information missing between [COLOR=Blue]**Mar  8 22:31:52**[/COLOR] and **[COLOR=Blue]Mar  8 22:40:55[/COLOR]**.
```

Mar  8 22:31:52 compaqubuntu dbus[457]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
**[COLOR=Red]<<sometime here the wireless was attempted to be activated>>[/COLOR]**
Mar  8 22:40:55 compaqubuntu kernel: imklog 5.8.1, log source = /proc/kmsg started.
```

---

### Post by jrahman on 2012-03-16
Its March break here in Ontario (and many part of North America), expectedly, many people are on holidays with family. Believe, some wireless guru will come up with some comments on my problem soon.

Have a nice weekend :D

---

