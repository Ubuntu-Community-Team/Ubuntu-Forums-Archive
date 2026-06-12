---
title: "No wireless connection"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by malcburt on 2009-11-04
Hi,
I'm a complete newbie to this and I've just completed a Wubi installation of 9.10, because all my drivers were supposed to work (I thought).  I've got a Dell Wireless 1370 WLAN Mini-PCI card in a Dell Latitude 110L, with a Broadcom 3.100.35.0 driver.  However no joy getting my wireless connection booting into Wubi.
I found a thread on this subject which said I needed to install bcmwl-kernel-source, so I downloaded this and copied it to USB flash drive. I right clicked on the file to open with GDebu Package Installer but this failed with the message "Error: dependency is not satisfiable: dkms".  The only advice I could find on what to do next said I had to use a wired connection to the internet however I don't seem to be able to make that work, even under XP.  Is there another way?  I tried to improvise following the same thread (really not knowing what I was doing and typed "sudo apt-get remove dkms" but it said it couldn't find dkms so gave up.
Thanks!

---

### Post by quinnten83 on 2009-11-05
> **malcburt said:**
> Hi,
I'm a complete newbie to this and I've just completed a Wubi installation of 9.10, because all my drivers were supposed to work (I thought).  I've got a Dell Wireless 1370 WLAN Mini-PCI card in a Dell Latitude 110L, with a Broadcom 3.100.35.0 driver.  However no joy getting my wireless connection booting into Wubi.
I found a thread on this subject which said I needed to install bcmwl-kernel-source, so I downloaded this and copied it to USB flash drive. I right clicked on the file to open with GDebu Package Installer but this failed with the message "Error: dependency is not satisfiable: dkms".  The only advice I could find on what to do next said I had to use a wired connection to the internet however I don't seem to be able to make that work, even under XP.  Is there another way?  I tried to improvise following the same thread (really not knowing what I was doing and typed "sudo apt-get remove dkms" but it said it couldn't find dkms so gave up.
Thanks!

Hey, I am by no means an expert on wireless (mine has usually worked).
Lets start testing if your wireless is recognized first.
- Are thenecesarry lights blinking?
 run the following command in terminal ```
lspci
```
you can find the terminal under applications > Accessories > terminal
look for something refering to wireless and then post that here.
If it is recognized we can take it from there, if not, we are majorly...
I allready suggested another wireless card, lynksys hasn't given me much problems yet, but broadcom cards have been hell for many for years...

---

### Post by ajm2009 on 2009-11-05
Hi, I have the same problem. No wireless. This is what I got from Terminal:
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:09.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 4)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] HyperTransport Configuration (rev 40)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 11h [Turion X2, Athlon X2, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Mobile K10 [Turion X2, Athlon X2, Sempron] Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]
02:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 4357 (rev 10)
06:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

 
Can anyone tell me how I can get my wireless card to work????

---

### Post by malcburt on 2009-11-05
OK here we go. Hopefully the mention of my Wireless LAN controller is good news... right?

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)

So where do I go from here?

---

### Post by malcburt on 2009-11-07
Hi,
OK I realise I ought to have followed the instructions as to how to post a thread on here, so I did my best to gather all the relevant information from the command line. Sorry it's a bit verbose but in a couple of cases couldn't work out how to get just the info about my wireless so bear with me.  As I said further up the thread I got as far as trying but failing to install bcmwl-kernel-source from a USB stick (I haven't got a wired internet connection).  So here it all is.  Any help of what to do next much appreciated. From a position of total ignorance it's funny that iwlist scan says the network is down. It certainly isn't if I run under XP on the same machine (or else I wouldn't be typing this!)...
Thanks!



malcburt@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
02:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)

malcburt@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:12:3f:f7:9e:83  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

malcburt@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

malcburt@ubuntu:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3740  0 
nls_cp437               5372  0 
vfat                   10716  0 
fat                    51452  1 vfat
usb_storage            52544  0 
binfmt_misc             8356  1 
ppdev                   6688  0 
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
arc4                    1660  2 
ecb                     2524  2 
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
b43                   122136  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
iptable_filter          3100  0 
pcmcia                 36808  0 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ip_tables              11692  1 iptable_filter
joydev                 10272  0 
snd_timer              22276  2 snd_pcm,snd_seq
mac80211              181236  1 b43
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           24200  1 
x_tables               16544  1 ip_tables
cfg80211               93052  2 b43,mac80211
rsrc_nonstatic         11644  1 yenta_socket
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
psmouse                56180  0 
led_class               4096  1 b43
dell_wmi                2564  0 
serio_raw               5280  0 
dell_laptop             8128  0 
lp                      8964  0 
dcdbas                  7292  1 dell_laptop
parport                35340  2 ppdev,lp
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
i915                  221064  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
ssb                    35300  1 b43
e100                   32452  0 
mii                     5212  1 e100
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video

malcburt@ubuntu:~$ dmesg

*** couldn't paste 1st bit of the output from terminal, there was so much! this is all I could get... ***

[    0.167933] system 00:0b: ioport range 0x13c0-0x13df has been reserved
[    0.167938] system 00:0b: ioport range 0x17b0-0x17bb has been reserved
[    0.167942] system 00:0b: ioport range 0x17c0-0x17df has been reserved
[    0.167947] system 00:0b: ioport range 0x1bb0-0x1bbb has been reserved
[    0.167951] system 00:0b: ioport range 0x1bc0-0x1bdf has been reserved
[    0.167955] system 00:0b: ioport range 0x1fb0-0x1fbb has been reserved
[    0.167960] system 00:0b: ioport range 0x1fc0-0x1fdf has been reserved
[    0.167964] system 00:0b: ioport range 0x23b0-0x23bb has been reserved
[    0.167969] system 00:0b: ioport range 0x23c0-0x23df has been reserved
[    0.167973] system 00:0b: ioport range 0x27b0-0x27bb has been reserved
[    0.167978] system 00:0b: ioport range 0x27c0-0x27df has been reserved
[    0.167982] system 00:0b: ioport range 0x2bb0-0x2bbb has been reserved
[    0.167986] system 00:0b: ioport range 0x2bc0-0x2bdf has been reserved
[    0.168001] system 00:0b: ioport range 0x2fb0-0x2fbb has been reserved
[    0.168005] system 00:0b: ioport range 0x2fc0-0x2fdf has been reserved
[    0.168010] system 00:0b: ioport range 0x33b0-0x33bb has been reserved
[    0.168014] system 00:0b: ioport range 0x33c0-0x33df has been reserved
[    0.168019] system 00:0b: ioport range 0x37b0-0x37bb has been reserved
[    0.168023] system 00:0b: ioport range 0x37c0-0x37df has been reserved
[    0.168028] system 00:0b: ioport range 0x3bb0-0x3bbb has been reserved
[    0.168032] system 00:0b: ioport range 0x3bc0-0x3bdf has been reserved
[    0.168037] system 00:0b: ioport range 0x3fb0-0x3fbb has been reserved
[    0.168041] system 00:0b: ioport range 0x3fc0-0x3fdf has been reserved
[    0.168046] system 00:0b: ioport range 0x43b0-0x43bb has been reserved
[    0.168050] system 00:0b: ioport range 0x43c0-0x43df has been reserved
[    0.168055] system 00:0b: ioport range 0x47b0-0x47bb has been reserved
[    0.168060] system 00:0b: ioport range 0x47c0-0x47df has been reserved
[    0.168064] system 00:0b: ioport range 0x4bb0-0x4bbb has been reserved
[    0.168069] system 00:0b: ioport range 0x4bc0-0x4bdf has been reserved
[    0.168073] system 00:0b: ioport range 0x4fb0-0x4fbb has been reserved
[    0.168078] system 00:0b: ioport range 0x4fc0-0x4fdf has been reserved
[    0.168082] system 00:0b: ioport range 0x53b0-0x53bb has been reserved
[    0.168087] system 00:0b: ioport range 0x53c0-0x53df has been reserved
[    0.168092] system 00:0b: ioport range 0x57b0-0x57bb has been reserved
[    0.168096] system 00:0b: ioport range 0x57c0-0x57df has been reserved
[    0.168101] system 00:0b: ioport range 0x5bb0-0x5bbb has been reserved
[    0.168106] system 00:0b: ioport range 0x5bc0-0x5bdf has been reserved
[    0.168110] system 00:0b: ioport range 0x5fb0-0x5fbb has been reserved
[    0.168115] system 00:0b: ioport range 0x5fc0-0x5fdf has been reserved
[    0.168120] system 00:0b: ioport range 0x63b0-0x63bb has been reserved
[    0.168124] system 00:0b: ioport range 0x63c0-0x63df has been reserved
[    0.168129] system 00:0b: ioport range 0x67b0-0x67bb has been reserved
[    0.168134] system 00:0b: ioport range 0x67c0-0x67df has been reserved
[    0.168138] system 00:0b: ioport range 0x6bb0-0x6bbb has been reserved
[    0.168143] system 00:0b: ioport range 0x6bc0-0x6bdf has been reserved
[    0.168148] system 00:0b: ioport range 0x6fb0-0x6fbb has been reserved
[    0.168152] system 00:0b: ioport range 0x6fc0-0x6fdf has been reserved
[    0.168157] system 00:0b: ioport range 0x73b0-0x73bb has been reserved
[    0.168162] system 00:0b: ioport range 0x73c0-0x73df has been reserved
[    0.168167] system 00:0b: ioport range 0x77b0-0x77bb has been reserved
[    0.168171] system 00:0b: ioport range 0x77c0-0x77df has been reserved
[    0.168176] system 00:0b: ioport range 0x7bb0-0x7bbb has been reserved
[    0.168181] system 00:0b: ioport range 0x7bc0-0x7bdf has been reserved
[    0.168186] system 00:0b: ioport range 0x7fb0-0x7fbb has been reserved
[    0.168190] system 00:0b: ioport range 0x7fc0-0x7fdf has been reserved
[    0.168195] system 00:0b: ioport range 0x83b0-0x83bb has been reserved
[    0.168200] system 00:0b: ioport range 0x83c0-0x83df has been reserved
[    0.168205] system 00:0b: ioport range 0x87b0-0x87bb has been reserved
[    0.168210] system 00:0b: ioport range 0x87c0-0x87df has been reserved
[    0.168214] system 00:0b: ioport range 0x8bb0-0x8bbb has been reserved
[    0.168219] system 00:0b: ioport range 0x8bc0-0x8bdf has been reserved
[    0.168224] system 00:0b: ioport range 0x8fb0-0x8fbb has been reserved
[    0.168229] system 00:0b: ioport range 0x8fc0-0x8fdf has been reserved
[    0.168234] system 00:0b: ioport range 0x93b0-0x93bb has been reserved
[    0.168239] system 00:0b: ioport range 0x93c0-0x93df has been reserved
[    0.168244] system 00:0b: ioport range 0x97b0-0x97bb has been reserved
[    0.168248] system 00:0b: ioport range 0x97c0-0x97df has been reserved
[    0.168253] system 00:0b: ioport range 0x9bb0-0x9bbb has been reserved
[    0.168258] system 00:0b: ioport range 0x9bc0-0x9bdf has been reserved
[    0.168263] system 00:0b: ioport range 0x9fb0-0x9fbb has been reserved
[    0.168268] system 00:0b: ioport range 0x9fc0-0x9fdf has been reserved
[    0.168273] system 00:0b: ioport range 0xa3b0-0xa3bb has been reserved
[    0.168278] system 00:0b: ioport range 0xa3c0-0xa3df has been reserved
[    0.168283] system 00:0b: ioport range 0xa7b0-0xa7bb has been reserved
[    0.168288] system 00:0b: ioport range 0xa7c0-0xa7df has been reserved
[    0.168293] system 00:0b: ioport range 0xabb0-0xabbb has been reserved
[    0.168298] system 00:0b: ioport range 0xabc0-0xabdf has been reserved
[    0.168303] system 00:0b: ioport range 0xafb0-0xafbb has been reserved
[    0.168307] system 00:0b: ioport range 0xafc0-0xafdf has been reserved
[    0.168312] system 00:0b: ioport range 0xb3b0-0xb3bb has been reserved
[    0.168317] system 00:0b: ioport range 0xb3c0-0xb3df has been reserved
[    0.168322] system 00:0b: ioport range 0xb7b0-0xb7bb has been reserved
[    0.168327] system 00:0b: ioport range 0xb7c0-0xb7df has been reserved
[    0.168332] system 00:0b: ioport range 0xbbb0-0xbbbb has been reserved
[    0.168337] system 00:0b: ioport range 0xbbc0-0xbbdf has been reserved
[    0.168343] system 00:0b: ioport range 0xbfb0-0xbfbb has been reserved
[    0.168352] system 00:0b: ioport range 0xbfc0-0xbfdf has been reserved
[    0.168357] system 00:0b: ioport range 0xc3b0-0xc3bb has been reserved
[    0.168362] system 00:0b: ioport range 0xc3c0-0xc3df has been reserved
[    0.168367] system 00:0b: ioport range 0xc7b0-0xc7bb has been reserved
[    0.168372] system 00:0b: ioport range 0xc7c0-0xc7df has been reserved
[    0.168377] system 00:0b: ioport range 0xcbb0-0xcbbb has been reserved
[    0.168383] system 00:0b: ioport range 0xcbc0-0xcbdf has been reserved
[    0.168388] system 00:0b: ioport range 0xcfb0-0xcfbb has been reserved
[    0.168393] system 00:0b: ioport range 0xcfc0-0xcfdf has been reserved
[    0.168402] system 00:0b: ioport range 0xe3b0-0xe3bb has been reserved
[    0.168407] system 00:0b: ioport range 0xe3c0-0xe3df has been reserved
[    0.168412] system 00:0b: ioport range 0xe7b0-0xe7bb has been reserved
[    0.168417] system 00:0b: ioport range 0xe7c0-0xe7df has been reserved
[    0.168422] system 00:0b: ioport range 0xebb0-0xebbb has been reserved
[    0.168428] system 00:0b: ioport range 0xebc0-0xebdf has been reserved
[    0.168433] system 00:0b: ioport range 0xefb0-0xefbb has been reserved
[    0.168438] system 00:0b: ioport range 0xefc0-0xefdf has been reserved
[    0.168443] system 00:0b: ioport range 0xf3b0-0xf3bb has been reserved
[    0.168449] system 00:0b: ioport range 0xf3c0-0xf3df has been reserved
[    0.168454] system 00:0b: ioport range 0xf7b0-0xf7bb has been reserved
[    0.168459] system 00:0b: ioport range 0xf7c0-0xf7df has been reserved
[    0.168464] system 00:0b: ioport range 0xfbb0-0xfbbb has been reserved
[    0.168470] system 00:0b: ioport range 0xfbc0-0xfbdf has been reserved
[    0.168475] system 00:0b: ioport range 0xffb0-0xffbb has been reserved
[    0.168480] system 00:0b: ioport range 0xffc0-0xffdf has been reserved
[    0.203240] AppArmor: AppArmor Filesystem Enabled
[    0.203290] pci 0000:02:01.0: CardBus bridge, secondary bus 0000:03
[    0.203294] pci 0000:02:01.0:   IO window: 0x00d000-0x00d0ff
[    0.203302] pci 0000:02:01.0:   IO window: 0x00d400-0x00d4ff
[    0.203309] pci 0000:02:01.0:   PREFETCH window: 0x20000000-0x23ffffff
[    0.203317] pci 0000:02:01.0:   MEM window: 0x24000000-0x27ffffff
[    0.203324] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:02
[    0.203329] pci 0000:00:1e.0:   IO window: 0xd000-0xdfff
[    0.203337] pci 0000:00:1e.0:   MEM window: 0xdfd00000-0xdfdfffff
[    0.203344] pci 0000:00:1e.0:   PREFETCH window: 0x20000000-0x23ffffff
[    0.203361] pci 0000:00:1e.0: setting latency timer to 64
[    0.203373] pci 0000:02:01.0: enabling device (0000 -> 0003)
[    0.203385]   alloc irq_desc for 16 on node -1
[    0.203388]   alloc kstat_irqs on node -1
[    0.203397] pci 0000:02:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.203409] pci_bus 0000:00: resource 0 io:  [0x00-0xffff]
[    0.203413] pci_bus 0000:00: resource 1 mem: [0x000000-0xffffffff]
[    0.203417] pci_bus 0000:02: resource 0 io:  [0xd000-0xdfff]
[    0.203421] pci_bus 0000:02: resource 1 mem: [0xdfd00000-0xdfdfffff]
[    0.203425] pci_bus 0000:02: resource 2 pref mem [0x20000000-0x23ffffff]
[    0.203429] pci_bus 0000:02: resource 3 io:  [0x00-0xffff]
[    0.203433] pci_bus 0000:02: resource 4 mem: [0x000000-0xffffffff]
[    0.203437] pci_bus 0000:03: resource 0 io:  [0xd000-0xd0ff]
[    0.203441] pci_bus 0000:03: resource 1 io:  [0xd400-0xd4ff]
[    0.203445] pci_bus 0000:03: resource 2 pref mem [0x20000000-0x23ffffff]
[    0.203449] pci_bus 0000:03: resource 3 mem: [0x24000000-0x27ffffff]
[    0.203507] NET: Registered protocol family 2
[    0.203641] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[    0.204019] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[    0.204157] TCP bind hash table entries: 16384 (order: 5, 131072 bytes)
[    0.204295] TCP: Hash tables configured (established 16384 bind 16384)
[    0.204299] TCP reno registered
[    0.204412] NET: Registered protocol family 1
[    0.204498] Trying to unpack rootfs image as initramfs...
[    0.514597] Freeing initrd memory: 7726k freed
[    0.523368] cpufreq-nforce2: No nForce2 chipset.
[    0.523414] Scanning for low memory corruption every 60 seconds
[    0.523595] audit: initializing netlink socket (disabled)
[    0.523624] type=2000 audit(1257584821.520:1): initialized
[    0.536240] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.538293] VFS: Disk quotas dquot_6.5.2
[    0.538371] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.539144] fuse init (API version 7.12)
[    0.539259] msgmni has been set to 977
[    0.539555] alg: No test for stdrng (krng)
[    0.539572] io scheduler noop registered
[    0.539575] io scheduler anticipatory registered
[    0.539578] io scheduler deadline registered
[    0.539637] io scheduler cfq registered (default)
[    0.539659] pci 0000:00:02.0: Boot video device
[    0.539781] pci 0000:02:08.0: Firmware left e100 interrupts enabled; disabling
[    0.539885] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.539921] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.540628] ACPI: AC Adapter [AC] (on-line)
[    0.540748] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.541403] ACPI: Lid Switch [LID]
[    0.541478] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.541486] ACPI: Power Button [PBTN]
[    0.541547] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.541552] ACPI: Sleep Button [SBTN]
[    0.542086] Marking TSC unstable due to TSC halts in idle
[    0.542123] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    0.542159] processor LNXCPU:00: registered as cooling_device0
[    0.542164] ACPI: Processor [CPU0] (supports 8 throttling states)
[    0.546140] Switched to high resolution mode on CPU 0
[    0.548361] thermal LNXTHERM:01: registered as thermal_zone0
[    0.548374] ACPI: Thermal Zone [THM] (59 C)
[    0.548437] isapnp: Scanning for PnP cards...
[    0.554053] ACPI: Battery Slot [BAT0] (battery absent)
[    0.902699] isapnp: No Plug & Play device found
[    0.904210] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.904724]   alloc irq_desc for 17 on node -1
[    0.904728]   alloc kstat_irqs on node -1
[    0.904738] serial 0000:00:1e.3: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.904747] serial 0000:00:1e.3: PCI INT B disabled
[    0.906052] brd: module loaded
[    0.906682] loop: module loaded
[    0.906788] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    0.906937] ata_piix 0000:00:1f.1: version 2.13
[    0.906951] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.907006] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.907202] scsi0 : ata_piix
[    0.907328] scsi1 : ata_piix
[    0.908127] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    0.908132] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    0.909287] Fixed MDIO Bus: probed
[    0.909336] PPP generic driver version 2.4.2
[    0.909466] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.909491] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.909513] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.909518] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.909585] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    0.913514] ehci_hcd 0000:00:1d.7: debug port 1
[    0.913523] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    0.914059] ata2: port disabled. ignoring.
[    0.914094] ehci_hcd 0000:00:1d.7: irq 16, io mem 0xffa80800
[    0.928015] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.928122] usb usb1: configuration #1 chosen from 1 choice
[    0.928166] hub 1-0:1.0: USB hub found
[    0.928177] hub 1-0:1.0: 8 ports detected
[    0.928275] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.928300] uhci_hcd: USB Universal Host Controller Interface driver
[    0.928343] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.928353] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.928358] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.928399] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    0.928430] uhci_hcd 0000:00:1d.0: irq 16, io base 0x0000bf80
[    0.928544] usb usb2: configuration #1 chosen from 1 choice
[    0.928585] hub 2-0:1.0: USB hub found
[    0.928593] hub 2-0:1.0: 2 ports detected
[    0.928655] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.928664] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.928668] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.928714] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.928758] uhci_hcd 0000:00:1d.1: irq 17, io base 0x0000bf60
[    0.928862] usb usb3: configuration #1 chosen from 1 choice
[    0.928898] hub 3-0:1.0: USB hub found
[    0.928908] hub 3-0:1.0: 2 ports detected
[    0.928978]   alloc irq_desc for 18 on node -1
[    0.928982]   alloc kstat_irqs on node -1
[    0.928991] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.928999] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.929004] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.929045] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.929082] uhci_hcd 0000:00:1d.2: irq 18, io base 0x0000bf40
[    0.929200] usb usb4: configuration #1 chosen from 1 choice
[    0.929236] hub 4-0:1.0: USB hub found
[    0.929246] hub 4-0:1.0: 2 ports detected
[    0.929301]   alloc irq_desc for 19 on node -1
[    0.929304]   alloc kstat_irqs on node -1
[    0.929309] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.929318] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.929323] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.929372] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.929411] uhci_hcd 0000:00:1d.3: irq 19, io base 0x0000bf20
[    0.929515] usb usb5: configuration #1 chosen from 1 choice
[    0.929550] hub 5-0:1.0: USB hub found
[    0.929558] hub 5-0:1.0: 2 ports detected
[    0.929689] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.934269] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.934277] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.934355] mice: PS/2 mouse device common for all mice
[    0.934553] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.934590] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.934739] device-mapper: uevent: version 1.0.3
[    0.934874] device-mapper: ioctl: 4.15.0-ioctl (2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
[    0.934978] device-mapper: multipath: version 1.1.0 loaded
[    0.934982] device-mapper: multipath round-robin: version 1.0.0 loaded
[    0.935146] EISA: Probing bus 0 at eisa.0
[    0.935157] Cannot allocate resource for EISA slot 1
[    0.935196] EISA: Detected 0 cards.
[    0.935325] cpuidle: using governor ladder
[    0.935409] cpuidle: using governor menu
[    0.936099] TCP cubic registered
[    0.936322] NET: Registered protocol family 10
[    0.936921] lo: Disabled Privacy Extensions
[    0.937334] NET: Registered protocol family 17
[    0.937359] Bluetooth: L2CAP ver 2.13
[    0.937362] Bluetooth: L2CAP socket layer initialized
[    0.937366] Bluetooth: SCO (Voice Link) ver 0.6
[    0.937368] Bluetooth: SCO socket layer initialized
[    0.937425] Bluetooth: RFCOMM TTY layer initialized
[    0.937428] Bluetooth: RFCOMM socket layer initialized
[    0.937431] Bluetooth: RFCOMM ver 1.11
[    0.937473] Using IPI No-Shortcut mode
[    0.937561] PM: Resume from disk failed.
[    0.937578] registered taskstats version 1
[    0.937742]   Magic number: 1:573:120
[    0.937747] misc device-mapper: hash matches
[    0.937856] rtc_cmos 00:06: setting system clock to 2009-11-07 09:07:02 UTC (1257584822)
[    0.937861] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.937864] EDD information not available.
[    0.939487] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    1.084947] ata1.00: ATA-6: Hitachi HTS541040G9AT00, MB2OA61A, max UDMA/100
[    1.084952] ata1.00: 78140160 sectors, multi 8: LBA48 
[    1.085010] ata1.01: ATAPI: PHILIPS CD-RW/DVD-ROM SCB5265, TD15, max UDMA/33
[    1.100887] ata1.00: configured for UDMA/100
[    1.116426] ata1.01: configured for UDMA/33
[    1.118947] scsi 0:0:0:0: Direct-Access     ATA      Hitachi HTS54104 MB2O PQ: 0 ANSI: 5
[    1.119130] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.119785] sd 0:0:0:0: [sda] 78140160 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    1.119851] sd 0:0:0:0: [sda] Write Protect is off
[    1.119855] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.119888] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.120084]  sda:
[    1.120221] scsi 0:0:1:0: CD-ROM            PHILIPS  CDRW/DVD SCB5265 TD15 PQ: 0 ANSI: 5
[    1.124028] Clocksource tsc unstable (delta = -129765222 ns)
[    1.139741]  sda1 sda2 sda3 < sda5 >
[    1.177322] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.180709] sr0: scsi3-mmc drive: 4x/24x writer cd/rw xa/form2 cdda tray
[    1.180714] Uniform CD-ROM driver Revision: 3.20
[    1.180808] sr 0:0:1:0: Attached scsi CD-ROM sr0
[    1.180867] sr 0:0:1:0: Attached scsi generic sg1 type 5
[    1.180899] Freeing unused kernel memory: 540k freed
[    1.181312] Write protecting the kernel text: 4568k
[    1.181364] Write protecting the kernel read-only data: 1836k
[    1.366995] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:18/input/input5
[    1.367061] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[    1.367112] ACPI Warning: \_SB_.PCI0.VID2._DOD: Return Package has no elements (empty) 20090521 nspredef-434
[    1.367194] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:1d/input/input6
[    1.367227] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[    1.438614] Linux agpgart interface v0.103
[    1.443677] agpgart-intel 0000:00:00.0: Intel 915GM Chipset
[    1.444175] agpgart-intel 0000:00:00.0: detected 7932K stolen memory
[    1.494624] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xc0000000
[    1.494990] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
[    1.494994] e100: Copyright(c) 1999-2006 Intel Corporation
[    1.495050]   alloc irq_desc for 20 on node -1
[    1.495053]   alloc kstat_irqs on node -1
[    1.495063] e100 0000:02:08.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    1.522487] e100 0000:02:08.0: PME# disabled
[    1.621419] e100: eth0: e100_probe: addr 0xdfdfd000, irq 20, MAC addr 00:12:3f:f7:9e:83
[    1.621487] b43-pci-bridge 0000:02:03.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.621933] [drm] Initialized drm 1.1.0 20060810
[    1.642250] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.642259] i915 0000:00:02.0: setting latency timer to 64
[    2.241997] [drm] DAC-6: set mode 640x480 0
[    2.427784] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[    2.427789] ata1.01: ST_FIRST: !(DRQ|ERR|DF)
[    2.427804] ata1.01: cmd a0/01:00:00:fe:00/00:00:00:00:00/b0 tag 0 dma 16640 in
[    2.427806]          cdb 12 00 00 00 fe 00 00 00  00 00 00 00 00 00 00 00
[    2.427808]          res 50/00:01:00:fe:00/00:00:00:00:00/b0 Emask 0x2 (HSM violation)
[    2.427813] ata1.01: status: { DRDY }
[    2.427924] ata1: soft resetting link
[    2.428324] ssb: Sonics Silicon Backplane found on PCI device 0000:02:03.0
[    2.471192] [drm] TV-14: set mode NTSC 480i 0
[    2.598768] [drm] fb0: inteldrmfb frame buffer device
[    2.598781] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    2.663502] render error detected, EIR: 0x00000010
[    2.663508] page table error
[    2.663510]   PGTBL_ER: 0x00000100
[    2.663514] [drm:i915_handle_error] *ERROR* EIR stuck: 0x00000010, masking
[    2.663523] render error detected, EIR: 0x00000010
[    2.663525] page table error
[    2.663527]   PGTBL_ER: 0x00000100
[    2.674267] [drm] LVDS-8: set mode 1024x768 17
[    3.034718] ata1.00: configured for UDMA/100
[    3.059820] Console: switching to colour frame buffer device 128x48
[    3.068438] ata1.01: configured for UDMA/33
[    3.068747] ata1: EH complete
[    4.029989] EXT4-fs (loop0): barriers enabled
[    4.069525] kjournald2 starting: pid 359, dev loop0:8, commit interval 5 seconds
[    4.069560] EXT4-fs (loop0): delayed allocation enabled
[    4.069566] EXT4-fs: file extents enabled
[    4.070533] EXT4-fs: mballoc enabled
[    4.070557] EXT4-fs (loop0): mounted filesystem with ordered data mode
[    5.410058] type=1505 audit(1257584826.971:2): operation="profile_load" pid=383 name=/usr/share/gdm/guest-session/Xsession
[    5.413625] type=1505 audit(1257584826.974:3): operation="profile_load" pid=384 name=/sbin/dhclient3
[    5.414535] type=1505 audit(1257584826.974:4): operation="profile_load" pid=384 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[    5.415028] type=1505 audit(1257584826.974:5): operation="profile_load" pid=384 name=/usr/lib/connman/scripts/dhclient-script
[    5.467193] type=1505 audit(1257584827.026:6): operation="profile_load" pid=385 name=/usr/bin/evince
[    5.482191] type=1505 audit(1257584827.042:7): operation="profile_load" pid=385 name=/usr/bin/evince-previewer
[    5.490787] type=1505 audit(1257584827.050:8): operation="profile_load" pid=385 name=/usr/bin/evince-thumbnailer
[    5.546146] type=1505 audit(1257584827.106:9): operation="profile_load" pid=387 name=/usr/lib/cups/backend/cups-pdf
[    5.547215] type=1505 audit(1257584827.106:10): operation="profile_load" pid=387 name=/usr/sbin/cupsd
[    5.551410] type=1505 audit(1257584827.110:11): operation="profile_load" pid=388 name=/usr/sbin/tcpdump
[   10.671572] udev: starting version 147
[   11.566655] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   11.668202] lp: driver loaded but no devices found
[   12.081563] dell-wmi: No known WMI GUID found
[   12.347132] intel_rng: FWH not detected
[   12.799755] cfg80211: Calling CRDA to update world regulatory domain
[   12.875546] yenta_cardbus 0000:02:01.0: CardBus bridge found [1028:01a5]
[   12.875575] yenta_cardbus 0000:02:01.0: Using CSCINT to route CSC interrupts to PCI
[   12.875579] yenta_cardbus 0000:02:01.0: Routing CardBus interrupts to PCI
[   12.875587] yenta_cardbus 0000:02:01.0: TI: mfunc 0x00001002, devctl 0x64
[   12.958672] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x8fa0b1, caps: 0xa04713/0x200000
[   12.997876] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   13.104812] yenta_cardbus 0000:02:01.0: ISA IRQ mask 0x0cf8, PCI irq 16
[   13.104820] yenta_cardbus 0000:02:01.0: Socket status: 30000007
[   13.104826] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #03 to #06
[   13.104843] yenta_cardbus 0000:02:01.0: pcmcia: parent PCI bridge I/O window: 0xd000 - 0xdfff
[   13.104849] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xd000-0xdfff: clean.
[   13.105509] yenta_cardbus 0000:02:01.0: pcmcia: parent PCI bridge Memory window: 0xdfd00000 - 0xdfdfffff
[   13.105514] yenta_cardbus 0000:02:01.0: pcmcia: parent PCI bridge Memory window: 0x20000000 - 0x23ffffff
[   13.413640] ip_tables: (C) 2000-2006 Netfilter Core Team
[   14.211343] cfg80211: World regulatory domain updated:
[   14.211349] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   14.211354] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.211358] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.211362] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   14.211366] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.211370] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   14.904374] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   15.286124] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   15.287881] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   15.288639] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   15.289252] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   15.290064] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   15.464497] phy0: Selected rate control algorithm 'minstrel'
[   15.465412] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
[   16.774976] Intel ICH 0000:00:1e.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   16.775041] Intel ICH 0000:00:1e.2: setting latency timer to 64
[   17.600045] intel8x0_measure_ac97_clock: measured 55380 usecs (2668 samples)
[   17.600051] intel8x0: clocking to 48000
[   27.373753] Adding 262136k swap on /host/ubuntu/disks/swap.disk.  Priority:-1 extents:2 across:2783928k 
[   27.479184] EXT4-fs (loop0): internal journal on loop0:8
[   28.113257] type=1505 audit(1257584849.674:12): operation="profile_replace" pid=827 name=/usr/share/gdm/guest-session/Xsession
[   28.116205] type=1505 audit(1257584849.678:13): operation="profile_replace" pid=828 name=/sbin/dhclient3
[   28.117119] type=1505 audit(1257584849.678:14): operation="profile_replace" pid=828 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   28.117619] type=1505 audit(1257584849.678:15): operation="profile_replace" pid=828 name=/usr/lib/connman/scripts/dhclient-script
[   28.125194] type=1505 audit(1257584849.686:16): operation="profile_replace" pid=829 name=/usr/bin/evince
[   28.142797] type=1505 audit(1257584849.702:17): operation="profile_replace" pid=829 name=/usr/bin/evince-previewer
[   28.152360] type=1505 audit(1257584849.714:18): operation="profile_replace" pid=829 name=/usr/bin/evince-thumbnailer
[   28.173985] type=1505 audit(1257584849.734:19): operation="profile_replace" pid=831 name=/usr/lib/cups/backend/cups-pdf
[   28.175143] type=1505 audit(1257584849.734:20): operation="profile_replace" pid=831 name=/usr/sbin/cupsd
[   28.181944] type=1505 audit(1257584849.742:21): operation="profile_replace" pid=832 name=/usr/sbin/tcpdump
[   28.536142] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   28.672781] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[   28.683095] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   28.683103] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   28.683107] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   28.704676] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   29.148072] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   29.155781] b43 ssb0:0: firmware: requesting b43-open/ucode5.fw
[   29.172447] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   29.172533] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   29.172612] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.
[   29.708345] ppdev: user-space parallel port driver
[   30.264677] [drm] DAC-6: set mode 640x480 0
[   30.390004] [drm] DAC-6: set mode 640x480 0
[   30.661089] [drm] TV-14: set mode NTSC 480i 0
[   30.803177] [drm] TV-14: set mode NTSC 480i 0
[   30.951966] [drm] DAC-6: set mode 640x480 0
[   31.070818] [drm] DAC-6: set mode 640x480 0
[   31.326447] [drm] TV-14: set mode NTSC 480i 0
[   31.472466] [drm] TV-14: set mode NTSC 480i 0
[   33.872578] [drm] DAC-6: set mode 640x480 0
[   33.978233] [drm] DAC-6: set mode 640x480 0
[   34.181666] [drm] TV-14: set mode NTSC 480i 0
[   34.322328] [drm] TV-14: set mode NTSC 480i 0
[   34.474638] [drm] DAC-6: set mode 640x480 0
[   34.580591] [drm] DAC-6: set mode 640x480 0
[   34.785036] [drm] TV-14: set mode NTSC 480i 0
[   34.925732] [drm] TV-14: set mode NTSC 480i 0
[   35.074605] [drm] DAC-6: set mode 640x480 0
[   35.180540] [drm] DAC-6: set mode 640x480 0
[   35.385018] [drm] TV-14: set mode NTSC 480i 0
[   35.526779] [drm] TV-14: set mode NTSC 480i 0
[   49.093122] [drm] DAC-6: set mode 640x480 0
[   49.199149] [drm] DAC-6: set mode 640x480 0
[   49.403529] [drm] TV-14: set mode NTSC 480i 0
[   49.543881] [drm] TV-14: set mode NTSC 480i 0
[   49.708712] [drm] DAC-6: set mode 640x480 0
[   49.882360] [drm] DAC-6: set mode 640x480 0
[   50.100813] [drm] TV-14: set mode NTSC 480i 0
[   50.244671] [drm] TV-14: set mode NTSC 480i 0
[   50.427827] [drm] DAC-6: set mode 640x480 0
[   50.546325] [drm] DAC-6: set mode 640x480 0
[   50.752283] [drm] TV-14: set mode NTSC 480i 0
[   50.893698] [drm] TV-14: set mode NTSC 480i 0
[   50.914191] ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[   50.914198] ata1.01: ST_FIRST: !(DRQ|ERR|DF)
[   50.914213] ata1.01: cmd a0/00:00:00:08:00/00:00:00:00:00/b0 tag 0 pio 16392 in
[   50.914216]          cdb 25 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[   50.914218]          res 50/00:01:00:08:00/00:00:00:00:00/b0 Emask 0x2 (HSM violation)
[   50.914223] ata1.01: status: { DRDY }
[   50.914336] ata1: soft resetting link
[   51.100933] ata1.00: configured for UDMA/100
[   51.116391] ata1.01: configured for UDMA/33
[   51.116647] ata1: EH complete
[   52.877953] [drm] DAC-6: set mode 640x480 0
[   53.047310] [drm] DAC-6: set mode 640x480 0
[   53.251127] [drm] TV-14: set mode NTSC 480i 0
[   53.391543] [drm] TV-14: set mode NTSC 480i 0
[  100.944072] usb 1-1: new high speed USB device using ehci_hcd and address 2
[  101.079032] usb 1-1: configuration #1 chosen from 1 choice
[  101.394874] Initializing USB Mass Storage driver...
[  101.395036] scsi2 : SCSI emulation for USB Mass Storage devices
[  101.395283] usbcore: registered new interface driver usb-storage
[  101.395288] USB Mass Storage support registered.
[  101.396579] usb-storage: device found at 2
[  101.396582] usb-storage: waiting for device to settle before scanning
[  106.396324] usb-storage: device scan complete
[  106.397422] scsi 2:0:0:0: Direct-Access     USB 2.0  Flash Disk       PMAP PQ: 0 ANSI: 0 CCS
[  106.398035] sd 2:0:0:0: Attached scsi generic sg2 type 0
[  107.689899] sd 2:0:0:0: [sdb] 2014208 512-byte logical blocks: (1.03 GB/983 MiB)
[  107.690508] sd 2:0:0:0: [sdb] Write Protect is off
[  107.690512] sd 2:0:0:0: [sdb] Mode Sense: 23 00 00 00
[  107.690516] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  107.694254] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  107.694262]  sdb: sdb1
[  107.701278] sd 2:0:0:0: [sdb] Assuming drive cache: write through
[  107.701288] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[  135.557202] usb 1-1: USB disconnect, address 2
[  548.200188] pcmcia: Detected deprecated PCMCIA ioctl usage from process: lshw.
[  548.200195] pcmcia: This interface will soon be removed from the kernel; please expect breakage unless you upgrade to new tools.
[  548.200199] pcmcia: see [http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html](http://www.kernel.org/pub/linux/utils/kernel/pcmcia/pcmcia.html) for details.
[ 1229.442987] sr 0:0:1:0: ioctl_internal_command return code = 8000002
[ 1229.442994]    : Sense Key : No Sense [current] 
[ 1229.443000]    : Add. Sense: No additional sense information


malcburt@ubuntu:~$ sudo lshw -c network
[sudo] password for malcburt: 
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:19 memory:dfdfe000-dfdfffff
  *-network:1
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 03
       serial: 00:12:3f:f7:9e:83
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: irq:20 memory:dfdfd000-dfdfdfff ioport:df40(size=64)
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:3a:fa:fb
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
malcburt@ubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Failed to read scan data : Network is down

malcburt@ubuntu:~$ lsb_release -d
Description:	Ubuntu 9.10
malcburt@ubuntu:~$ uname -mr
2.6.31-14-generic i686
malcburt@ubuntu:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ]


PS: I visited [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and tried following the advice there.  Found that my PCI-ID is 4318 so apparently is supported.  Tried sudo apt-get install b43-fwcutter but it  didn;t prompt me to fetch & install firmware, just said it couldn't find it.

---

### Post by platelunch on 2009-11-07
hey. i had the exact same problem as you. i installed from wubi and ended up with no internet, wired or wireless. i tried a million different things posted on the forums, probably every single thing posted on here about 9.10 and broadcom wireless not working. i ended up finding a driver on the broadcom website and downloaded it onto a usb flashdrive. i rebooted in ubuntu and tried to follow the instuctions that broadcom gave on how to get it to work, but i had to heavily modify the instructions for it to work, and i still have to manually load the driver everytime i reboot, but its only two commands, so its no big deal. its kind of something id have to walk you thru, posting the instructions up here would be very complicated. email me at [email]bob.rojas@gmail.com[/email] if you want me to help you because i dont check back here that often.

---

### Post by malcburt on 2009-11-08
I don't really like the idea of having to fix it again upon every reboot, but might be a last resort.  In the meantime, *Somebody *must have got broadcom drivers working permanently, if that really is my problem?

---

### Post by Methuselah on 2010-01-01
Hi macbert,

It seems that your particular wireless card is not well supported by linux drivers.
Broadcom does not provide linux drivers so the existing support is reverse engineered.
I'm guessing yours is the 4318 listed at this site:
[http://bcm43xx.berlios.de/?go=devices](http://bcm43xx.berlios.de/?go=devices)
And it is said to be 'unstable' and 'work in progress'.

However, the windows drivers for wireless cards can often be made to work in linux using ndiswrapper.
I don't consider this ideal but I have done it once (with a 2wire USB dongle) and it was stable.

Try this link for more info:
[http://www.linuxquestions.org/linux/answers/Networking/How_to_get_Broadcom_43xx_Wireless_AirForce54g_card_to_work_proven_in_Ubuntu_Dappe_Drake](http://www.linuxquestions.org/linux/answers/Networking/How_to_get_Broadcom_43xx_Wireless_AirForce54g_card_to_work_proven_in_Ubuntu_Dappe_Drake)

---

### Post by jamesutk on 2010-02-04
I have the same wireless card and cannot connect. 
Dell 1370 wlan mini-pci 
Chipset:  Broadcom BCM4318 (rev 02) 
[B](AirForce54g)

[/B]I tried the instructions on "http://www.linuxquestions.org/linux/answers/Networking/How_to_get_Broadcom_43xx_Wireless_AirForce54g_card_to_work_proven_in_Ubuntu_Dappe_Drake"  mentioned above. 
When I entered "sudo ndiswrapper -i oem3.inf" it said "couldn't open...no such file or directoryat /usr/sbin/ndiswrapper-1.9 line 219"
Did I do something wrong?

(I am new to linux and would like to get my wireless working)

---

### Post by bkratz on 2010-02-04
> **jamesutk said:**
> I have the same wireless card and cannot connect. 
Dell 1370 wlan mini-pci 
Chipset:  Broadcom BCM4318 (rev 02) 
[B](AirForce54g)

[/B]I tried the instructions on "http://www.linuxquestions.org/linux/answers/Networking/How_to_get_Broadcom_43xx_Wireless_AirForce54g_card_to_work_proven_in_Ubuntu_Dappe_Drake"  mentioned above. 
When I entered "sudo ndiswrapper -i oem3.inf" it said "couldn't open...no such file or directoryat /usr/sbin/ndiswrapper-1.9 line 219"
Did I do something wrong?

(I am new to linux and would like to get my wireless working)




See post #9 of this thread

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

