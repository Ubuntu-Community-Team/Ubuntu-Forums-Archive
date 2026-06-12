---
title: "Another ndiswrapper / broadcom wireless problem"
date: 2010-02-23
forum: Networking &amp; Wireless
---

### Post by shoepolice on 2010-02-23
Hi there, I've just installed Ubuntu 9.10 on my aged Acer Aspire 3000 and am having the seemingly common problem of getting the wireless to work. What I've done so far...

Been through this thread;

[http://ubuntuforums.org/showthread.php?t=1188702](http://ubuntuforums.org/showthread.php?t=1188702) 

DETAILS REQUIRED:

network.txt;

  *-network:0
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:c0:9f:c3:2e:ff
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=half latency=173 link=no maxlatency=11 mingnt=52 multicast=yes port=MII speed=10MB/s
       resources: irq:19 ioport:1800(size=256) memory:e2005000-e2005fff memory:68000000-6801ffff(prefetchable)
  *-network:1
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: wlan0
       version: 02
       serial: 00:14:a4:23:a4:e2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.55+Broadcom,12/22/2004, 3.100. latency=64 link=no multicast=yes wireless=IEEE 802.11g
       resources: irq:17 memory:e2000000-e2001fff

AND rc.local file;

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0


AND (got this for a few of those commands)

jim@ubuntu:~$ sudo rmmod b43
[sudo] password for jim: 
ERROR: Module b43 does not exist in /proc/modules

2. Then saw and went through the comprehensive guide;

[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

All OK but got to the last step of reinstalling ndiswrapper as I was on v1.5. On trying to reinstall as per instructions got;

root@ubuntu:~/Desktop# tar -xzvf ndiswrapper*
tar: ndiswrapper*: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
root@ubuntu:~/Desktop# 


Error messages I get are "Unable to see if hardware is present" when installing the bcmwl5a driver and "Could not find a network configuration tool" when trying to configure connection in GUI.

Pleeeeeeeeeeeease can anyone help me?!

---

### Post by shoepolice on 2010-02-23
1. Acer Aspire 3000

2.
00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

00:0b.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)

3.
jim@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:c3:2e:ff  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fec3:2eff/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7107 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5664 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8093313 (8.0 MB)  TX bytes:917593 (917.5 KB)
          Interrupt:19 Base address:0x1800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:14:a4:23:a4:e2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Memory:e2000000-e2002000 

jim@ubuntu:~$ iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

4.
jim@ubuntu:~$ lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
b44                    28684  0 
ssb                    35364  1 b44
ndiswrapper           184700  0 
joydev                 10240  0 
pcmcia                 36808  0 
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
iptable_filter          3100  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
yenta_socket           24296  1 
rsrc_nonstatic         11644  1 yenta_socket
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
led_class               4096  0 
psmouse                56500  0 
serio_raw               5280  0 
k8temp                  4188  0 
pcmcia_core            36528  3 pcmcia,yenta_socket,rsrc_nonstatic
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
i2c_sis96x              3904  0 
shpchp                 32272  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
nls_iso8859_1           3740  1 
nls_cp437               5372  1 
vfat                   10716  1 
fat                    51452  1 vfat
sis900                 19932  0 
mii                     5212  2 b44,sis900
sis_agp                 6972  0 
amd64_agp               9796  1 
agpgart                34988  2 sis_agp,amd64_agp

5.
[   13.428827] wlan0: ethernet device 00:14:a4:23:a4:e2 using NDIS driver: bcmwl5a, version: 0x3642e00, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4318.5.conf
[   13.428854] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   13.438472] usbcore: registered new interface driver ndiswrapper
[   15.203074] type=1505 audit(1266967967.346:12): operation="profile_replace" pid=774 name=/usr/share/gdm/guest-session/Xsession
[   15.205352] type=1505 audit(1266967967.350:13): operation="profile_replace" pid=775 name=/sbin/dhclient3
[   15.205692] type=1505 audit(1266967967.350:14): operation="profile_replace" pid=775 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   15.205877] type=1505 audit(1266967967.350:15): operation="profile_replace" pid=775 name=/usr/lib/connman/scripts/dhclient-script
[   15.212501] type=1505 audit(1266967967.358:16): operation="profile_replace" pid=776 name=/usr/bin/evince
[   15.218559] type=1505 audit(1266967967.362:17): operation="profile_replace" pid=776 name=/usr/bin/evince-previewer
[   15.222264] type=1505 audit(1266967967.366:18): operation="profile_replace" pid=776 name=/usr/bin/evince-thumbnailer
[   15.229739] type=1505 audit(1266967967.374:19): operation="profile_replace" pid=778 name=/usr/lib/cups/backend/cups-pdf
[   15.230190] type=1505 audit(1266967967.374:20): operation="profile_replace" pid=778 name=/usr/sbin/cupsd
[   15.232715] type=1505 audit(1266967967.378:21): operation="profile_replace" pid=779 name=/usr/sbin/tcpdump
[   18.584135] ndiswrapper: device wlan0 removed
[   18.584155] ndiswrapper 0000:00:0b.0: PCI INT A disabled
[   18.584235] usbcore: deregistering interface driver ndiswrapper
[   18.601477] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[   18.616075] ndiswrapper: driver bcmwl5a (Broadcom,12/22/2004, 3.100.46.0) loaded
[   18.616327] ndiswrapper 0000:00:0b.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   18.624968] ndiswrapper: using IRQ 17
[   18.832816] wlan0: ethernet device 00:14:a4:23:a4:e2 using NDIS driver: bcmwl5a, version: 0x3642e00, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 14E4:4318.5.conf
[   18.832844] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK
[   18.848068] usbcore: registered new interface driver ndiswrapper
[   19.652436] ppdev: user-space parallel port driver
[   22.733112] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.720895] eth0: Media Link On 100mbps full-duplex 


6.
  *-network:0             
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 91
       serial: 00:c0:9f:c3:2e:ff
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=192.168.1.64 latency=173 link=yes maxlatency=11 mingnt=52 multicast=yes port=MII speed=100MB/s
       resources: irq:19 ioport:1800(size=256) memory:e2005000-e2005fff memory:68000000-6801ffff(prefetchable)
  *-network:1
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: wlan0
       version: 02
       serial: 00:14:a4:23:a4:e2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5a driverversion=1.56+Broadcom,12/22/2004, 3.100. latency=64 link=no multicast=yes wireless=IEEE 802.11g
       resources: irq:17 memory:e2000000-e2001fff

7.
wlan0     Scan completed :
          Cell 01 - Address: 00:1A:70:95:9C:14
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:18/100  Signal level:-84 dBm  Noise level:-96 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:21:04:12:A1:0D
                    ESSID:"Tiscali12A10D"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:20/100  Signal level:-83 dBm  Noise level:-96 dBm
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
          Cell 03 - Address: 00:1D:68:05:54:17
                    ESSID:"BTHomeHub-E81A"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.442 GHz (Channel 7)
                    Quality:89/100  Signal level:-39 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

8.
Ubuntu 9.10

9.
2.6.31-19-generic i686


10.
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
WARNING: ifup -a is disabled in favour of NetworkManager.
  Set ifupdown:managed=false in /etc/NetworkManager/nm-system-settings.conf.
                                                                         [ OK ]

---

