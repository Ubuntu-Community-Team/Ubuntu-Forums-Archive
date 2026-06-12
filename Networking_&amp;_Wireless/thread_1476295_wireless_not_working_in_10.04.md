---
title: "wireless not working in 10.04"
date: 2010-05-07
forum: Networking &amp; Wireless
---

### Post by eddiej23 on 2010-05-07
I did the normal fix by blacklisting certain drivers for the WUSB600, and the adapter is active, detects other wireless networks (including my own) but keeps asking for password.  I enter it, and it will ask for it again.  After 3 tries, it gives up.

These are the pertinent outputs (I hope):

eddie@eddie-desktop:~$ lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 645xx (rev 51)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:0a.0 Multimedia audio controller: Creative Labs SB X-Fi
01:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7600 GS] (rev a2)
eddie@eddie-desktop:~$ 

---------------------------------------------------------------

eddie@eddie-desktop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 06a3:075c Saitek PLC X52 Flight Controller
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 1737:0071 Linksys 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
eddie@eddie-desktop:~$ 

-----------------------------------------------------------------

eddie@eddie-desktop:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:320 errors:0 dropped:0 overruns:0 frame:0
          TX packets:320 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:23184 (23.1 KB)  TX bytes:23184 (23.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1e:e5:d9:82:d3  
          inet6 addr: fe80::21e:e5ff:fed9:82d3/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:32173 errors:0 dropped:0 overruns:11665230 frame:11665230
          TX packets:11665899 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8552420 (8.5 MB)  TX bytes:44624 (44.6 KB)

eddie@eddie-desktop:~$ 

-----------------------------------------------------------------

eddie@eddie-desktop:~$ iwconfig
lo        no wireless extensions.

wlan0     RTxx70 Wireless  ESSID:""  Nickname:"RT3070STA"
          Mode:Auto  Frequency=2.462 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=77/100  Signal level:-84 dBm  Noise level:-87 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eddie@eddie-desktop:~$ 

-----------------------------------------------------------------

eddie@eddie-desktop:~$  lsmod
Module                  Size  Used by
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_intel8x0           25588  1 
snd_ctxfi              82726  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  4 snd_intel8x0,snd_ctxfi,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
nouveau               467048  2 
ttm                    49943  1 nouveau
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         29297  1 nouveau
drm                   162471  4 nouveau,ttm,drm_kms_helper
ppdev                   5259  0 
snd                    54148  17 snd_intel8x0,snd_ctxfi,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sis_agp                 4047  1 
i2c_algo_bit            5028  1 nouveau
rt2870sta             461811  1 
joydev                  8708  0 
parport_pc             25962  1 
soundcore               6620  1 snd
shpchp                 28820  0 
agpgart                31724  3 ttm,drm,sis_agp
snd_page_alloc          7076  3 snd_intel8x0,snd_ctxfi,snd_pcm
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
usbhid                 36110  0 
hid                    67032  1 usbhid
floppy                 53016  0 
sata_sis                3332  5 
eddie@eddie-desktop:~$ 

-----------------------------------------------------------------

eddie@eddie-desktop:~$ sudo lshw -C network
[sudo] password for eddie: 
  *-network               
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1e:e5:d9:82:d3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=RTxx70 Wireless
eddie@eddie-desktop:~$ 

-----------------------------------------------------------------

eddie@eddie-desktop:~$ iwlist scan
lo        Interface doesn't support scanning.

wlan0     No scan results

eddie@eddie-desktop:~$ 

eddie@eddie-desktop:~$ lsb_release -d
Description:    Ubuntu 10.04 LTS
eddie@eddie-desktop:~$ 

eddie@eddie-desktop:~$ uname -mr
2.6.32-21-generic i686
eddie@eddie-desktop:~$ 

-----------------------------------------------------------------

TIA

Ed

---

### Post by RyanKH on 2010-05-16
I have had precisely the same issues.  Does anyone have any ideas?

Cheers,
Ryan

---

### Post by pdc on 2010-05-17
would you feel like working through this guide

[http://ubuntuforums.org/showthread.php?t=641598](http://ubuntuforums.org/showthread.php?t=641598)

your device should use the rt2870sta as here

[http://ohioloco.ubuntuforums.org/showthread.php?t=1423100](http://ohioloco.ubuntuforums.org/showthread.php?t=1423100)

 it seems loaded: and you have configured your wireless ?

---

### Post by eddiej23 on 2010-05-26
Wireless is configured.  I manually put in a MAC address, but do not have/find a BSSID address.  Keeps asking for password three times and quits.

So, next question: What wireless USB adapter DOES work in 10.04?

Thanks,

Ed

---

### Post by nibblet5109 on 2010-05-26
I'm also having problems - drivers are good, and active, but no wireless in sight.  I'm using a WPC54G v1.0 card in a toshiba satellite if that's needed - I have no wire connect opportunity to download wicd... so I'm open to suggestions.  Thanks!

RAB

---

### Post by eddiej23 on 2010-05-27
Thanks for all the help.  Nothing worked.  I even tried a wired connection, and to my surprise: nothing AGAIN!
Things that used to work, don't now.  I don't have the time to mess with this anymore.  As far as I'm concerned, Windows just works.  Ubuntu does not.

Ed

---

