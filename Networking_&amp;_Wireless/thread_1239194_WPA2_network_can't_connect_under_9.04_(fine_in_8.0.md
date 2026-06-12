---
title: "WPA2 network can't connect under 9.04 (fine in 8.04) using any method"
date: 2009-08-13
forum: Networking &amp; Wireless
---

### Post by and.hunt on 2009-08-13
I'm having problems connecting to my WPA2 protected router since I upgraded my laptop from Ubuntu 8.04 to Ubuntu 9.04 yesterday. When using the nm-applet method, the connection in progress icon appears for a while, and then every so often I keep getting asked to confirm the key to access the network. Using wpa_supplicant and wicd has also failed. At one point today the network suddenly connected, only to fail on a renewed boot. Unprotected networks work fine. I have seen similar problems around on the forums, but none of the fixes actually does anything. I suspect this is something to do with the underlying driver, as the wpa_supplicant.log does show some driver issues:
```

CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
Trying to associate with 00:21:29:68:0c:27 (SSID='HHWireless' freq=2462 MHz)
Association request to the driver failed
Associated with 00:21:29:68:0c:27
WPA: Failed to set PTK to the driver.
WPA: Failed to set GTK to the driver.
RSN: Failed to configure GTK
CTRL-EVENT-SCAN-RESULTS
Authentication with 00:21:29:68:0c:27 timed out.
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-SCAN-RESULTS
Trying to associate with 00:21:29:68:0c:27 (SSID='HHWireless' freq=2462 MHz)
Association request to the driver failed
Associated with 00:21:29:68:0c:27
WPA: Failed to set PTK to the driver.
WPA: Failed to set GTK to the driver.
RSN: Failed to configure GTK
CTRL-EVENT-SCAN-RESULTS
Authentication with 00:21:29:68:0c:27 timed out.
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-SCAN-RESULTS
Trying to associate with 00:21:29:68:0c:27 (SSID='HHWireless' freq=2462 MHz)
Association request to the driver failed
Associated with 00:21:29:68:0c:27
WPA: Failed to set PTK to the driver.
WPA: Failed to set GTK to the driver.
RSN: Failed to configure GTK
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-SCAN-RESULTS
Trying to associate with 00:21:29:68:0c:27 (SSID='HHWireless' freq=2462 MHz)
Association request to the driver failed
Associated with 00:21:29:68:0c:27
WPA: Failed to set PTK to the driver.
WPA: Failed to set GTK to the driver.
RSN: Failed to configure GTK
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
Authentication with 00:21:29:68:0c:27 timed out.
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-SCAN-RESULTS
Trying to associate with 00:21:29:68:0c:27 (SSID='HHWireless' freq=2462 MHz)
Association request to the driver failed
Associated with 00:21:29:68:0c:27
WPA: Failed to set PTK to the driver.
WPA: Failed to set GTK to the driver.
RSN: Failed to configure GTK
CTRL-EVENT-SCAN-RESULTS
Authentication with 00:21:29:68:0c:27 timed out.
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-SCAN-RESULTS
Trying to associate with 00:21:29:68:0c:27 (SSID='HHWireless' freq=2462 MHz)
Association request to the driver failed
Associated with 00:21:29:68:0c:27
WPA: Failed to set PTK to the driver.
WPA: Failed to set GTK to the driver.
RSN: Failed to configure GTK
root@andrew-laptop2-ubuntu:/var/log# more wpa_supplicant.log
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
Trying to associate with 00:21:29:68:0c:27 (SSID='HHWireless' freq=2462 MHz)
Association request to the driver failed
Associated with 00:21:29:68:0c:27
WPA: Failed to set PTK to the driver.
WPA: Failed to set GTK to the driver.
RSN: Failed to configure GTK
CTRL-EVENT-SCAN-RESULTS
Authentication with 00:21:29:68:0c:27 timed out.
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-SCAN-RESULTS
Trying to associate with 00:21:29:68:0c:27 (SSID='HHWireless' freq=2462 MHz)
Association request to the driver failed
Associated with 00:21:29:68:0c:27
WPA: Failed to set PTK to the driver.
WPA: Failed to set GTK to the driver.
RSN: Failed to configure GTK
CTRL-EVENT-SCAN-RESULTS
Authentication with 00:21:29:68:0c:27 timed out.
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-SCAN-RESULTS
Trying to associate with 00:21:29:68:0c:27 (SSID='HHWireless' freq=2462 MHz)
Association request to the driver failed
Associated with 00:21:29:68:0c:27
WPA: Failed to set PTK to the driver.
WPA: Failed to set GTK to the driver.
RSN: Failed to configure GTK
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-SCAN-RESULTS
Trying to associate with 00:21:29:68:0c:27 (SSID='HHWireless' freq=2462 MHz)
Association request to the driver failed
Associated with 00:21:29:68:0c:27
WPA: Failed to set PTK to the driver.
WPA: Failed to set GTK to the driver.
RSN: Failed to configure GTK
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
Authentication with 00:21:29:68:0c:27 timed out.
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-SCAN-RESULTS
Trying to associate with 00:21:29:68:0c:27 (SSID='HHWireless' freq=2462 MHz)
Association request to the driver failed
Associated with 00:21:29:68:0c:27
WPA: Failed to set PTK to the driver.
WPA: Failed to set GTK to the driver.
RSN: Failed to configure GTK
CTRL-EVENT-SCAN-RESULTS
Authentication with 00:21:29:68:0c:27 timed out.
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-SCAN-RESULTS
Trying to associate with 00:21:29:68:0c:27 (SSID='HHWireless' freq=2462 MHz)
Association request to the driver failed
Associated with 00:21:29:68:0c:27
WPA: Failed to set PTK to the driver.
WPA: Failed to set GTK to the driver.
RSN: Failed to configure GTK
CTRL-EVENT-SCAN-RESULTS
Authentication with 00:21:29:68:0c:27 timed out.
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-SCAN-RESULTS
Trying to associate with 00:21:29:68:0c:27 (SSID='HHWireless' freq=2462 MHz)
Association request to the driver failed
Associated with 00:21:29:68:0c:27
WPA: Failed to set PTK to the driver.
WPA: Failed to set GTK to the driver.
RSN: Failed to configure GTK
CTRL-EVENT-SCAN-RESULTS
Authentication with 00:21:29:68:0c:27 timed out.
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-SCAN-RESULTS
Trying to associate with 00:21:29:68:0c:27 (SSID='HHWireless' freq=2462 MHz)
Association request to the driver failed
Associated with 00:21:29:68:0c:27
WPA: Failed to set PTK to the driver.
WPA: Failed to set GTK to the driver.
RSN: Failed to configure GTK
CTRL-EVENT-SCAN-RESULTS
Authentication with 00:21:29:68:0c:27 timed out.
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-SCAN-RESULTS
Trying to associate with 00:21:29:68:0c:27 (SSID='HHWireless' freq=2462 MHz)
Association request to the driver failed
Associated with 00:21:29:68:0c:27
WPA: Failed to set PTK to the driver.
WPA: Failed to set GTK to the driver.
RSN: Failed to configure GTK
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
Authentication with 00:00:00:00:00:00 timed out.
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS

```

Edit: I forgot to add that usually the network is hidden, unhiding it didn't help though.

---

### Post by and.hunt on 2009-08-13
Here is the standard info:
1)
Laptop: Toshiba Portege R100
2)
```
02:0a.0 Network controller [0280]: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter [8086:1043] (rev 04)
```
3)
ifconfig: (eth1 is the wireless card - I just noticed it says Ethernet though?)
```
eth0      Link encap:Ethernet  HWaddr 00:08:0d:9b:aa:14
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr 00:04:23:64:fa:88
          inet6 addr: fe80::204:23ff:fe64:fa88/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:6 dropped:5 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1530 (1.5 KB)  TX bytes:1612 (1.6 KB)
          Interrupt:11 Base address:0x6000 Memory:dfdfe000-dfdfefff

eth3      Link encap:Ethernet  HWaddr 00:50:04:fe:9d:ef
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:4ff:fefe:9def/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1023 errors:0 dropped:0 overruns:0 frame:0
          TX packets:815 errors:0 dropped:0 overruns:0 carrier:4
          collisions:0 txqueuelen:1000
          RX bytes:982815 (982.8 KB)  TX bytes:131537 (131.5 KB)
          Interrupt:3 Base address:0x300

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1204 (1.2 KB)  TX bytes:1204 (1.2 KB)

```
iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:16 dBm
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth3      no wireless extensions.

```
lsmod | grep "ipw2100"
```

ipw2100                73264  0
lbm_cw_ieee80211       35016  1 ipw2100
lbm_cw_cfg80211        36448  1 ipw2100

```

5)
dmesg | grep "ipw2100"
```

[   44.375474] ipw2100: Intel(R) PRO/Wireless 2100 Network Driver, git-1.2.2
[   44.375480] ipw2100: Copyright(c) 2003-2006 Intel Corporation
[   44.378679] ipw2100: Detected Intel PRO/Wireless 2100 Network Connection

```
6)
lshw -C network
```

  *-network:0
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 83
       serial: 00:08:0d:9b:aa:14
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  *-network:1
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: a
       bus info: pci@0000:02:0a.0
       logical name: eth1
       version: 04
       serial: 00:04:23:64:fa:88
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 latency=64 link=no maxlatency=34 mingnt=2 module=ipw2100 multicast=yes wireless=unassociated
  *-network
       description: Megahertz 574B
       product: B
       vendor: 3Com
       physical id: 0
       version: 001
       slot: Socket 0
       resources: irq:3
  *-network
       description: Ethernet interface
       physical id: 3
       logical name: eth3
       serial: 00:50:04:fe:9d:ef
       capabilities: ethernet physical
       configuration: broadcast=yes driver=3c574_cs ip=192.168.1.100 multicast=yes

```

7)
iwlist scan
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:0F:CC:A4:0A:A4
                    ESSID:"roman"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality:37  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 180ms ago
          Cell 02 - Address: 00:0F:CC:E0:9D:68
                    ESSID:"keinsystem"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.422 GHz (Channel 3)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality:42  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 148ms ago
          Cell 03 - Address: 00:21:29:68:0C:27
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 11 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:82  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 436ms ago
          Cell 04 - Address: 00:24:37:0D:E7:70
                    ESSID:"lgh-70440"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality:39  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 400ms ago
          Cell 05 - Address: 00:1C:F0:F7:9A:CD
                    ESSID:"dlink"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:25  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 6820ms ago
          Cell 06 - Address: 00:0F:CC:FC:6D:1C
                    ESSID:"bruno_nych"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality:25  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 1188ms ago
          Cell 07 - Address: 00:02:CF:EB:41:78
                    ESSID:"BOLLHALDER"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 11 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:23  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 1872ms ago
          Cell 08 - Address: 00:0F:CC:DE:FA:84
                    ESSID:"6757 2510"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 22 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Quality:20  Signal level:0  Noise level:0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 80ms ago

eth3      Interface doesn't support scanning.

```

8)
lsb_release -d
```
Description:    Ubuntu 9.04

```

9)
uname -mr
```

2.6.24-23-generic i686

```
(I'm running on the 8.04 kernel to see whether this improves things, but there is no change.)

10)
/etc/init.d/networking restart
```

 * Reconfiguring network interfaces...                                                     [ OK ]
```

//Update: I'm testing Puppy Linux now on the same pc, and WPA works fine there.

---

### Post by jmexia on 2009-08-14
hi,

just to clear the air: i am a noob.  however, i would like to share my experience solving a similar issue as the one you described in your first post.  are you using both, wpa-tkip and wpa2-aes, on your network?  when i broadcast my ssid and enable both wpa and wpa2 on my wap/wireless-router, my dell mini 9 can connect just fine.  when i stop broadcasting my ssid and keep both wpa and wpa2 enabled, i encounter problems connecting (having to keep authenticating the passphrase/key etc.).  if i enable only wpa2 and keep ssid broadcast disabled, my mini 9 connects just fine again.  i don't have a technical explanation...just know it works for me.  i do notice that my other pc does take a little longer associating and connecting to the network now (it used to be almost instantaneous when wpa-tkip and wpa2-aes were both enabled).  it must like wpa better...

hope this helps...good luck!
j

---

### Post by and.hunt on 2009-08-15
I've already reverted back to Ubuntu 8.04 (where everything is fine), so I won't really be able to test on my laptop now. That said, I did try various settings with another wireless router, and I only could connect when there wasn't any encryption, (hiding the SSID didn't change anythig), but not to WPA networks. If I have time I'll put a second ubuntu (9.04) installation on a spare partition to test and see if I can solve the problem.
(OT: This could be a challenge as the spare partition is only 1.5Gb, but I can probably get a spare external USB HD, since only the kernel really needs to be on the main hd to be booted, since my laptop can't boot cd, usb or network.)
(OT2: Did no one do thorough testing of 9.04 before it was release, since so many people had problems with WPA?)

---

