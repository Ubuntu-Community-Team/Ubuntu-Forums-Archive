---
title: "No wireless signals. Wireless card is detected."
date: 2009-01-21
forum: Networking &amp; Wireless
---

### Post by abbasali on 2009-01-21
Hello,

I recently bought a wireless router 54 Mbps 802.11g TRENDnet TEW-432BRP. I first test it on Vista and it worked seemlessly. I secured the router with WPA encryption shared key. I then rebooted the laptop to Kubuntu and the wireless worked there also. I was able to connect to the router by specifying the security key.

But when i started the kubuntu the next day, i was not able to see any wifi signals. The wifi connection was there (as i have saved it in the first go) in networkmanager but it was not getting connected. I tried rebooting a few times but no luck.

I am providing some debug info below. Hope it will help in finding the issue.

Machine - Toshiba L310 Laptop
Wireless card - Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (from lspci)

```

iwconfig

wlan0     IEEE 802.11abg  ESSID:""
          Mode:Managed  Frequency:2.417 GHz  Access Point: Not-Associated
          Tx-Power=15 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


iwlist scan
wlan0     Scan completed :
          Cell 01 - Address: 00:14:D1:3F:BC:6F
                    ESSID:"TRENDnet"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=62/100  Signal level:-70 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=0000000265e8f181
                    Extra: Last beacon: 1336ms ago

dmesg (only related to wireless)
[   15.969764] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks                                                       
[   15.969768] iwl3945: Copyright(c) 2003-2008 Intel Corporation                                                                                             
[   16.013596] iwl3945 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17                                                                              
[   16.013612] iwl3945 0000:08:00.0: setting latency timer to 64                                                                                             
[   16.013641] iwl3945: Detected Intel Wireless WiFi Link 3945ABG                                                                                            
[   16.076575] iwl3945: Tunable channels: 13 802.11bg, 23 802.11a channels 
[   16.413067] iwl3945 0000:08:00.0: PCI INT A disabled 
[   94.997260] iwl3945 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17                                                                              
[   94.997411] iwl3945 0000:08:00.0: restoring config space at offset 0x1 (was 0x100002, writing 0x100006)

```

OS - Kubuntu 8.10
Kernel - 2.6.27-9-generic i686

I will appreciate any help in this regards.

Thanks.

---

