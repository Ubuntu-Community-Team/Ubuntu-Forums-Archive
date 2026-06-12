---
title: "railink rt2870 won't connect in 11.04"
date: 2011-06-28
forum: Networking &amp; Wireless
---

### Post by alliance1975 on 2011-06-28
I have a Sparklan WUBR-502GN USB dongle with the RT2870 chip. It has worked, (with a little effort) of previous installs of 9.04, 9.10, 10.04 and 10.10. However it refuses to work in 11.04. I followed the same procedures, (blacklisting, confirming device ID, modifying config.mk and rt_linux.h, sudo make & make install and removing staging/rt2870), outlined in past forum articles and that worked in the previous RCs, but the connection to my home network will not complete. Has something changed in 11.04 that is substantially different from past releases?

P.S. the only thing I haven’t done, since 11.04 was only installed moments before, is do the build essential and headers.

If someone could direct me to recent postings that include info on rt2870 under 11.04 I would be grateful.

---

### Post by ratcheer on 2011-06-28
11.04 may have loaded the wrong driver. Please post the output of "sudo lspci -v".

Tim

---

### Post by alliance1975 on 2011-06-28
Tim,

It will be several hours before I can reply. I will get the answer. You asked for lspci. I will also get lsusb as well.

---

### Post by alliance1975 on 2011-06-28
Per your request: Note no attempt to install railink drivers or other changes made.
```
chris@hpdv5k:~$ sudo lspci -v #rt2870 unplugged
[sudo] password for chris: 

06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
	Subsystem: Hewlett-Packard Company Broadcom 802.11b/g WLAN
	Flags: bus master, fast devsel, latency 64, IRQ 21
	Memory at c0200000 (32-bit, non-prefetchable) [size=8K]
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb

06:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Hewlett-Packard Company Device 30a4
	Flags: bus master, medium devsel, latency 128, IRQ 22
	I/O ports at a000 [size=256]
	Memory at c0202000 (32-bit, non-prefetchable) [size=256]
	Capabilities: [50] Power Management version 2
	Kernel driver in use: 8139too
	Kernel modules: 8139too, 8139cp

```

a repeat of lspci with the rt2870 plugged in yielded no change.

```
chris@hpdv5k:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID 148f:2770 Ralink Technology, Corp. RT2770 Wireless Adapter
Bus 001 Device 007: ID 13fd:1040 Initio Corporation 
Bus 001 Device 006: ID 046d:c03d Logitech, Inc. M-BT96a Pilot Optical Mouse
Bus 001 Device 004: ID 0a81:0101 Chesen Electronics Corp. Keyboard
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

iwconfig

```
chris@hpdv5k:~$ sudo iwconfig
[sudo] password for chris: 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
wlan1     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on

```

---

### Post by alliance1975 on 2011-06-28
Additional info. rt list w/o rt2870 plugged in.

```
chris@hpdv5k:~$ lsmod |grep rt
rt2870sta             450556  0 
rt2800usb              18235  0 
rt2800lib              45181  1 rt2800usb
crc_ccitt              12667  2 rt2870sta,rt2800lib
rt2x00usb              20330  1 rt2800usb
rt2x00lib              49235  3 rt2800usb,rt2800lib,rt2x00usb
parport_pc             36959  0 
mac80211              294370  4 rt2800lib,rt2x00usb,rt2x00lib,b43
cfg80211              178528  3 rt2x00lib,b43,mac80211
parport                46458  3 parport_pc,ppdev,lp

```

a simple plug in of the rt2870 usb dongle and an attempt to connect failed. wpa password entered correctly.

---

### Post by alliance1975 on 2011-06-28
Additional info:

```
chris@hpdv5k:~$ sudo iwlist ra0 scan
ra0       Scan completed :
          Cell 01 - Address: 00:26:5A:D1:7F:1E
                    Protocol:802.11g/n
                    ESSID:"DUDEKS"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:70/100  Signal level:-62 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:1C:DF:AB:5C:71
                    Protocol:802.11b/g/n
                    ESSID:"DUDEKS"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:100/100  Signal level:-37 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0E0050F204104A0001101044000102

```

---

### Post by chili555 on 2011-06-28
Dr. Chili extracts a gleaming scalpel from the autoclave and behind his mask says, please do:
```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add four lines:
```
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00pci
blacklist rt2x00lib
```
Proofread carefully, save and close gedit. Reboot and tell us how beautifully your wireless is now working.

---

### Post by alliance1975 on 2011-06-28
Thank you Chili, you have helped me in the past and it looks like I need you again.

Per your request rt2800pci and rt2x00pci added to blacklist but still the vapor swirls with no connection.

```
# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist rt2800usb
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00pci
blacklist rt2x00lib
```

---

### Post by chili555 on 2011-06-28
> Cell 02 - Address: 00:1C:DF:AB:5C:71
                    Protocol:802.11b/g/n
                    ESSID:"DUDEKS"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:100/100  Signal level:-37 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:300 Mb/s
                    IE: [COLOR="Red"]WPA Version 1[/COLOR]
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/[COLOR="Red"]WPA2 Version 1[/COLOR]
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD0E0050F204104A0001101044000102Sometimes, there is better luck connecting if the router is set to WPA2 only and not WPA and WPA2 mixed mode. Can you please reset the router to WPA2 only?

---

### Post by alliance1975 on 2011-06-28
Revised the router security to WPA2 only but still no response.

Should I do a reboot?

Did a reboot any way, no luck.

---

