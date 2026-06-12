---
title: "Dlink dwa-130/ Lucid (10.04) Not Connecting after upgrade"
date: 2010-11-08
forum: Networking &amp; Wireless
---

### Post by nolesce on 2010-11-08
I upgraded from to Lucid and the wireless network no longer connects. It continuously asks for my WPA password. (i did find this issue elsewhere but the solution I saw was to wait for lucid which would fix it.)  below is the inf the sticky asks for

```


lsusb 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 07d1:3b11 D-Link System Wireless N Adapter DWA-130
Bus 001 Device 002: ID 04fc:05d8 Sunplus Technology Co., Ltd 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:52 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:1b:11:f1:d9:ac  
          inet6 addr: fe80::21b:11ff:fef1:d9ac/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:320 errors:0 dropped:0 overruns:0 frame:0
          TX packets:455 errors:0 dropped:9 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:90199 (90.1 KB)  TX bytes:65884 (65.8 KB)

lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
r128                   35235  3 
drm                   162409  4 r128
snd_intel8x0           25588  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54180  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ppdev                   5259  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
dell_wmi                1793  0 
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
dcdbas                  5422  0 
soundcore               6620  1 snd
parport_pc             25962  1 
joydev                  8708  0 
ndiswrapper           184677  0 
vga16fb                11385  1 
vgastate                8961  1 vga16fb
psmouse                63245  0 
serio_raw               3978  0 
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
intel_agp              24119  1 
agpgart                31724  2 drm,intel_agp
shpchp                 28820  0 
intel_rng               2276  0 
lp                      7060  0 
parport                32635  3 ppdev,parport_pc,lp
3c59x                  31839  0 
floppy                 53016  0 
mii                     4381  1 3c59x
hid_sunplus             1259  0 
usbhid                 36110  0 
hid                    67032  2 hid_sunplus,usbhid

dmesg
[76059.154500] ndiswrapper (iw_set_auth:1602): invalid cmd 12
(about 2 or so screens of the same message)

sudo lshw -C network
[sudo] password for carlea: 
  *-network               
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: c
       bus info: pci@0000:02:0c.0
       logical name: eth0
       version: 78
       serial: 00:0b:db:a7:e1:9d
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=half latency=64 link=no maxlatency=10 mingnt=10 multicast=yes port=MII speed=10MB/s
       resources: irq:18 ioport:dc80(size=128) memory:ff6ffc00-ff6ffc7f memory:20000000-2001ffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1b:11:f1:d9:ac
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netmw245 driverversion=1.55+Marvell,11/27/2006,1.0.4.9 link=no multicast=yes wireless=IEEE 802.11g

iwlist scan 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1E:58:40:B6:AF
                    ESSID:"dlink"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:54/100  Signal level:-61 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 68:7F:74:8C:D3:8C
                    ESSID:"toshiba"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:26/100  Signal level:-79 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK


lsb_release -d
Description:	Ubuntu 10.04.1 LTS

uname -mr
2.6.32-25-generic i686

sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          WARNING: All config files need .conf: /etc/modprobe.d/linux-wlan-ng, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist-modem, it will be ignored in a future release.
FATAL: Module p80211 not found.
Failed to load p80211.ko.
run-parts: /etc/network/if-pre-up.d/linux-wlan-ng-pre-up exited with return code 1
There is already a pid file /var/run/dhclient.wlan0.pid with pid 1164
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/00:1b:11:f1:d9:ac
Sending on   LPF/wlan0/00:1b:11:f1:d9:ac
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                         

```

In addition (if this helps) the logs from the router

```

NFO]	Sun Feb 01 14:20:26 2004	Wireless system with MAC address 001B11F1D9AC associated
[INFO]	Sun Feb 01 14:20:15 2004	Wireless system with MAC address 001B11F1D9AC disconnected for reason: Received Deauthentication.
[INFO]	Sun Feb 01 14:20:05 2004	Wireless system with MAC address 001B11F1D9AC associated
[INFO]	Sun Feb 01 14:20:03 2004	Wireless system with MAC address 001B11F1D9AC disconnected for reason: Received Deauthentication.
[INFO]	Sun Feb 01 14:20:03 2004	Wireless system with MAC address 001B11F1D9AC associated

```

The connection was working fine (except for constantly having to reconnect through network manager every few minutes) until the upgrade. Now no connection at all. I can see the led blinking rapidly (as it does when attempting to connect) and it cycles frequently. :confused:

---

### Post by uncaspi on 2010-11-08
You got a bad message in dmesg pointing to a bug in ndiswrapper according to this thread.

[http://ubuntuforums.org/showthread.php?t=1343847](http://ubuntuforums.org/showthread.php?t=1343847)

---

### Post by nolesce on 2010-11-09
Well yes and no. I fixed that problem and dmesg is better but still no connection.](*,)

---

