---
title: "USB wireless error"
date: 2010-09-15
forum: Networking &amp; Wireless
---

### Post by pgcudahy on 2010-09-15
Hey, trying to install my Netgear MA111 USB wireless adapter on ubuntu. I've been narrowing down why it keeps failing and here's where I'm at. I got it set up with ndiswrapper then ran iwlist scan and it found all the nearby networks. Then I did exactly two things. Ran "sudo ndiswrapper -m" and installed wpasupplicant. When I rerun iwlist scan I get the error "wlan0     Failed to read scan data : Cannot allocate memory" This memory allocation error also comes up when I try to run wpa_supplicant and prevents it from connecting. Any thoughts?


```

patrick@BigBox:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 94:44:52:5D:FF:1C
                    ESSID:"MDX2"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:96/100  Signal level:-34 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:1A:C4:C9:87:E1
                    ESSID:"2WIRE318"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.422 GHz (Channel 3)
                    Quality:65/100  Signal level:-54 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 03 - Address: 68:7F:74:9E:97:F0
                    ESSID:"PurpleCheetah"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:23/100  Signal level:-81 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: 68:7F:74:9E:97:F2
                    ESSID:"PurpleCheetah-guest"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:25/100  Signal level:-80 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 05 - Address: 00:22:6B:46:D8:F2
                    ESSID:"whonkco"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:25/100  Signal level:-80 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK

patrick@BigBox:~$ sudo ndiswrapper -m
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...
patrick@BigBox:~$ sudo apt-get install wpasupplicant
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libnl1 libpcsclite1
Suggested packages:
  pcscd wpagui libengine-pkcs11-openssl
The following NEW packages will be installed:
  libnl1 libpcsclite1 wpasupplicant
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 538kB of archives.
After this operation, 1,438kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid/main libnl1 1.1-5build1 [129kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main libpcsclite1 1.5.3-1ubuntu4.1 [45.9kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ lucid/main wpasupplicant 0.6.9-3ubuntu3 [363kB]
Fetched 538kB in 3s (146kB/s)        
Selecting previously deselected package libnl1.
(Reading database ... 40879 files and directories currently installed.)
Unpacking libnl1 (from .../libnl1_1.1-5build1_i386.deb) ...
Selecting previously deselected package libpcsclite1.
Unpacking libpcsclite1 (from .../libpcsclite1_1.5.3-1ubuntu4.1_i386.deb) ...
Selecting previously deselected package wpasupplicant.
Unpacking wpasupplicant (from .../wpasupplicant_0.6.9-3ubuntu3_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up libnl1 (1.1-5build1) ...

Setting up libpcsclite1 (1.5.3-1ubuntu4.1) ...

Setting up wpasupplicant (0.6.9-3ubuntu3) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
patrick@BigBox:~$ sudo iwlist wlan0 scan
wlan0     Failed to read scan data : Cannot allocate memory

```

---

