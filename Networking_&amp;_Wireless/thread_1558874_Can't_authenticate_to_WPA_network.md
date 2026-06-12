---
title: "Can't authenticate to WPA network"
date: 2010-08-22
forum: Networking &amp; Wireless
---

### Post by netsense on 2010-08-22
Hi, and if you can help, thank you.

I have a TP-Link Atheros-based USB card: TL-WN422G. It's listed widely as being compatible, but I'm baffled if I can make it work.

I'm running an ndiswrapper (XP-64) driver, and that seems to be loaded and recognizing the hardware correctly. The system can scan and correctly identify our network, and other nearby ones, but when the WPA key is entered (correctly, I've triple checked), the "Secrets" windows just keeps popping up and no IP is acquired. I've installed and tried toi configure it with wpa-supplicant, all to no avail.

Can anyone help?

I've attached below a (long, sorry) list of various outputs that I've looked at.

Thanks, Edwin.

Ubuntu 10.04.1 LTS (Kubuntu); 2.6.32-24-server x86_64 

output of lsusb 
Bus 002 Device 002: ID 0040:073d  
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0413:6029 Leadtek Research, Inc. 
Bus 001 Device 002: ID 0cf3:1006 Atheros Communications, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root 

outpuut of lsmod 
Module                  Size  Used by
snd_hda_codec_nvhdmi     4760  1 
snd_hda_codec_via      33175  0 
tda18271               37906  1 
af9013                 21954  1 
snd_hda_intel          25677  2 
snd_hda_codec          85663  3 snd_hda_codec_nvhdmi,snd_hda_codec_via,snd_hda_intel
snd_hwdep               6778  1 snd_hda_codec
snd_pcm_oss            41234  0 
snd_mixer_oss          16107  1 snd_pcm_oss
snd_pcm                87248  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31027  0 
snd_seq_midi            5829  0 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
snd_rawmidi            23116  1 snd_seq_midi
softcursor              1565  1 bitblit
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
vga16fb                12757  1 
snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
vgastate                9857  1 vga16fb
snd_timer              23617  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
dvb_usb_af9015         30239  0 
dvb_usb                16709  1 dvb_usb_af9015
snd                    70946  15 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ppdev                   6375  0 
dvb_core              102993  1 dvb_usb
soundcore               8052  1 snd                                                            
nvidia              10832442  38                                                               
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm                                          
psmouse                64576  0                                                                
i2c_nforce2             6099  0                                                                
lp                      9336  0                                                                
shpchp                 33711  0                                                                
serio_raw               4950  0                                                                
ndiswrapper           244768  0                                                                
joydev                 10976  0                                                                
parport                37160  2 ppdev,lp                                                       
usbhid                 41084  0                                                                
hid                    83408  1 usbhid                                                         
ahci                   37870  2                                                                
forcedeth              55592  0  

output of ndiswrapper -l 
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
netathuwx : driver installed
        device (0CF3:1006) present

output of  iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

output of iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0F:B5:36:EE:69
                    ESSID:"Hymie"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:35/100  Signal level:-73 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:17:9A:1F:80:92
                    ESSID:"family"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)                                                                                                                    
                    Quality:10/100  Signal level:-89 dBm  Noise level:-96 dBm                                                                                          
                    Encryption key:on                                                                                                                                  
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s                                                                                               
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s                                                                                                
                              36 Mb/s; 48 Mb/s; 54 Mb/s                                                                                                                
                    Extra:bcn_int=100                                                                                                                                  
                    Extra:atim=0

output of dmesg | grep -e ndis -e wlan
[   20.562543] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   21.655144] ndiswrapper (link_pe_images:575): fixing KI_USER_SHARED_DATA address in the driver
[   21.667171] ndiswrapper: driver netathuwx (,01/04/2010,7.7.0.75) loaded
[   23.324680] wlan0: ethernet device d8:5d:4c:90:92:97 using NDIS driver: netathuwx, version: 0x70007, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0CF3:1006.F.conf
[   23.838735] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   23.842493] usbcore: registered new interface driver ndiswrapper
[   24.216987] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   53.058705] ndiswrapper (iw_set_auth:1602): invalid cmd 12
[   53.608534] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   53.612645] Modules linked in: snd_hda_codec_nvhdmi snd_hda_codec_via tda18271 af9013 snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi fbcon tileblit font bitblit snd_rawmidi softcursor snd_seq_midi_event vga16fb snd_seq vgastate snd_timer snd_seq_device dvb_usb_af9015 dvb_usb snd ppdev dvb_core soundcore nvidia(P) snd_page_alloc psmouse i2c_nforce2 lp shpchp serio_raw ndiswrapper joydev parport usbhid hid ahci forcedeth
[   53.612909]  [<ffffffffa0069a14>] ? ntdriver_thread+0x74/0xb0 [ndiswrapper]
[   53.612942]  [<ffffffffa00699e7>] ? ntdriver_thread+0x47/0xb0 [ndiswrapper]
[   53.612974]  [<ffffffffa00699a0>] ? ntdriver_thread+0x0/0xb0 [ndiswrapper]
[   63.630485] wlan0: no IPv6 routers present
[  117.949854] ndiswrapper (iw_set_auth:1602): invalid cmd 12

Output of sudo lshw -c Network
  *-network               
       description: Ethernet interface
       product: MCP79 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: b1
       serial: 00:25:22:47:1d:64
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
       resources: irq:22 memory:fae7d000-fae7dfff ioport:d080(size=8) memory:fae7e800-fae7e8ff memory:fae7e400-fae7e40f
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: d8:5d:4c:90:92:97
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netathuwx driverversion=1.55+,01/04/2010,7.7.0.75 link=no multicast=yes wireless=IEEE 802.11g

Output of ifconfig
eth0      Link encap:Ethernet  HWaddr 00:25:22:47:1d:64  
          inet addr:172.31.255.110  Bcast:172.31.255.255  Mask:255.255.255.0
          inet6 addr: fe80::225:22ff:fe47:1d64/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:608 errors:0 dropped:0 overruns:0 frame:0
          TX packets:417 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:631228 (631.2 KB)  TX bytes:67615 (67.6 KB)
          Interrupt:22 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4800 (4.8 KB)  TX bytes:4800 (4.8 KB)

wlan0     Link encap:Ethernet  HWaddr d8:5d:4c:90:92:97  
          inet6 addr: fe80::da5d:4cff:fe90:9297/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:64 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7232 (7.2 KB)  TX bytes:9166 (9.1 KB)

Output of sudo ifconfig -v wlan0 up is nothing (no change in wlan0 status, though.

Ouput of sudo /etc/init.d/networking restart                                                                                                              
 * Reconfiguring network interfaces...                                                                                                                                 Ignoring unknown interface eth0=eth0.
                                                                                                                                                                [ OK ]

Output of cat /var/log/kern.log | grep -e ndis -e wlan
Aug 23 09:58:31 Max-Headroom kernel: [   23.324680] wlan0: ethernet device d8:5d:4c:90:92:97 using NDIS driver: netathuwx, version: 0x70007, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0CF3:1006.F.conf
Aug 23 09:58:32 Max-Headroom kernel: [   23.838735] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Aug 23 09:58:32 Max-Headroom kernel: [   24.216987] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 23 09:59:02 Max-Headroom kernel: [   53.608534] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Aug 23 09:58:29 Max-Headroom kernel: [   20.562543] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
Aug 23 09:58:30 Max-Headroom kernel: [   21.655144] ndiswrapper (link_pe_images:575): fixing KI_USER_SHARED_DATA address in the driver
Aug 23 09:58:30 Max-Headroom kernel: [   21.667171] ndiswrapper: driver netathuwx (,01/04/2010,7.7.0.75) loaded
Aug 23 09:58:31 Max-Headroom kernel: [   23.324680] wlan0: ethernet device d8:5d:4c:90:92:97 using NDIS driver: netathuwx, version: 0x70007, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0CF3:1006.F.conf
Aug 23 09:58:32 Max-Headroom kernel: [   23.838735] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Aug 23 09:58:32 Max-Headroom kernel: [   23.842493] usbcore: registered new interface driver ndiswrapper
Aug 23 09:58:32 Max-Headroom kernel: [   24.216987] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 23 09:59:01 Max-Headroom kernel: [   53.058705] ndiswrapper (iw_set_auth:1602): invalid cmd 12
Aug 23 09:59:02 Max-Headroom kernel: [   53.608534] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Aug 23 09:59:02 Max-Headroom kernel: [   53.612645] Modules linked in: snd_hda_codec_nvhdmi snd_hda_codec_via tda18271 af9013 snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi fbcon tileblit font bitblit snd_rawmidi softcursor snd_seq_midi_event vga16fb snd_seq vgastate snd_timer snd_seq_device dvb_usb_af9015 dvb_usb snd ppdev dvb_core soundcore nvidia(P) snd_page_alloc psmouse i2c_nforce2 lp shpchp serio_raw ndiswrapper joydev parport usbhid hid ahci forcedeth
Aug 23 09:59:02 Max-Headroom kernel: [   53.612909]  [<ffffffffa0069a14>] ? ntdriver_thread+0x74/0xb0 [ndiswrapper]
Aug 23 09:59:02 Max-Headroom kernel: [   53.612942]  [<ffffffffa00699e7>] ? ntdriver_thread+0x47/0xb0 [ndiswrapper]
Aug 23 09:59:02 Max-Headroom kernel: [   53.612974]  [<ffffffffa00699a0>] ? ntdriver_thread+0x0/0xb0 [ndiswrapper]
Aug 23 09:59:12 Max-Headroom kernel: [   63.630485] wlan0: no IPv6 routers present
Aug 23 10:00:06 Max-Headroom kernel: [  117.949854] ndiswrapper (iw_set_auth:1602): invalid cmd 12

Output of cat /var/log/syslog | grep -e ndis -e wlan
Aug 23 09:58:29 Max-Headroom kernel: [   20.562543] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
Aug 23 09:58:30 Max-Headroom kernel: [   21.655144] ndiswrapper (link_pe_images:575): fixing KI_USER_SHARED_DATA address in the driver
Aug 23 09:58:30 Max-Headroom kernel: [   21.667171] ndiswrapper: driver netathuwx (,01/04/2010,7.7.0.75) loaded
Aug 23 09:58:31 Max-Headroom kernel: [   23.324680] wlan0: ethernet device d8:5d:4c:90:92:97 using NDIS driver: netathuwx, version: 0x70007, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0CF3:1006.F.conf
Aug 23 09:58:32 Max-Headroom kernel: [   23.838735] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
Aug 23 09:58:32 Max-Headroom kernel: [   23.842493] usbcore: registered new interface driver ndiswrapper
Aug 23 09:58:32 Max-Headroom NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:04.1/usb1/1-2/1-2:1.0/net/wlan0, iface: wlan0)
Aug 23 09:58:32 Max-Headroom NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:04.1/usb1/1-2/1-2:1.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Aug 23 09:58:32 Max-Headroom NetworkManager: <info>  (wlan0): driver does not support SSID scans (scan_capa 0x00).
Aug 23 09:58:32 Max-Headroom NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'ndiswrapper')
Aug 23 09:58:32 Max-Headroom NetworkManager: <info>  (wlan0): exported as /org/freedesktop/NetworkManager/Devices/1
Aug 23 09:58:32 Max-Headroom NetworkManager: <info>  (wlan0): now managed
Aug 23 09:58:32 Max-Headroom NetworkManager: <info>  (wlan0): device state change: 1 -> 2 (reason 2)
Aug 23 09:58:32 Max-Headroom NetworkManager: <info>  (wlan0): bringing up device.
Aug 23 09:58:32 Max-Headroom NetworkManager: <info>  (wlan0): preparing device.
Aug 23 09:58:32 Max-Headroom NetworkManager: <info>  (wlan0): deactivating device (reason: 2).
Aug 23 09:58:32 Max-Headroom kernel: [   24.216987] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 23 09:58:34 Max-Headroom NetworkManager: <info>  (wlan0): supplicant interface state:  starting -> ready
Aug 23 09:58:34 Max-Headroom NetworkManager: <info>  (wlan0): device state change: 2 -> 3 (reason 42)
Aug 23 09:58:55 Max-Headroom NetworkManager: <info>  Activation (wlan0) starting connection 'Hymie'
Aug 23 09:58:55 Max-Headroom NetworkManager: <info>  (wlan0): device state change: 3 -> 4 (reason 0)
Aug 23 09:58:55 Max-Headroom NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 23 09:58:55 Max-Headroom NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 23 09:58:55 Max-Headroom NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 23 09:58:55 Max-Headroom NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 23 09:58:55 Max-Headroom NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 23 09:58:55 Max-Headroom NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Aug 23 09:58:55 Max-Headroom NetworkManager: <info>  Activation (wlan0/wireless): access point 'Hymie' has security, but secrets are required.
Aug 23 09:58:55 Max-Headroom NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Aug 23 09:58:55 Max-Headroom NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 23 09:58:56 Max-Headroom NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 23 09:58:56 Max-Headroom NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 23 09:58:56 Max-Headroom NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Aug 23 09:58:56 Max-Headroom NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 23 09:58:56 Max-Headroom NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 23 09:58:56 Max-Headroom NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 23 09:58:56 Max-Headroom NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Aug 23 09:58:56 Max-Headroom NetworkManager: <info>  Activation (wlan0/wireless): connection 'Hymie' has security, and secrets exist.  No new secrets needed.
Aug 23 09:58:56 Max-Headroom NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 23 09:58:56 Max-Headroom NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Aug 23 09:58:56 Max-Headroom NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Aug 23 09:59:01 Max-Headroom NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Aug 23 09:59:01 Max-Headroom kernel: [   53.058705] ndiswrapper (iw_set_auth:1602): invalid cmd 12
Aug 23 09:59:02 Max-Headroom NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> 4-way handshake
Aug 23 09:59:02 Max-Headroom NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> associated
Aug 23 09:59:02 Max-Headroom kernel: [   53.608534] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
Aug 23 09:59:02 Max-Headroom kernel: [   53.612645] Modules linked in: snd_hda_codec_nvhdmi snd_hda_codec_via tda18271 af9013 snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi fbcon tileblit font bitblit snd_rawmidi softcursor snd_seq_midi_event vga16fb snd_seq vgastate snd_timer snd_seq_device dvb_usb_af9015 dvb_usb snd ppdev dvb_core soundcore nvidia(P) snd_page_alloc psmouse i2c_nforce2 lp shpchp serio_raw ndiswrapper joydev parport usbhid hid ahci forcedeth
Aug 23 09:59:02 Max-Headroom kernel: [   53.612909]  [<ffffffffa0069a14>] ? ntdriver_thread+0x74/0xb0 [ndiswrapper]
Aug 23 09:59:02 Max-Headroom kernel: [   53.612942]  [<ffffffffa00699e7>] ? ntdriver_thread+0x47/0xb0 [ndiswrapper]
Aug 23 09:59:02 Max-Headroom kernel: [   53.612974]  [<ffffffffa00699a0>] ? ntdriver_thread+0x0/0xb0 [ndiswrapper]
Aug 23 09:59:03 Max-Headroom NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Aug 23 09:59:03 Max-Headroom avahi-daemon[710]: Registering new address record for fe80::da5d:4cff:fe90:9297 on wlan0.*.
Aug 23 09:59:09 Max-Headroom NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> associated
Aug 23 09:59:09 Max-Headroom NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Aug 23 09:59:12 Max-Headroom NetworkManager: <info>  wlan0: link timed out.
Aug 23 09:59:12 Max-Headroom kernel: [   63.630485] wlan0: no IPv6 routers present
Aug 23 09:59:16 Max-Headroom NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> associated
Aug 23 09:59:16 Max-Headroom NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Aug 23 09:59:22 Max-Headroom NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> associated
Aug 23 09:59:23 Max-Headroom NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Aug 23 09:59:29 Max-Headroom NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> associated
Aug 23 09:59:30 Max-Headroom NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Aug 23 09:59:36 Max-Headroom NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> associated
Aug 23 09:59:37 Max-Headroom NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Aug 23 09:59:43 Max-Headroom NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> associated
Aug 23 09:59:44 Max-Headroom NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Aug 23 09:59:50 Max-Headroom NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> associated
Aug 23 09:59:51 Max-Headroom NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Aug 23 09:59:57 Max-Headroom NetworkManager: <info>  Activation (wlan0/wireless): association took too long.
Aug 23 09:59:57 Max-Headroom NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Aug 23 09:59:57 Max-Headroom NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets
Aug 23 09:59:57 Max-Headroom NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 23 09:59:57 Max-Headroom NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 23 09:59:57 Max-Headroom NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Aug 23 09:59:57 Max-Headroom NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 23 09:59:57 Max-Headroom NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 23 09:59:57 Max-Headroom NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 23 09:59:57 Max-Headroom NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Aug 23 09:59:59 Max-Headroom NetworkManager: <info>  Activation (wlan0/wireless): connection 'Hymie' has security, and secrets exist.  No new secrets needed.
Aug 23 09:59:59 Max-Headroom NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 23 09:59:59 Max-Headroom NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> disconnected
Aug 23 09:59:59 Max-Headroom NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Aug 23 10:00:01 Max-Headroom NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Aug 23 10:00:01 Max-Headroom NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Aug 23 10:00:06 Max-Headroom NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Aug 23 10:00:06 Max-Headroom kernel: [  117.949854] ndiswrapper (iw_set_auth:1602): invalid cmd 12
Aug 23 10:00:06 Max-Headroom NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> 4-way handshake
Aug 23 10:00:06 Max-Headroom NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> associated
Aug 23 10:00:07 Max-Headroom NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Aug 23 10:00:13 Max-Headroom NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> associated
Aug 23 10:00:14 Max-Headroom NetworkManager: <info>  wlan0: link timed out.
Aug 23 10:00:14 Max-Headroom NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Aug 23 10:00:20 Max-Headroom NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> associated
Aug 23 10:00:21 Max-Headroom NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Aug 23 10:00:27 Max-Headroom NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> associated
Aug 23 10:00:28 Max-Headroom NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Aug 23 10:00:34 Max-Headroom NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> associated
Aug 23 10:00:35 Max-Headroom NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Aug 23 10:00:41 Max-Headroom NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> associated
Aug 23 10:00:42 Max-Headroom NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Aug 23 10:00:48 Max-Headroom NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> associated
Aug 23 10:00:49 Max-Headroom NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Aug 23 10:00:55 Max-Headroom NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> associated
Aug 23 10:00:56 Max-Headroom NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
Aug 23 10:00:59 Max-Headroom NetworkManager: <info>  Activation (wlan0/wireless): association took too long.
Aug 23 10:00:59 Max-Headroom NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Aug 23 10:00:59 Max-Headroom NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets
Aug 23 10:01:00 Max-Headroom NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> disconnected
Aug 23 10:01:16 Max-Headroom NetworkManager: <info>  wlan0: link timed out.:mad:

---

### Post by bkratz on 2010-08-22
If you are trying to connect to your own AP you might try switching it to AES only, not tkip/aes encryption, it made the difference for me on wpa2.

I also noticed this in your listing above.

Aug 23 09:59:01 Max-Headroom kernel: [ 53.058705] ndiswrapper (iw_set_auth:1602): invalid cmd 12

You might want to look at this thread although I thought it had been taken care of. 

[http://georgia.ubuntuforums.org/showthread.php?t=1343847](http://georgia.ubuntuforums.org/showthread.php?t=1343847)

---

### Post by netsense on 2010-08-23
bkratz,
Our WAP is a Netgear WG602v3; it supports both TKIP and AES, but setting which one to use doesn't work - and upgrading firmware doesn't either. :(
I did see the cmd 12 message, but frankly overlooked investigating it. However, I have now patched ndiswrapper, and the cmd 12 error has gone; sadly, however, the problem remains the same.

---

### Post by p.tar on 2010-08-23
> **bkratz said:**
> If you are trying to connect to your own AP you might try switching it to AES only, not tkip/aes encryption, it made the difference for me on wpa2.

I just want to state, that setting the router to AES only on a D-Link 300 router let my Ralink rt2870 easily connect to the AP with WPA2.

This might not help the original poster, but maybe others who are struggling with these symptoms: While connecting, 'iwconfig' shows intermittently a "Wireless  ESSID:" name and and an associated "Access Point:", or no name and 'Not-Associated'.

The KNetworkmanager just prompts me every now and then for the password. Switching to WiCD (remove Knetworkmanager!) helped, because it says "authentication failure".

After setting 'AES-only' on the router, everything worked fine.

(Used 10.04 Lucid with latest ralink Updates from the 2010-08-19 update)

cu
p.tar

---

### Post by netsense on 2010-08-23
Ok, Solved it; the solution can be found at [http://www.linuxquestions.org/questions/linux-networking-3/cant-authenticate-to-wpa-network-827877/:p](http://www.linuxquestions.org/questions/linux-networking-3/cant-authenticate-to-wpa-network-827877/:p)

---

