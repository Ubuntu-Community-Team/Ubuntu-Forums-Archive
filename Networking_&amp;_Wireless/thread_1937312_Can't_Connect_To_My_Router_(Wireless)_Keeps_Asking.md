---
title: "Can't Connect To My Router (Wireless) Keeps Asking For Password"
date: 2012-03-07
forum: Networking &amp; Wireless
---

### Post by DuckyVader on 2012-03-07
Hello, I'm running Ubuntu 10.04 trying to connect to my Netgear router wifi, but it just shows the little circle loading icon and just keeps asking me for my wifi password.

I also made my phone a hotspot to try and connect to it and it did the same thing but after a little while in connected to it.

In Terminal I typed:
> uname -a
lspci -nnk | grep -iA2 net
iwconfig
sudo iwlist scan #which network is yours
lsmod
route -n
cat /etc/resolv.conf

And Got:

> 
ducky@gio-desktop:~$ uname -a
Linux gio-desktop 2.6.32-39-generic #86-Ubuntu SMP Mon Feb 13 21:47:32 UTC 2012 i686 GNU/Linux
ducky@gio-desktop:~$ lspci -nnk | grep -iA2 net
00:04.0 Ethernet controller [0200]: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet [1039:0900] (rev 90)
	Kernel driver in use: sis900
	Kernel modules: sis900
ducky@gio-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RTxx70 Wireless  ESSID:""  Nickname:"RT3070STA"
          Mode:Auto  Frequency=2.457 GHz  Access Point: C0:3F:0E:73:9B:31   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:-69 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ducky@gio-desktop:~$ sudo iwlist scan #which network is yours
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: C0:3F:0E:73:9B:31
                    Protocol:802.11g/n
                    ESSID:"DeathMachine"
                    Mode:Managed
                    Channel:10
                    Quality:52/100  Signal level:-69 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:18 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:24:7B:F8:9B:38
                    Protocol:802.11b/g/n
                    ESSID:"RAMIREZ"
                    Mode:Managed
                    Channel:11
                    Quality:42/100  Signal level:-73 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

ducky@gio-desktop:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
snd_intel8x0           25652  2 
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
snd_timer              19130  2 snd_pcm,snd_seq
fbcon                  35102  72 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
softcursor              1189  1 bitblit
snd                    54244  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
vga16fb                11385  1 
vgastate                8961  1 vga16fb
soundcore               6620  1 snd
shpchp                 28835  0 
amd64_agp               7165  1 
agpgart                31724  1 amd64_agp
ppdev                   5259  0 
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
k8temp                  3152  0 
parport_pc             25962  1 
rt2870sta             461811  1 
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
ohci1394               26950  0 
usbhid                 36110  0 
hid                    67288  1 usbhid
ieee1394               81181  1 ohci1394
sata_sis                3332  2 
sis900                 17048  0 
mii                     4381  1 sis900
ducky@gio-desktop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
70.190.128.0    0.0.0.0         255.255.248.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         70.190.128.1    0.0.0.0         UG    0      0        0 eth0

DEATHMACHINE is the one I'm trying to connect to.

NOTE: Right now I have my pc connected to my modem, wired, for internet.

---

