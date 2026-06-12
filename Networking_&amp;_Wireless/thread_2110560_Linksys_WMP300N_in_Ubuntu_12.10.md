---
title: "Linksys WMP300N in Ubuntu 12.10"
date: 2013-01-30
forum: Networking &amp; Wireless
---

### Post by MVillumsen on 2013-01-30
Hi

I have been searching all over the internet for a while now and I'm unable to find a solution to my problem.

I recently installed Ubuntu 12.10 on my stationary computer with an old Linksys WMP300N V.2 wireless network adapter which doesn't seem to work. When ubuntu is installed I can see a list of all available wireless networks, but when I try to connect to my network (hosted by an Apple Airport Extreme) it tries to connect for a few minutes and then it asks for the password again. This is repeated till I cancel. I have the same problem when trying to connect to other wireless networks. 

After reading various forums I tried installing the original drivers via ndiswrapper, which gives me a "FATAL: module ndiswrapper not found." error. If I install the driver using the terminal I am not getting the error. After trying to install the driver with ndiswrapper (either in the GUI or in the terminal) I am unable to see any wireless networks and it seems that the adapter is "disabled".

Can anyone help me solve this problem?

Btw. the linksys WMP300N Works fine in windows 7 and I have never had any trouble with it before I installed ubuntu.

---

### Post by praseodym on 2013-01-30
Hi,

imho its an Atheros device. Uninstall ndiswrapper via:
```

sudo modprobe -rfv ndiswrapper
sudo apt-get remove --purge ndiswrapper* ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/*
sudo depmod -a
sudo update-initramfs -u
```
After that, deactivate the hardware encryption of the driver via:
```

echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
```
Reboot and check:
```

lspci -nnk
lsmod
iwconfig
```
BTW: I recommend pure WPA2-AES (CCMP) encryption, if possible.

---

### Post by MVillumsen on 2013-01-31
Thanks, although when I do that I am back where I started. It just tries to connect to the network for a few minutes and then it asks for password, which is repeated.. It never actually connects to the network. I am using WPA2 Personal encryption (can't remember if it is AEK or TKIP - pretty sure it is AEK though).

---

### Post by praseodym on 2013-01-31
check:
```

dmesg | egrep 'ndis|wlan0|ath9k'
sudo iwlist scan
iwconfig
```

---

### Post by MVillumsen on 2013-01-31
> **praseodym said:**
> check:
```

dmesg | egrep 'ndis|wlan0|ath9k'
sudo iwlist scan
iwconfig
```

Do you want me to copy-paste all the information it returns? Because it is quite a lot.. Or do is there anything specific I should look for?

---

### Post by praseodym on 2013-02-01
Errrr, YES, otherwise errors can not be found. ;-)

---

### Post by MVillumsen on 2013-02-01
True true :)

dmesg | egrep 'ndis|wlan0|ath9k':

```

[   12.397047] ieee80211 phy0: >Selected rate control algorithm 'ath9k_rate_control'
[   12.400675] Registered led device: ath9k-phy0
[   12.564949] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   12.566608] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.070420] wlan0: authenticate with 20:c9:d0:1d:b1:db
[   14.074230] wlan0: send auth to 20:c9:d0:1d:b1:db (try 1/3)
[   14.097699] wlan0: authenticated
[   14.100022] wlan0: associate with 20:c9:d0:1d:b1:db (try 1/3)
[   14.127210] wlan0: RX AssocResp from 20:c9:d0:1d:b1:db (capab=0x431 status=0 aid=1)
[   14.127299] wlan0: associated
[   14.127722] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   55.192524] wlan0: authenticate with 20:c9:d0:1d:b1:db
[   55.195777] wlan0: send auth to 20:c9:d0:1d:b1:db (try 1/3)
[   55.220874] wlan0: authenticated
[   55.224032] wlan0: associate with 20:c9:d0:1d:b1:db (try 1/3)
[   55.250399] wlan0: RX AssocResp from 20:c9:d0:1d:b1:db (capab=0x431 status=0 aid=1)
[   55.250482] wlan0: associated
[   94.244661] wlan0: authenticate with 20:c9:d0:1d:b1:db
[   94.248313] wlan0: send auth to 20:c9:d0:1d:b1:db (try 1/3)
[   94.272023] wlan0: authenticated
[   94.276053] wlan0: associate with 20:c9:d0:1d:b1:db (try 1/3)
[   94.301158] wlan0: RX AssocResp from 20:c9:d0:1d:b1:db (capab=0x431 status=0 aid=1)
[   94.301243] wlan0: associated

```sudo iwlist scan:

```

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 20:C9:D0:1D:B1:DB
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"Villumsen"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000076e5b048aa
                    Extra: Last beacon: 0ms ago
                    IE: Unknown: 000956696C6C756D73656E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030102
                    IE: Unknown: 0706444B20010D1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AAD511BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 3D1602000400000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0700039301750320
                    IE: Unknown: DD070017F203020180
                    IE: Unknown: DD0E0017F2070001010620C9D01DB1DB
                    IE: Unknown: DD0B0017F20100010100000007
          Cell 02 - Address: 2C:B0:5D:EF:23:F2
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=46/70  Signal level=-64 dBm  
                    Encryption key:on
                    ESSID:"ugsf6jpa"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000156ce17e270
                    Extra: Last beacon: 88ms ago
                    IE: Unknown: 000875677366366A7061
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001300000000000000000000000000000000000000
                    IE: Unknown: DD090010180202F0280000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: B2:B2:DC:54:D6:74
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=45/70  Signal level=-65 dBm  
                    Encryption key:on
                    ESSID:"Krammer78"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001a14c85fd03
                    Extra: Last beacon: 0ms ago
                    IE: Unknown: 00094B72616D6D65723738
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030102
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1017FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1602000600000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B050001477A12
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4304000000
                    IE: Unknown: 0706434820010D10
                    IE: Unknown: DD1E00904C336E1017FF000000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3402000600000000000000000000000000000000000000
          Cell 04 - Address: 40:4A:03:7D:A7:FB
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=36/70  Signal level=-74 dBm  
                    Encryption key:on
                    ESSID:"Fullrate"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000347a601b6
                    Extra: Last beacon: 1844ms ago
                    IE: Unknown: 000846756C6C72617465
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: 00:15:E9:0B:C9:7E
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"BMB"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000030a50651166
                    Extra: Last beacon: 1828ms ago
                    IE: Unknown: 0003424D42
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
                    IE: Unknown: 050402030000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
          Cell 06 - Address: 2C:B0:5D:D9:73:48
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"WiFiHumle"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000156d1cc51d1
                    Extra: Last beacon: 308ms ago
                    IE: Unknown: 00095769466948756D6C65
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B081100000000000000000000000000000000000000
                    IE: Unknown: DD090010180200F0280000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 07 - Address: 00:1E:2A:7D:33:5C
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"txvqqrju"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000fa7d47e341
                    Extra: Last beacon: 1344ms ago
                    IE: Unknown: 00087478767171726A75
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030108
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1608001700000000000000000000000000000000000000
                    IE: Unknown: DD090010180204F0280000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

```iwconfig:

```

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Villumsen"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: 20:C9:D0:1D:B1:DB   
          Bit Rate=104 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=60/70  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0

```

---

### Post by praseodym on 2013-02-01
Try channel 11 or 13, depending on the output of

```
iwlist chan
```
The last one available.

---

### Post by MVillumsen on 2013-02-01
iwlist chan:

```

eth0      no frequency information.

lo        no frequency information.

wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz


```

Still the same problem after changing to channel 11 or 13 :/

---

### Post by praseodym on 2013-02-01
Maybe you try to deactivate the N-mode in your router. Change to b+g only

---

### Post by MVillumsen on 2013-02-01
> **praseodym said:**
> Maybe you try to deactivate the N-mode in your router. Change to b+g only

The airport extreme changes automatically to fit the adapter, so that didn't change anything :/

---

### Post by MVillumsen on 2013-02-10
After booting to ubuntu today the wireless network is suddenly working just fine. I have no idea how it was fixed.. Maybe some update fixed it?

---

