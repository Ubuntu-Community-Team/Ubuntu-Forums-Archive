---
title: "BCM4306 (rev 02), Ubuntu 9.10, Dell X300, All atempts to activate wireless failed"
date: 2010-06-13
forum: Networking &amp; Wireless
---

### Post by The Flying Penguin on 2010-06-13
I am trying to get wireless to work on a friend's Dell Latitude X300 with the BCM4306 (rev 02) under Ubuntu 9.10. This actually used to be my laptop before I sold it to him and I did in fact have wireless working using ndiswrapper, although I can't remember which version of Ubuntu I had running.

Here is what I have tried after installing the updates of course:

1) I tried using ndisgtk to install the XP driver but it said that no hardware was detected.
2) I tried using the hardware driver utility under administration to activate the propriatary drivers but after clicking activate, it would just keep saying downloading and nothing would ever happen, even after sitting all night. I had the ethernet plugged in and the Ubuntu disc in the drive (it was added to software sources).
3) I tried installing the bcmwl-kernel-source from Synaptic.
4) I tried installing and running b43-fwcutter and installing the firmware it installs.

None of that worked. I tried using the keyboard hotkey to turn the wifi on after every attempted fix.

Then I found this post: [http://forum.linuxmint.com/viewtopic.php?f=53&t=35393&start=0](http://forum.linuxmint.com/viewtopic.php?f=53&t=35393&start=0)

Now that claims that this exact card should work under 9.10 using WICD. So I installed that in place of the gnome network manager. Still no go. It says "no wireless networks found". I even tried reinstalling 9.10 and all the updates in case I messed something up. WICD still says the same thing.

Running the command "sudo ifconfig wlan0 up" gives me the error "SIOCSIFFLAGS: No such file or directory".

So now I am running on a fresh install of 9.10 with all updates applied and WICD installed in place of the gnome network manager.

Anyway, here are the things the thread "How to post a wireless issue" said to include. Let me know if I left something out. I couldn't get grep to work right so I just had to try to figure out what was relevant.

1 ) Machine Brand and Model (PC/Laptop):
Dell Latitude X300 Laptop

2 ) Wireless Brand, Model and Wireless Chipset:
```
02:04.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
02:05.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
```3 ) check interface:
ifconfig
```
dustin@dustin-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0d:56:b7:b5:b6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

```And iwconfig
```

dustin@dustin-laptop:~$ iwconfig
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

```4 ) Check for modules:
Sorry, wasn't sure exactly what information to cut out of this so I included the whole thing. I'm assuming the b43 listings are the relevant information but I didn't want to leave anything out.
```
dustin@dustin-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6464  0 
arc4                    1660  2 
ecb                     2524  2 
snd_rawmidi            22176  1 snd_seq_midi
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
pcmcia                 36808  0 
joydev                 10240  0 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
b43legacy             117784  0 
x_tables               16544  1 ip_tables
yenta_socket           24296  2 
snd_timer              22276  2 snd_pcm,snd_seq
mac80211              181140  1 b43legacy
cfg80211               93052  2 b43legacy,mac80211
led_class               4096  1 b43legacy
rsrc_nonstatic         11644  1 yenta_socket
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcmcia_core            36592  3 pcmcia,yenta_socket,rsrc_nonstatic
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                57332  0 
soundcore               7264  1 snd
shpchp                 32272  0 
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
serio_raw               5280  0 
irda                  189564  0 
ppdev                   6688  0 
dell_wmi                2564  0 
crc_ccitt               1852  1 irda
parport_pc             31940  1 
dcdbas                  7292  0 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
usb_storage            52768  1 
i915                  226120  3 
drm                   160032  3 i915
i2c_algo_bit            5760  1 i915
tg3                   109632  0 
ssb                    35524  1 b43legacy
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
video                  19380  1 i915
output                  2780  1 video
intel_agp              27676  2 i915
agpgart                34988  2 drm,intel_agp

```5 ) Kernel boot messages

```

o4/input/input7
[   10.460458] yenta_cardbus 0000:02:03.1: ISA IRQ mask 0x0018, PCI irq 10
[   10.460465] yenta_cardbus 0000:02:03.1: Socket status: 30000006
[   10.460472] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #06 to #0a
[   10.460510] yenta_cardbus 0000:02:03.1: pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[   10.460516] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3000-0x3fff: clean.
[   10.460896] yenta_cardbus 0000:02:03.1: pcmcia: parent PCI bridge Memory window: 0xe0200000 - 0xe02fffff
[   10.460902] yenta_cardbus 0000:02:03.1: pcmcia: parent PCI bridge Memory window: 0x28000000 - 0x2fffffff
[   10.492179] cfg80211: World regulatory domain updated:
[   10.492186]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.492191]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.492196]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.492201]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.492206]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.492211]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.525320] b43legacy-phy0: Broadcom 4306 WLAN found
[   10.573426] b43legacy-phy0 debug: Found PHY: Analog 1, Type 2, Revision 1
[   10.573450] b43legacy-phy0 debug: Found Radio: Manuf 0x17F, Version 0x2050, Revision 2
[   10.600056] b43legacy-phy0 debug: Radio initialized
[   10.834805] ip_tables: (C) 2000-2006 Netfilter Core Team
[   10.909290] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   10.910154] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   10.910548] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   10.910888] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   10.911422] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   11.040085] phy0: Selected rate control algorithm 'minstrel'
[   11.041365] Broadcom 43xx-legacy driver loaded [ Features: PLID, Firmware-ID: FW10 ]
[   11.089309] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x100-0x3af: clean.
[   11.090173] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[   11.090569] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff: clean.
[   11.090909] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7: clean.
[   11.091444] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: clean.
[   11.719344] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 10 (level, low) -> IRQ 10
[   11.719393] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   12.544053] intel8x0_measure_ac97_clock: measured 54958 usecs (2648 samples)
[   12.544059] intel8x0: clocking to 48000
[   14.415249] type=1505 audit(1276446760.993:12): operation="profile_replace" pid=907 name=/usr/share/gdm/guest-session/Xsession
[   14.418514] type=1505 audit(1276446760.997:13): operation="profile_replace" pid=908 name=/sbin/dhclient3
[   14.419576] type=1505 audit(1276446760.997:14): operation="profile_replace" pid=908 name=/usr/lib/NetworkManager/nm-dhcp-client.action
[   14.420205] type=1505 audit(1276446761.001:15): operation="profile_replace" pid=908 name=/usr/lib/connman/scripts/dhclient-script
[   14.430096] type=1505 audit(1276446761.009:16): operation="profile_replace" pid=909 name=/usr/bin/evince
[   14.448897] type=1505 audit(1276446761.029:17): operation="profile_replace" pid=909 name=/usr/bin/evince-previewer
[   14.459739] type=1505 audit(1276446761.037:18): operation="profile_replace" pid=909 name=/usr/bin/evince-thumbnailer
[   14.474387] type=1505 audit(1276446761.053:19): operation="profile_replace" pid=911 name=/usr/lib/cups/backend/cups-pdf
[   14.475632] type=1505 audit(1276446761.053:20): operation="profile_replace" pid=911 name=/usr/sbin/cupsd
[   14.479968] type=1505 audit(1276446761.057:21): operation="profile_replace" pid=912 name=/usr/sbin/tcpdump
[   15.306788] ttyS1: LSR safety check engaged!
[   17.715829] [drm] DAC-6: set mode 640x480 0
[   18.213518] [drm] DAC-6: set mode 640x480 0
[   18.807472] [drm] DAC-6: set mode 640x480 0
[   19.299635] [drm] DAC-6: set mode 640x480 0
[   23.272053] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw
[   23.681368] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[   23.681378] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).
[   27.541739] [drm] DAC-6: set mode 640x480 0
[   28.033077] [drm] DAC-6: set mode 640x480 0
[   28.632436] [drm] DAC-6: set mode 640x480 0
[   29.124231] [drm] DAC-6: set mode 640x480 0
[   29.744512] [drm] DAC-6: set mode 640x480 0
[   30.235993] [drm] DAC-6: set mode 640x480 0
[   32.514138] tg3 0000:02:05.0: firmware: requesting tigon/tg3_tso5.bin
[   32.592765] tg3 0000:02:05.0: wake-up capability disabled by ACPI
[   32.592774] tg3 0000:02:05.0: PME# disabled
[   32.940228] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   34.462078] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   34.462084] tg3: eth0: Flow control is on for TX and on for RX.
[   34.462413] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   35.304041] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw
[   35.310103] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[   35.310114] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).
[   35.656040] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw
[   35.660798] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[   35.660808] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).
[   36.040410] tg3 0000:02:05.0: PME# enabled
[   36.040438] tg3 0000:02:05.0: wake-up capability enabled by ACPI
[   36.251117] tg3 0000:02:05.0: wake-up capability disabled by ACPI
[   36.251127] tg3 0000:02:05.0: PME# disabled
[   36.589807] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   38.166831] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   38.166837] tg3: eth0: Flow control is on for TX and on for RX.
[   38.167153] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   48.344131] eth0: no IPv6 routers present
[  125.859577] [drm] DAC-6: set mode 640x480 0
[  126.352214] [drm] DAC-6: set mode 640x480 0
[  126.957884] [drm] DAC-6: set mode 640x480 0
[  127.462516] [drm] DAC-6: set mode 640x480 0
[  128.062392] [drm] DAC-6: set mode 640x480 0
[  128.553885] [drm] DAC-6: set mode 640x480 0
[  131.546252] [drm] DAC-6: set mode 640x480 0
[  132.038661] [drm] DAC-6: set mode 640x480 0
[  171.613068] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw
[  171.622824] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[  171.622834] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).
[  193.748166] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw
[  193.757321] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[  193.757337] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).
[  197.680035] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw
[  197.686648] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[  197.686660] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).
[  511.549539] tg3: eth0: Link is down.
[  516.904539] tg3 0000:02:05.0: PME# enabled
[  516.904583] tg3 0000:02:05.0: wake-up capability enabled by ACPI
[  516.928893] tg3 0000:02:05.0: wake-up capability disabled by ACPI
[  516.928902] tg3 0000:02:05.0: PME# disabled
[  517.246113] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  517.468073] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw
[  517.477609] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[  517.477619] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).
[  517.744180] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw
[  517.754433] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[  517.754441] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).
[  523.652063] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw
[  523.661271] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[  523.661288] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).
[  528.656167] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw
[  528.665345] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[  528.665361] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).
[  728.652173] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw
[  728.664969] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[  728.664979] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).
[  933.660073] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw
[  933.672870] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[  933.672880] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).
[ 1138.664169] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw
[ 1138.677639] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[ 1138.677655] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).
[ 1343.696161] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw
[ 1343.725608] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[ 1343.725625] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).
[ 1548.656064] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw
[ 1548.669524] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[ 1548.669540] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).
[ 1631.460078] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw
[ 1631.469947] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[ 1631.469981] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).
[ 2069.244177] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw
[ 2069.253143] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[ 2069.253159] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).
[ 2279.676175] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw
[ 2279.686042] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[ 2279.686058] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).
[ 2484.656167] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw
[ 2484.669698] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[ 2484.669715] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).
[ 2684.656194] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw
[ 2684.665475] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[ 2684.665491] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).
[ 2889.656071] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw
[ 2889.665356] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[ 2889.665372] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).

```6 ) Network configuration
```

dustin@dustin-laptop:~$ sudo lshw -C network
[sudo] password for dustin: 
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 4
       bus info: pci@0000:02:04.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:5 memory:e0210000-e0211fff
  *-network:1
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth0
       version: 01
       serial: 00:0d:56:b7:b5:b6
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=5705-v3.16 latency=64 link=no mingnt=64 multicast=yes port=twisted pair speed=100MB/s
       resources: irq:11 memory:e0200000-e020ffff
  *-network DISABLED
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:90:4b:6f:f1:76
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg

```7 ) Scan for networks:
```
wlan0     Failed to read scan data : Network is down
```8 ) Ubuntu Version: 
Ubuntu 9.10

9 ) Kernel/architecture (including 32 vs. 64 bit): 
2.6.31-22-generic i686
(I'm not sure why it says i686, it should be i386?)

10 ) Restarting the network:
```
 * Reconfiguring network interfaces...                                   [ OK ] 

```

---

### Post by purelinuxuser on 2010-06-13
> **The Flying Penguin said:**
> 
4) I tried installing and running b43-fwcutter and installing the firmware it installs.


> **The Flying Penguin said:**
> 
```

[  132.038661] [drm] DAC-6: set mode 640x480 0
[  171.613068] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw
[  171.622824] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[  171.622834] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).
[  193.748166] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw
[  193.757321] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[  193.757337] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).
[  197.680035] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw
[  197.686648] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[  197.686660] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).
[  511.549539] tg3: eth0: Link is down.
[  516.904539] tg3 0000:02:05.0: PME# enabled
[  516.904583] tg3 0000:02:05.0: wake-up capability enabled by ACPI
[  516.928893] tg3 0000:02:05.0: wake-up capability disabled by ACPI
[  516.928902] tg3 0000:02:05.0: PME# disabled
[  517.246113] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  517.468073] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw
[  517.477609] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[  517.477619] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).
[  517.744180] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw
[  517.754433] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[  517.754441] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).
[  523.652063] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw
[  523.661271] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[  523.661288] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).
[  528.656167] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw
[  528.665345] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[  528.665361] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).
[  728.652173] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw
[  728.664969] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[  728.664979] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).
[  933.660073] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw
[  933.672870] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[  933.672880] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).
[ 1138.664169] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw
[ 1138.677639] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[ 1138.677655] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).
[ 1343.696161] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw
[ 1343.725608] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[ 1343.725625] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).
[ 1548.656064] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw
[ 1548.669524] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[ 1548.669540] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).
[ 1631.460078] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw
[ 1631.469947] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[ 1631.469981] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).
[ 2069.244177] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw
[ 2069.253143] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[ 2069.253159] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).
[ 2279.676175] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw
[ 2279.686042] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[ 2279.686058] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).
[ 2484.656167] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw
[ 2484.669698] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[ 2484.669715] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).
[ 2684.656194] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw
[ 2684.665475] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[ 2684.665491] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).
[ 2889.656071] b43legacy ssb0:0: firmware: requesting b43legacy/ucode4.fw
[ 2889.665356] b43legacy-phy0 ERROR: Firmware file "b43legacy/ucode4.fw" not found or load failed.
[ 2889.665372] b43legacy-phy0 ERROR: You must go to http://linuxwireless.org/en/users/Drivers/b43#devicefirmware and download the correct firmware (version 3).

```

Hmm... you say you installed b43-fwcutter and its relevant firmware, but your logs tell a different story. Plug into Ethernet, install (or reinstall) b43-fwcutter from Synaptic and you'll get a prompt with a checkbox that says, "Automatically download and install firmware?" be sure it is **checked**.  Then reboot.

Good luck ;)

---

### Post by The Flying Penguin on 2010-06-14
Yeah, I did install it and it didn't work. I tried the methods that I posted above on the same install as well. The logs I posted are from a clean install. I figured after all the monkeying around I did that a fresh install may help.

Since fwcutter didn't work last time I kind of just ignored the message about needing firmware. Anyway, I shouldn't have ignored it because this time around fwcutter worked! The wireless is working great now!

I figured since it didn't work last time that it wouldn't this time. I wish I had copied the logs before the reinstall to see what the conflict was. Oh well, thank you very much! My friend will be very happy now.

---

