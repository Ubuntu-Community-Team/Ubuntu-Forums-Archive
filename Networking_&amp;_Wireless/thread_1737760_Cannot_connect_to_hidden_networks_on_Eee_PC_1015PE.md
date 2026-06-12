---
title: "Cannot connect to hidden networks on Eee PC 1015PEM"
date: 2011-04-23
forum: Networking &amp; Wireless
---

### Post by MrProsser on 2011-04-23
I have an Eee PC 1015PEM with Ubuntu 10.10, I believe the wireless card is an rt3090 (though sometimes I see references to rt2860).  I had problems getting this to connect to any wireless network originally but eventually was able to fix this by blacklisting a number of modules.  However I am still unable to connect to hidden networks and have not been able to find a solution.  I was wondering if anyone might be able to help.

---

### Post by MrProsser on 2011-04-23
I am going to;  post some extra info here based on the networking sticky.  It will not post this as one message so I have to break it up.
The kernel is 2.6.35-28-generic i686


Output of lspic
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge (rev 02)
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications AR8132 Fast Ethernet (rev c0)
02:00.0 Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe

Output of lsusb:
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 13d3:5702 IMC Networks 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by MrProsser on 2011-04-23
Output of ifconfig:
eth0      Link encap:Ethernet  HWaddr 20:cf:30:5c:c5:34  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:45 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 74:f0:6d:04:ac:34  
          inet addr:192.168.3.6  Bcast:192.168.3.255  Mask:255.255.255.0
          inet6 addr: fe80::76f0:6dff:fe04:ac34/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:72269 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12999 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17053116 (17.0 MB)  TX bytes:3265712 (3.2 MB)
          Interrupt:17 

Output of iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     Ralink STA  ESSID:"NETGEAR"  Nickname:"RT2860STA"
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:90:4C:7E:00:6E   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-63 dBm  Noise level:-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Output of lsmod:
Module                  Size  Used by
joydev                  8767  0 
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
snd_hda_codec_realtek   218492  1 
snd_hda_intel          22235  2 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
i915                  295435  4 
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
eeepc_wmi               2899  0 
drm_kms_helper         30200  1 i915
sparse_keymap           3145  1 eeepc_wmi
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   168060  4 i915,drm_kms_helper
uvcvideo               55847  0 
snd                    49038  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                59033  0 
videodev               43098  1 uvcvideo
serio_raw               4022  0 
v4l1_compat            13359  2 uvcvideo,videodev
intel_agp              26566  2 i915
i2c_algo_bit            5168  1 i915
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
video                  18712  1 i915
agpgart                32011  2 drm,intel_agp
output                  1883  1 video
rt2860sta             504366  1 
crc_ccitt               1351  1 rt2860sta
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
atl1c                  29949  0 
ahci                   19198  2 
libahci                21728  1 ahci

Output of lshw -C network:
[sudo] password for suzy: 
  *-network               
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 74:f0:6d:04:ac:34
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 ip=192.168.3.6 latency=0 multicast=yes wireless=Ralink STA
       resources: irq:17 memory:fbff0000-fbffffff
  *-network
       description: Ethernet interface
       product: AR8132 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c0
       serial: 20:cf:30:5c:c5:34
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:45 memory:f7fc0000-f7ffffff ioport:ec00(size=128)

---

### Post by MrProsser on 2011-04-23
Output of iwlist scan:
wlan0     Scan completed :
          Cell 01 - Address: 00:26:50:34:6A:E9
                    Protocol:802.11b/g
                    ESSID:"BELL637"
                    Mode:Managed
                    Channel:1
                    Quality:73/100  Signal level:-61 dBm  Noise level:-83 dBm
                    Encryption key:eek:n
                    Bit Rates:18 Mb/s
          Cell 02 - Address: B0:E7:54:grin:9:AD:01
                    Protocol:802.11b/g
                    ESSID:"Lesdays"
                    Mode:Managed
                    Channel:6
                    Quality:78/100  Signal level:-59 dBm  Noise level:-83 dBm
                    Encryption key:eek:n
                    Bit Rates:18 Mb/s
          Cell 03 - Address: C0:C1:C0:1B:35:24
                    Protocol:802.11b/g/n
                    ESSID:"taucer"
                    Mode:Managed
                    Channel:6
                    Quality:78/100  Signal level:-59 dBm  Noise level:-83 dBm
                    Encryption key:eek:n
                    Bit Rates:144 Mb/s
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: 00:90:4C:7E:00:6E
                    Protocol:802.11b/g
                    ESSID:"NETGEAR"
                    Mode:Managed
                    Channel:11
                    Quality:73/100  Signal level:-61 dBm  Noise level:-83 dBm
                    Encryption key:eek:n
                    Bit Rates:54 Mb/s
          Cell 05 - Address: 94:44:52:50:5E:AC
                    Protocol:802.11b/g/n
                    ESSID:"Haluza"
                    Mode:Managed
                    Channel:11
                    Quality:42/100  Signal level:-73 dBm  Noise level:-83 dBm
                    Encryption key:eek:n
                    Bit Rates:300 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK

---

