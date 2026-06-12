---
title: "Boroadcom BCM4318"
date: 2009-04-25
forum: Networking &amp; Wireless
---

### Post by patanjali on 2009-04-25
Hi all,

I have recently installed Kubuntu 8.04 and am having trouble getting my wireless PC card to work despite following the excellent howtos avi;lable through these fora.  It uses the Broadcom BCM4318 chipset.  I have installed the windows driver with Ndiswrapper but the link light never comes on.  See terminal outputs below which seem to suggest that all is well, but of course it's not.  

[COLOR="Red"]jack@phoenix:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:21:04:14:78:0B
                    ESSID:"Tiscali14780B"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:48/100  Signal level:-65 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
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
                       Preauthentication Supported

jack@phoenix:~$ dmesg | grep -e wlan -e ndis
[   47.548097] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   47.646167] ndiswrapper: driver bcmwl5 (ASUS,02/11/2005, 3.100.64.0) loaded
[   47.655096] ndiswrapper: using IRQ 16
[   48.009836] wlan0: ethernet device 00:18:39:c0:fc:b5 using NDIS driver: bcmwl5, version: 0x3644000, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4318.5.conf
[   48.009880] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   48.009971] usbcore: registered new interface driver ndiswrapper
[   57.358340] ndiswrapper: device wlan0 removed
[   57.359131] usbcore: deregistering interface driver ndiswrapper
[   57.430836] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[   57.462593] ndiswrapper: driver bcmwl5 (ASUS,02/11/2005, 3.100.64.0) loaded
[   57.472473] ndiswrapper: using IRQ 16
[  110.808094] wlan0: ethernet device 00:18:39:c0:fc:b5 using NDIS driver: bcmwl5, version: 0x3644000, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4318.5.conf
[  110.809187] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[  110.810146] usbcore: registered new interface driver ndiswrapper
[  592.708804] ADDRCONF(NETDEV_UP): wlan0: link is not ready[/COLOR]

Can anyone point me in the right direction. My laptop is an older Toshiba Satellite Pro A30 with a 2.1 GHz processor and 764 MB RAM.  

TIA

P  :confused:

---

