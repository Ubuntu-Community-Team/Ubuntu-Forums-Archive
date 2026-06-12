---
title: "Ubuntu 9.04 / Linksys WMP54G / old pc prob connecting"
date: 2009-12-28
forum: Networking &amp; Wireless
---

### Post by Tholley on 2009-12-28
I have a new WMP54G wireless adapter installed in an old pc I built for my daughter.
I have not been able to get it to connect with the Linksys WRT54G router.
I found a bunch of stuff about ndiswrapper and installed it, copied the driver off of the install cd, used System, Admin, Windows Wireless Drivers to install, but still will not work.

I read from the HardwareSupportComponents that the adapter should work right out of the box. It is ver. 4.1

So deleted the the driver in said above, and back at square 1, I think...

here are some of the things you might want to look at... (I have it wired right now)

kaylen@kaylen-desktop:~$ lspci
00:00.0 Host bridge: nVidia Corporation nForce2 IGP2 (rev c1)
00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev c1)
00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev c1)
00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev c1)
00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev c1)
00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev c1)
00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a4)
00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a4)
00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller (rev a1)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev c1)
01:04.0 Network controller: RaLink RT2561/RT61 802.11g PCI
02:00.0 VGA compatible controller: nVidia Corporation NV20 [GeForce3 Ti 200] (rev a3)
kaylen@kaylen-desktop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
kaylen@kaylen-desktop:~$ lspci -nn | grep linksys
kaylen@kaylen-desktop:~$ lspci -nn | grep 'linksys'
kaylen@kaylen-desktop:~$ 

As you can tell... I'm a novice when it comes to commands...
I'll add more if I can.

Thanks for any help!

---

### Post by Tholley on 2009-12-28
here is more...

kaylen@kaylen-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0d:87:48:c0:aa  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:87ff:fe48:c0aa/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2777 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1470 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1558235 (1.5 MB)  TX bytes:232021 (232.0 KB)
          Interrupt:22 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

wlan1     Link encap:Ethernet  HWaddr 00:25:9c:7a:4f:32  
          inet6 addr: fe80::225:9cff:fe7a:4f32/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:183 errors:0 dropped:0 overruns:0 frame:0
          TX packets:180 errors:0 dropped:5 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24345 (24.3 KB)  TX bytes:21276 (21.2 KB)
          Interrupt:16 Memory:e0000000-e0008000 

kaylen@kaylen-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11g  ESSID:"thollsys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:66:42:74:98   
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=-121 dBm  
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:100/100  Signal level:-25 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

kaylen@kaylen-desktop:~$

---

### Post by Tholley on 2009-12-28
more...

kaylen@kaylen-desktop:~$ iwconfig wlan1
wlan1     IEEE 802.11g  ESSID:off/any  
          Mode:Auto  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=-121 dBm  
          RTS thr=2347 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

kaylen@kaylen-desktop:~$ lsmod
Module                  Size  Used by
binfmt_misc            16776  1 
bridge                 56212  0 
stp                    10500  1 bridge
bnep                   20224  2 
video                  25872  0 
output                 11008  1 video
input_polldev          11912  0 
lp                     17156  0 
snd_intel8x0           37532  3 
snd_ac97_codec        112292  1 snd_intel8x0
ppdev                  15620  0 
ac97_bus                9856  1 snd_ac97_codec
snd_pcm_oss            46336  0 
snd_mixer_oss          22656  1 snd_pcm_oss
snd_pcm                83076  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy          10756  0 
snd_seq_oss            37760  0 
snd_seq_midi           14336  0 
snd_rawmidi            29696  1 snd_seq_midi
snd_seq_midi_event     15104  2 snd_seq_oss,snd_seq_midi
snd_seq                56880  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29704  2 snd_pcm,snd_seq
snd_seq_device         14988  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ndiswrapper           193436  0 
nvidia               4712596  32 
psmouse                61972  0 
pcspkr                 10496  0 
serio_raw              13444  0 
shpchp                 40212  0 
snd                    62756  16 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         16904  2 snd_intel8x0,snd_pcm
parport_pc             40100  1 
parport                42220  3 lp,ppdev,parport_pc
nvidia_agp             14492  1 
agpgart                42696  2 nvidia,nvidia_agp
i2c_nforce2            14980  0 
forcedeth              61712  0 
floppy                 64324  0 
fbcon                  46112  0 
tileblit               10752  1 fbcon
font                   16384  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
kaylen@kaylen-desktop:~$

---

### Post by Tholley on 2009-12-29
Bump...

Posted like the instructions say, but the guys with the generic subjects ("need help", "cannot connect") seem to be getting all the love. :(

Now I am off to work, so if there are any suggestions, I will certainly try when I get back home to this computer.

Thanks in advance.

---

### Post by Tholley on 2009-12-29
bump again...
 
anybody?

---

