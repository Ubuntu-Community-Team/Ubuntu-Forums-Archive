---
title: "Wireless shows as connected but won't load any sites"
date: 2010-01-06
forum: Networking &amp; Wireless
---

### Post by ThePinkWitch on 2010-01-06
I'm new to Ubuntu and i set up my wireless myself and I think I may have put in wrong settings. I looked through the forum and found these commands to put in the terminal from other posts. Could someone please see if they can fathom what I've done wrong. I have an wG111v2 netgear usb which works fine in windows but is very sluggish on Ubuntu. It worked for a while but since i have deleted and reinstalled my wireless numerous times I now can't get iternet at all. I have Ubuntu 9.10 on my machine which I duel boot with winXP. Thanks for any help :)

ayte@kaytesRocket:~$ sudo dhclient wlan0
[sudo] password for kayte: 
There is already a pid file /var/run/dhclient.pid with pid 1927
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:18:4d:19:cb:b1
Sending on   LPF/wlan0/00:18:4d:19:cb:b1
Sending on   Socket/fallback
DHCPREQUEST of 10.0.0.2 on wlan0 to 255.255.255.255 port 67
DHCPACK of 10.0.0.2 from 10.0.0.138
bound to 10.0.0.2 -- renewal in 884728642 seconds.
kayte@kaytesRocket:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:0a.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc RV535 [Radeon X1650 Series] (rev 9e)
01:00.1 Display controller: ATI Technologies Inc RV535 [Radeon X1650 Series] (rev 9e)
kayte@kaytesRocket:~$ lsusb
Bus 001 Device 007: ID 090c:1000 Feiya Technology Corp. Flash Drive
Bus 001 Device 005: ID 0846:6a00 NetGear, Inc. WG111v2 54 Mbps Wireless [RealTek RTL8187L]
Bus 001 Device 002: ID 04b8:0847 Seiko Epson Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 003 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
kayte@kaytesRocket:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3740  1 
nls_cp437               5372  1 
vfat                   10716  1 
fat                    51452  1 vfat
binfmt_misc             8356  1 
arc4                    1660  2 
ecb                     2524  2 
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
x_tables               16544  1 ip_tables
snd_seq_oss            28576  0 
ppdev                   6688  0 
usblp                  12636  0 
rtl8187                50624  0 
mac80211              181076  1 rtl8187
eeprom_93cx6            1916  1 rtl8187
cfg80211               93052  2 rtl8187,mac80211
led_class               4096  1 rtl8187
parport_pc             31940  1 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
shpchp                 32272  0 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
usbhid                 38208  0 
usb_storage            52576  1 
sis900                 19932  0 
mii                     5212  1 sis900
radeon                636000  2 
ttm                    36212  1 radeon
drm                   159584  4 radeon,ttm
i2c_algo_bit            5760  1 radeon
sis_agp                 6972  1 
agpgart                34988  3 ttm,drm,sis_agp
kayte@kaytesRocket:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3740  1 
nls_cp437               5372  1 
vfat                   10716  1 
fat                    51452  1 vfat
binfmt_misc             8356  1 
arc4                    1660  2 
ecb                     2524  2 
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
x_tables               16544  1 ip_tables
snd_seq_oss            28576  0 
ppdev                   6688  0 
usblp                  12636  0 
rtl8187                50624  0 
mac80211              181076  1 rtl8187
eeprom_93cx6            1916  1 rtl8187
cfg80211               93052  2 rtl8187,mac80211
led_class               4096  1 rtl8187
parport_pc             31940  1 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
shpchp                 32272  0 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
usbhid                 38208  0 
usb_storage            52576  1 
sis900                 19932  0 
mii                     5212  1 sis900
radeon                636000  2 
ttm                    36212  1 radeon
drm                   159584  4 radeon,ttm
i2c_algo_bit            5760  1 radeon
sis_agp                 6972  1 
agpgart                34988  3 ttm,drm,sis_agp
kayte@kaytesRocket:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3740  1 
nls_cp437               5372  1 
vfat                   10716  1 
fat                    51452  1 vfat
binfmt_misc             8356  1 
arc4                    1660  2 
ecb                     2524  2 
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
x_tables               16544  1 ip_tables
snd_seq_oss            28576  0 
ppdev                   6688  0 
usblp                  12636  0 
rtl8187                50624  0 
mac80211              181076  1 rtl8187
eeprom_93cx6            1916  1 rtl8187
cfg80211               93052  2 rtl8187,mac80211
led_class               4096  1 rtl8187
parport_pc             31940  1 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
shpchp                 32272  0 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
usbhid                 38208  0 
usb_storage            52576  1 
sis900                 19932  0 
mii                     5212  1 sis900
radeon                636000  2 
ttm                    36212  1 radeon
drm                   159584  4 radeon,ttm
i2c_algo_bit            5760  1 radeon
sis_agp                 6972  1 
agpgart                34988  3 ttm,drm,sis_agp
kayte@kaytesRocket:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3740  1 
nls_cp437               5372  1 
vfat                   10716  1 
fat                    51452  1 vfat
binfmt_misc             8356  1 
arc4                    1660  2 
ecb                     2524  2 
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
x_tables               16544  1 ip_tables
snd_seq_oss            28576  0 
ppdev                   6688  0 
usblp                  12636  0 
rtl8187                50624  0 
mac80211              181076  1 rtl8187
eeprom_93cx6            1916  1 rtl8187
cfg80211               93052  2 rtl8187,mac80211
led_class               4096  1 rtl8187
parport_pc             31940  1 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
shpchp                 32272  0 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
usbhid                 38208  0 
usb_storage            52576  1 
sis900                 19932  0 
mii                     5212  1 sis900
radeon                636000  2 
ttm                    36212  1 radeon
drm                   159584  4 radeon,ttm
i2c_algo_bit            5760  1 radeon
sis_agp                 6972  1 
agpgart                34988  3 ttm,drm,sis_agp
kayte@kaytesRocket:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:2a:dc:76:3a  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xa800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:91 errors:0 dropped:0 overruns:0 frame:0
          TX packets:91 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9549 (9.5 KB)  TX bytes:9549 (9.5 KB)

wlan0     Link encap:Ethernet  HWaddr 00:18:4d:19:cb:b1  
          inet addr:10.0.0.2  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::218:4dff:fe19:cbb1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:332 errors:0 dropped:0 overruns:0 frame:0
          TX packets:410 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:141674 (141.6 KB)  TX bytes:62879 (62.8 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-18-4D-19-CB-B1-31-39-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

kayte@kaytesRocket:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"SpeedStream2936"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:13:A3:F0:80:41   
          Bit Rate=24 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-37 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

kayte@kaytesRocket:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:13:A3:F0:80:41
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"SpeedStream2936"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 11248ms ago
                    IE: Unknown: 000F537065656453747265616D32393336
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030103
                    IE: Unknown: 2A0104
                    IE: Unknown: 32080C1218243048606C

---

### Post by Loosewheel on 2010-01-06
What do you have for DNS and Gateway?..(to resolve hostnames and to route you out there) My /etc/resolv.conf file looks like this:
domain myhome.westell.com
search myhome.westell.com
nameserver 192.168.1.1
You should have the 'search' and 'nameserver' lines in there.

---

### Post by ThePinkWitch on 2010-01-06
> **Loosewheel said:**
> What do you have for DNS and Gateway?..(to resolve hostnames and to route you out there) My /etc/resolv.conf file looks like this:
domain myhome.westell.com
search myhome.westell.com
nameserver 192.168.1.1
You should have the 'search' and 'nameserver' lines in there.

Thankyou for reply :)

I have nothing..in frustration I uninstalled Net manager and downloaded wicd from the net on my other computer. When I tried to install wicd the terminal couldn't install it. It appears I have to download something from the net..I don't have any internet. I tried to reinstall net manager from the ubuntu cd..but that was not possible either. Synaptic won't go there even tho I've enabled cd in resources. I will be bald soon.

---

### Post by ThePinkWitch on 2010-01-07
I reinstalled Ubuntu for the THIRD time and I still have terrible internet. It still says it's connected and won't load websites or download. Occasionally when it first loads up it will work well for a few seconds or minutes then just stops. I've spent two weeks and reinstalled twice over this. If I can't resolve it I will have to revert to Windoze and after all the time and effort on this I will be very unhappy :( Is there anyone who might be able to help? I have a WG111v2 dongle. My wifi modem is a SpeedStream 6520 if that helps. Thanks for any help.

---

### Post by Loosewheel on 2010-01-08
Sorry you're having so much trouble....looks like you are not alone with the wireless problems. Lots of talk about slow connections,wicd, ndiswrapper with the RTL8187 chipset.
The easiest solution may be to download, burn, and install Ubuntu-9.04. No garuntee, but it may fly right out of the box.

---

### Post by ThePinkWitch on 2010-01-08
> **Loosewheel said:**
> Sorry you're having so much trouble....looks like you are not alone with the wireless problems. Lots of talk about slow connections,wicd, ndiswrapper with the RTL8187 chipset.
The easiest solution may be to download, burn, and install Ubuntu-9.04. No garuntee, but it may fly right out of the box.

Thankyou for answering :) I'm going to try one last thing before I do that (install 9.04). I'm going to try the d-link usb router thingy from my other computer on Ubuntu and see if thats any better, How do I uninstall the RTL8187 and install the D-link? Any help is so appreciated :)

---

