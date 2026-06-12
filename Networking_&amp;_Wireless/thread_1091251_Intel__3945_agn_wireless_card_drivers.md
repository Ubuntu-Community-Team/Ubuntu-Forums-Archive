---
title: "Intel  3945 agn wireless card drivers"
date: 2009-03-09
forum: Networking &amp; Wireless
---

### Post by indrulz on 2009-03-09
Hi guys
I have been trying to install WPA drivers for intel 3945agn wireless card, I downloaded iwlwifi from intel drivers website. I downloaded the package and extracted it. The problem is when I type make it says error 1, and asked me to set the shell to bash, which I did and after typing in make it gives me the same error again.

Below is what I got 
```

root@PC:~/iwlwifi-1.2.25# make
Makefile:24: 
Makefile:25: WARNING: $SHELL not set to bash.
Makefile:26: If you experience build errors, try
Makefile:27: 'make SHELL=/bin/bash'.
Makefile:28: 
Kernel Makefile not found at '/lib/modules/2.6.27-11-generic/source'
chmod: cannot access `compatible/*': No such file or directory
/bin/sh: cannot create compatible/kversion: Directory nonexistent
-e 
Makefile has been modified by generate_compatible, please run `make' again

make: *** [compatible/kversion] Error 1
root@PC:~/iwlwifi-1.2.25# 

```


Cheers for the help guys

---

### Post by chili555 on 2009-03-09
What did not work correctly for you with the built-in iwlwifi drivers already in the kernel?

(Written from a Thinkpad T60 running iwl3945 perfectly.)

---

### Post by indrulz on 2009-03-12
I could not access wireless from university. The university IT people told me that I need WPA drivers for my network card

---

### Post by chili555 on 2009-03-12
The iwl3945 module works very well with WPA. Does yours connect to unencryted networks? Does it scan? Open a terminal and do:```
sudo iwlist wlan0 scan
```Any clues? I'd also love to see the result of:```
dmesg | grep iwl
```Thanks.

---

### Post by indrulz on 2009-03-14
here are the results for the first code 
```
root@PC:~# sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:1F:33:7D:C5:EC
                    ESSID:"EDY_NETWORK"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=42/100  Signal level:-84 dBm  Noise level=-73 dBm
                    Encryption key:off
                    IE: Unknown: 2D1A1C181AFFFF000000000000000000000000000000000000000000
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000492ebaa00b
                    Extra: Last beacon: 3476ms ago
          Cell 02 - Address: 00:1D:92:13:46:76
                    ESSID:"wlan-ap"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/100  Signal level:-91 dBm  Noise level=-73 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000abc89e59bf
                    Extra: Last beacon: 3828ms ago
          Cell 03 - Address: 00:1A:2B:0D:71:23
                    ESSID:"BigPond2760"
                    Mode:Master
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=42/100  Signal level:-84 dBm  Noise level=-73 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000000edc29a185
                    Extra: Last beacon: 3556ms ago
          Cell 04 - Address: 00:17:3F:68:41:64
                    ESSID:"belkin54g - iiNet"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=46/100  Signal level:-81 dBm  Noise level=-73 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=00000021fd275177
                    Extra: Last beacon: 2172ms ago
          Cell 05 - Address: 00:13:A3:97:47:9D
                    ESSID:"SpeedStream"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=54/100  Signal level:-76 dBm  Noise level=-73 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=000000abc86da122
                    Extra: Last beacon: 2420ms ago
          Cell 06 - Address: 00:1E:2A:18:CF:CA
                    ESSID:"NETGEAR yuko"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=43/100  Signal level:-83 dBm  Noise level=-73 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=000000abbf8c3184
                    Extra: Last beacon: 2116ms ago
          Cell 07 - Address: 00:1B:11:3F:0C:22
                    ESSID:"14100952inu"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=92/100  Signal level:-39 dBm  Noise level=-73 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=000000592d2681d0
                    Extra: Last beacon: 56ms ago
          Cell 08 - Address: 00:0C:E3:61:1B:FF
                    ESSID:"Virgin Broadband"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=43/100  Signal level:-83 dBm  Noise level=-73 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000009c6d41f183
                    Extra: Last beacon: 2120ms ago
          Cell 09 - Address: 00:1A:70:77:DB:9C
                    ESSID:""
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=59/100  Signal level:-72 dBm  Noise level=-73 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s; 12 Mb/s
                              18 Mb/s; 24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=00000000656761c6
                    Extra: Last beacon: 2188ms ago

```


Here are the results for the second bit of code

```


root@PC:~# dmesg | grep iwl
[   15.068152] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   15.068157] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   15.068278] iwl3945 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   15.068293] iwl3945 0000:05:00.0: setting latency timer to 64
[   15.068318] iwl3945: Detected Intel Wireless WiFi Link 3945ABG
[   15.202508] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   15.262008] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   15.894423] iwl3945 0000:05:00.0: PCI INT A disabled
[   28.131783] iwl3945 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   28.131949] iwl3945 0000:05:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100006)
[   28.132697] firmware: requesting iwlwifi-3945-1.ucode
[   28.259109] Registered led device: iwl-phy0:radio
[   28.259138] Registered led device: iwl-phy0:assoc
[   28.259200] Registered led device: iwl-phy0:RX
[   28.259226] Registered led device: iwl-phy0:TX

```

---

### Post by chili555 on 2009-03-14
Everything looks fine. May I assume you are trying to connect to:> Cell 07 - Address: 00:1B:11:3F:0C:22
                    ESSID:"14100952inu"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=92/100  Signal level:-39 dBm  Noise level=-73 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=000000592d2681d0
                    Extra: Last beacon: 56ms ago
The others have very low signal strength and you will have difficulty connecting or staying connected.

When you select that network in Network Manager and put in your WPA key, what happens? Does it just not connect?

---

### Post by mikewhatever on 2009-03-14
Not sure it makes any difference, but the card it 3945ABG, not ABN, and yes, the included driver works well with wpa/wpa2.

---

