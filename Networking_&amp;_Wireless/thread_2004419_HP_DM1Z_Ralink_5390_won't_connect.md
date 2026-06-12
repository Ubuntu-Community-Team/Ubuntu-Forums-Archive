---
title: "HP DM1Z Ralink 5390 won't connect"
date: 2012-06-15
forum: Networking &amp; Wireless
---

### Post by astanasto on 2012-06-15
I have an HP DM1Z (AMD E-350 APU) with an Ralink 5390 adapter.  I'm running 12.04 64-bit.

With the drivers in the kernel (the rt2800pci module) I was having issues with connection stability.  There are some wireless networks that it won't connect to at all and others that it seems to work ok with.  My home network is a no-go.

I blacklisted the rt2800 module in /etc/modprobe.d/blacklist.conf

```

#blacklist the kernel rt2800 driver so I can explicitly load the rt5390 from ralink
blacklist rt2800pci

```and installed 2011_0406_RT5390_RT5392_Linux_STA_V2.5.0 from Ralink's site.

config.mk:
```

HAS_WPA_SUPPLICANT=y
HAS_NATIVE_WPA_SUPPLICANT=y

```To build & install:
```

sudo su
make
make install
modprobe rt5390sta
exit
```Same symptoms.  I then tried changing wireless mode from 9 to 5 to 3 w/o any luck.

```

sudo mkdir /etc/Wireless/RT53590STA/
sudo cp /etc/Wireless/RT2860STA/RT2860STA.dat /etc/Wireless/RT5390STA/RT5390STA.dat

```I then edited RT5390STA.dat and changed WirelessMode from 9 to 5 to 3, unloading and reloading the RT5390 module and retesting.

I'm at a loss.  Here is some debug output.  Keep in mind that I have a USB Rosewill RNX-N180 adapter that I'm using in the meantime so don't let that confuse you.

```

$ lspci | grep -i "network"
02:00.0 Network controller: Ralink corp. RT5390 [802.11 b/g/n 1T1R G-band PCI Express Single Chip]

``````

$ lsusb | grep -i "wlan"
Bus 001 Device 002: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter

```ifconfig shows the USB wlan adapter as wlan1 but the ralink is ra0 for some reason.  I know it was wlan0 at some point in the past.
```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 2c:27:d7:bc:ee:2a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:40 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1268 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1268 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:227419 (227.4 KB)  TX bytes:227419 (227.4 KB)

ra0       Link encap:Ethernet  HWaddr c0:f8:da:59:c6:6d  
          inet6 addr: fe80::c2f8:daff:fe59:c66d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:42836 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12524 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7669982 (7.6 MB)  TX bytes:183730 (183.7 KB)
          Interrupt:17 

wlan1     Link encap:Ethernet  HWaddr 00:1a:ef:1d:a3:e8  
          inet addr:192.168.1.113  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:efff:fe1d:a3e8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:36388 errors:0 dropped:2295 overruns:0 frame:0
          TX packets:28816 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22134521 (22.1 MB)  TX bytes:6836760 (6.8 MB)

``````

$ iwconfig
lo        no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:"myhomenet"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 58:6D:8F:71:92:82   
          Bit Rate:72 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=97/100  Signal level=100/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ra0       Ralink STA  ESSID:""  Nickname:"RT2860STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-45 dBm  Noise level:-45 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

``````

$ lsmod | grep -i "5390"
rt5390sta            1349530  1 

```The rt2800 module doesn't seem to be loaded.

```

$ dmesg | grep -i "5390"

[ 2829.280537] /home/astanasto/Downloads/2011_0406_RT5390_RT5392_Linux_STA_V2.5.0.3_DPO/os/linux/../../common/cmm_asic.c:3040 assert KeyIdx < 4failed

```That error repeats often.

```

$ iwlist scan

wlan1     Scan completed :
          Cell 01 - Address: 58:6D:8F:71:92:82
                    ESSID:"myhomenet"
                    Protocol:IEEE 802.11bgn
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:wpa_ie=dd1c0050f20101000050f20202000050f2040050f20201000050f2020c00
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020c00
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD270050F204104A0001101044000102104700108F342FFBB1EBB5C5B79BBB571A93C383103C000103
                    Signal level=100/100  

ra0       Scan completed :
          Cell 06 - Address: 58:6D:8F:71:92:82
                    Protocol:802.11b/g/n
                    ESSID:"myhomenet"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality=100/100  Signal level=-49 dBm  Noise level=-92 dBm
                    Encryption key:on
                    Bit Rates:144 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD270050F204104A0001101044000102104700108F342FFBB1EBB5C5B79BBB571A93C383103C000103

``````

$ lsb_release -d
Description:    Ubuntu 12.04 LTS

``````
$ uname -mr
3.2.0-24-generic x86_64

``````

$ sudo /etc/init.d/networking restart

 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                               Ignoring unknown interface wlan0=wlan0.
                                                                              [ OK ]

```

---

### Post by astanasto on 2012-06-15
I just disabled the rt5390 driver and switched back to the rt2800.  I am seeing the exact same behavior as before (constant cycling attempts to connect).

Blacklist rt5390 and un-blacklist rt2800 in /etc/modprobe.d/blacklist.conf:
```

#blacklist the kernel rt2800 driver so I can explicitly load the rt5390 from ra$
#blacklist rt2800pci

#blacklist the rt5390 driver so I can load the kernel's rt2800 driver instead
blacklist rt5390sta
```

```

$  lspci | grep -i "network"
02:00.0 Network controller: Ralink corp. RT5390 [802.11 b/g/n 1T1R G-band PCI Express Single Chip]

```

```

$ lsusb | grep -i "wlan"
Bus 001 Device 002: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter

```

Now the ralink is interface wlan0 again, rather than ra0.

```

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 2c:27:d7:bc:ee:2a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:40 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:469 errors:0 dropped:0 overruns:0 frame:0
          TX packets:469 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:66933 (66.9 KB)  TX bytes:66933 (66.9 KB)

wlan0     Link encap:Ethernet  HWaddr c0:f8:da:59:c6:6d  
          inet6 addr: fe80::c2f8:daff:fe59:c66d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:143 errors:0 dropped:0 overruns:0 frame:0
          TX packets:428 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24989 (24.9 KB)  TX bytes:100732 (100.7 KB)

wlan1     Link encap:Ethernet  HWaddr 00:1a:ef:1d:a3:e8  
          inet addr:192.168.1.113  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:efff:fe1d:a3e8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2542 errors:0 dropped:234 overruns:0 frame:0
          TX packets:1602 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1489823 (1.4 MB)  TX bytes:335718 (335.7 KB)

```

```

$ iwconfig
lo        no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:"myhomenet"  Nickname:"rtl_wifi"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 58:6D:8F:71:92:82   
          Bit Rate:72 Mb/s   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=100/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan0     IEEE 802.11bgn  ESSID:"myhomenet"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 58:6D:8F:71:92:82   
          Bit Rate=58.5 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=69/70  Signal level=-41 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:13   Missed beacon:0

eth0      no wireless extensions.

```

```

$ lsmod | grep -i "5390"
$ lsmod | grep -i "2800"
rt2800pci              18715  0 
rt2800lib              58925  1 rt2800pci
crc_ccitt              12667  1 rt2800lib
rt2x00pci              14577  1 rt2800pci
rt2x00lib              55301  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              506816  3 rt2800lib,rt2x00pci,rt2x00lib
eeprom_93cx6           12725  1 rt2800pci

```

```

$ dmesg | grep -i "2800"
[   23.938412] rt2800pci 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   23.938457] rt2800pci 0000:02:00.0: setting latency timer to 64
[   24.114865] Registered led device: rt2800pci-phy0::radio
[   24.114911] Registered led device: rt2800pci-phy0::assoc
[   24.114948] Registered led device: rt2800pci-phy0::quality
[   26.321286] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware

```

```

$ sudo /etc/init.d/networking restart
 * Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                          Ignoring unknown interface wlan0=wlan0.
                                                                         [ OK ]

```

---

### Post by astanasto on 2012-06-15
I noticed that the working USB Rosewill/Realtek adapter has powermanagement disabled while the onboard Ralink 5390 has it enabled.

```

$ sudo iwconfig wlan0 power off
$ iwconfig
lo        no wireless extensions.

wlan1     unassociated  Nickname:"rtl_wifi"
          Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

No change in symptoms.

I also noticed that if I timed running iwconfig as the connection attempted over and over I could see it associate to my network.

```

$ iwconfig

lo        no wireless extensions.

wlan1     unassociated  Nickname:"rtl_wifi"
          Mode:Managed  Access Point: Not-Associated   Sensitivity:0/0  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan0     IEEE 802.11bgn  ESSID:"myhomenet"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 58:6D:8F:71:92:82   
          Bit Rate=65 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-39 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:5   Missed beacon:0

eth0      no wireless extensions.

```

---

### Post by astanasto on 2012-06-17
It happens to be working right now.  Odd.

```

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 2c:27:d7:bc:ee:2a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:40 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:296 errors:0 dropped:0 overruns:0 frame:0
          TX packets:296 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:48192 (48.1 KB)  TX bytes:48192 (48.1 KB)

wlan0     Link encap:Ethernet  HWaddr c0:f8:da:59:c6:6d  
          inet addr:192.168.1.41  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::c2f8:daff:fe59:c66d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7267 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7383 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2941305 (2.9 MB)  TX bytes:1722516 (1.7 MB)
```

```

$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"myhomenet"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 58:6D:8F:71:92:82   
          Bit Rate=65 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=69/70  Signal level=-41 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:101  Invalid misc:61   Missed beacon:0

eth0      no wireless extensions.

```

```

$ lsmod | grep -i "5390"

$ lsmod | grep -i "2800"
rt2800pci              18715  0 
rt2800lib              58925  1 rt2800pci
crc_ccitt              12667  1 rt2800lib
rt2x00pci              14577  1 rt2800pci
rt2x00lib              55301  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              506816  3 rt2800lib,rt2x00pci,rt2x00lib
eeprom_93cx6           12725  1 rt2800pci

```

```
$ dmesg | grep -i "2800"
[   26.336194] rt2800pci 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   26.336239] rt2800pci 0000:02:00.0: setting latency timer to 64
[   26.437946] Registered led device: rt2800pci-phy0::radio
[   26.438027] Registered led device: rt2800pci-phy0::assoc
[   26.438386] Registered led device: rt2800pci-phy0::quality
[   28.810047] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware

```

---

### Post by astanasto on 2012-06-17
that was short-lived.  one reboot and the ra5390 is back on the fritz.

---

### Post by astanasto on 2012-06-19
I've given up.  I think my solution to this problem is to roll back to Win7 and run Ubuntu in VirtualBox.  

That way I've got wireless stability and I can still run my Bash/ImageMagick scripts w/o modification.

HP can go suck an egg for whitelisting / signing the BIOS such that swapping the wireless card is not feasible.  what a crappy anti-consumer thing to do.

---

### Post by lfehr on 2012-11-01
This is in german but it worked for me:

[http://forum.ubuntuusers.de/topic/ralink-rt-3391/#post-3473742](http://forum.ubuntuusers.de/topic/ralink-rt-3391/#post-3473742)

Hope it helps and it's not too late. :)

---

