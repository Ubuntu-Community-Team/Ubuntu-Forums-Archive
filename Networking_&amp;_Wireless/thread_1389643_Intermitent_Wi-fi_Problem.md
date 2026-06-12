---
title: "Intermitent Wi-fi Problem"
date: 2010-01-24
forum: Networking &amp; Wireless
---

### Post by ZootHornRollo on 2010-01-24
Hi,

I have an issue with my Wifi connection where by it will cut out intermittently.  This set up worked flawlessly for over a year but suddenly i strated getting problems.  I have two PC's with the same wifi card - one of them failed totally and is now connected to the router via cable. The other is the PC i am now having problems with.

There is often a pattern to it - pinging the router in terminal, it will ping back for 10 seconds and then stop for 30 seconds - but even that is intermittent, sometimes there is no pattern to it, but it consistently goes down for around 30 seconds each time.

Initially i had suspected it was the router - that has now been replaced.  Then i thought some kind of outside interference so i tried unplugging electrical items around the house but nothing changed - obviously i can't rule out the neighbours.  However, pinging the router from my Nokia N900 via wifi, i can consistently ping with no break in the signal even when the pc is not able to.  I can even go several yards to the other side of the pc and still get no drop out.  So i am now considering it may be the wifi card.

```
graham@lodainn:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 01
       serial: 00:1d:60:76:0e:1d
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
       resources: irq:28 ioport:a800(size=256) memory:fe9ff000-fe9fffff memory:fe9c0000-fe9dffff(prefetchable)
  *-network
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 2
       bus info: pci@0000:05:02.0
       logical name: wmaster0
       version: 00
       serial: 00:0e:2e:45:42:fb
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci ip=192.168.0.2 latency=64 multicast=yes wireless=IEEE 802.11bg
       resources: irq:23 memory:feaf0000-feaf7fff
graham@lodainn:~$   lspci -v | grep subordinate
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
	Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
graham@lodainn:~$ lspci
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801H (ICH8 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G73 [GeForce 7600 GT] (rev a1)
02:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 AHCI Controller (rev 03)
02:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 AHCI Controller (rev 03)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
05:00.0 USB Controller: NEC Corporation USB (rev 43)
05:00.1 USB Controller: NEC Corporation USB (rev 43)
05:00.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
05:01.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
05:01.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
05:01.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port
05:02.0 Network controller: RaLink RT2561/RT61 802.11g PCI

```

```
graham@lodainn:~$ iwconfig wlan0
wlan0     IEEE 802.11bg  ESSID:"SKY54186"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:24:B2:4B:3C:70   
          Bit Rate=54 Mb/s   Tx-Power=11 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=60/70  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

```
graham@lodainn:~$ lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
snd_emu10k1_synth       6108  0 
snd_emux_synth         32860  1 snd_emu10k1_synth
snd_seq_virmidi         5628  1 snd_emux_synth
snd_seq_midi_emul       6332  1 snd_emux_synth
snd_emu10k1           135136  3 snd_emu10k1_synth
snd_ac97_codec        101216  1 snd_emu10k1
ac97_bus                1532  1 snd_ac97_codec
arc4                    1660  2 
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
ecb                     2524  2 
snd_page_alloc          9156  2 snd_emu10k1,snd_pcm
snd_util_mem            4156  2 snd_emux_synth,snd_emu10k1
snd_hwdep               7200  2 snd_emux_synth,snd_emu10k1
rt61pci                20576  0 
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
crc_itu_t               1852  1 rt61pci
snd_rawmidi            22208  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
rt2x00pci               7900  1 rt61pci
snd_seq_midi_event      6940  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
rt2x00lib              29756  2 rt61pci,rt2x00pci
snd_seq                50224  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
led_class               4096  1 rt2x00lib
snd_timer              22276  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device          6920  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
input_polldev           3716  1 rt2x00lib
ppdev                   6688  0 
iptable_filter          3100  0 
snd                    59204  17 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              181140  2 rt2x00pci,rt2x00lib
lp                      8964  0 
parport_pc             31940  1 
soundcore               7264  1 snd
ip_tables              11692  1 iptable_filter
emu10k1_gp              2492  0 
cfg80211               93052  2 rt2x00lib,mac80211
gameport               11368  2 emu10k1_gp
x_tables               16544  1 ip_tables
usblp                  12636  0 
eeprom_93cx6            1916  1 rt61pci
nvidia               9586440  36 
parport                35340  3 ppdev,lp,parport_pc
psmouse                56500  0 
serio_raw               5280  0 
joydev                 10240  0 
asus_atk0110            8252  0 
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
usbhid                 38208  0 
ohci1394               29900  0 
floppy                 54916  0 
ieee1394               86596  1 ohci1394
r8169                  32064  0 
mii                     5212  1 r8169
intel_agp              27484  0 
agpgart                34988  2 nvidia,intel_agp

```

```
graham@lodainn:~$ sudo lshw -C network
[sudo] password for graham: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 01
       serial: 00:1d:60:76:0e:1d
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:28 ioport:a800(size=256) memory:fe9ff000-fe9fffff memory:fe9c0000-fe9dffff(prefetchable)
  *-network
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 2
       bus info: pci@0000:05:02.0
       logical name: wmaster0
       version: 00
       serial: 00:0e:2e:45:42:fb
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci ip=192.168.0.2 latency=64 multicast=yes wireless=IEEE 802.11bg
       resources: irq:23 memory:feaf0000-feaf7fff

```

```
graham@lodainn:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:24:B2:4B:3C:70
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=56/70  Signal level=-54 dBm  
                    Encryption key:on
                    ESSID:"SKY54186"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001d549f3a1c9
                    Extra: Last beacon: 160ms ago
                    IE: Unknown: 0008534B593534313836
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00

```

```
graham@lodainn:~$ lsb_release -d
Description:	Ubuntu 9.10

```

```
graham@lodainn:~$ uname -mr
2.6.31-17-generic i686

```

First time :
```
graham@lodainn:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface wlan0=wlan0.

```

Second time :
```
graham@lodainn:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ]
```

Last bit is maybe of interest?  First ime i ran it i got 'Ignoring unknown interface wlan0=wlan0.'  second time i didn't.

Any advise appreciated.

---

### Post by ZootHornRollo on 2010-01-25
bump

---

### Post by ZootHornRollo on 2010-01-25
i have added :

```
auto wlan0
iface wlan0 inet dhcp
wireless-power off
```

to /etc/network/interfaces

seems to have done the trick.

---

### Post by claracc on 2010-01-26
I have had a similar problem last week. After three months fully working (with wicd, network manager doesn work), wifi stopped working.

It connected and disconnected all the time, [http://ubuntuforums.org/showthread.php?t=1385932](http://ubuntuforums.org/showthread.php?t=1385932).

Nobody could give me an answer, but the problem fixed doing the following (or fixed itself, i don't know):

Install software package hostapd
Updating to python 2.5 (2.5.4-1ubuntu6.1)
Updating phyton 2.5-minimal (2.5.4-1ubuntu6.1)

So i think, some of security or recommended updates were the cause of the problem ???.

Any information is very welcome.

---

