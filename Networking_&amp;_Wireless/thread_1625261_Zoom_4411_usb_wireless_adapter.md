---
title: "Zoom 4411 usb wireless adapter"
date: 2010-11-18
forum: Networking &amp; Wireless
---

### Post by doug_a on 2010-11-18
I have a Zoom 4411 USB Wireless-N adapter which uses the Ralink rt2870 chipset.  I've installed the Windows XP drivers to run under ndiswrapper, but see no wlan0 device.  Any help in configuring this adapter would be appreciated.  Relevant related information is as follows:

doug@ubuntu01:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 148f:3070 Ralink Technology, Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

doug@ubuntu01:~$ lsb_release -d
Description:    Ubuntu 10.04.1 LTS
doug@ubuntu01:~$ uname -mr
2.6.32-25-generic i686

doug@ubuntu01:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0b:cd:00:90:6b  
          inet addr:192.168.1.107  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:cdff:fe00:906b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3180 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1372 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1809426 (1.8 MB)  TX bytes:234714 (234.7 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

doug@ubuntu01:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

doug@ubuntu01:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
snd_intel8x0           25588  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_seq_dummy           1338  0 
vga16fb                11385  1 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
vgastate                8961  1 vga16fb
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
i915                  286079  1 
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
drm_kms_helper         29297  1 i915
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
drm                   162409  3 i915,drm_kms_helper
snd                    54148  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit            5028  1 i915
ppdev                   5259  0 
psmouse                63245  0 
lp                      7060  0 
video                  17375  1 i915
intel_agp              24119  2 i915
parport_pc             25962  1 
soundcore               6620  1 snd
ndiswrapper           184677  0 
serio_raw               3978  0 
parport                32635  3 ppdev,lp,parport_pc
shpchp                 28820  0 
output                  1871  1 video
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
agpgart                31724  3 drm,intel_agp
e100                   28211  0 
mii                     4381  1 e100
floppy                 53016  0 

doug@ubuntu01:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
rt2870 : driver installed
    device (148F:3070) present (alternate driver: rt2800usb)

doug@ubuntu01:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82801DB PRO/100 VM (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:05:08.0
       logical name: eth0
       version: 81
       serial: 00:0b:cd:00:90:6b
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.107 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: irq:20 memory:fc500000-fc500fff ioport:1000(size=64)

doug@ubuntu01:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
wlan0: ERROR while getting interface flags: No such device
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; No such device.
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.

dmesg 

[   13.712042] usb 1-1: reset high speed USB device using ehci_hcd and address 2
[   13.950492] [drm] i915 disabling kernel modesetting for known bad device.
[   13.950532] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.950541] pci 0000:00:02.0: setting latency timer to 64
[   13.984583] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   14.005627] input: ImExPS/2 Logitech Explorer Mouse as /devices/platform/i8042/serio1/input/input4
[   14.060495] ndiswrapper (import:242): unknown symbol: ntoskrnl.exe:'MmGetSystemRoutineAddress'
[   14.060880] ndiswrapper (load_sys_files:206): couldn't prepare driver 'rt2870'
[   14.061995] ndiswrapper (load_wrap_driver:108): couldn't load driver rt2870; check system log for messages from 'loadndisdriver'
[   14.062130] usbcore: registered new interface driver ndiswrapper

---

### Post by uncaspi on 2010-11-18
What says dmesg | grep Net

---

### Post by doug_a on 2010-11-19
doug@ubuntu01:~$ dmesg | grep Net
[    0.104568] NetLabel: Initializing
[    0.104572] NetLabel:  domain hash size = 128
[    0.104574] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.104596] NetLabel:  unlabeled traffic allowed by default
[    1.346322] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
[   13.382421] type=1505 audit(1290130715.579:3):  operation="profile_load" pid=471 name="/usr/lib/NetworkManager/nm-dhcp-client.action"
[   14.162646] type=1505 audit(1290130716.359:7):  operation="profile_replace" pid=619 name="/usr/lib/NetworkManager/nm-dhcp-client.action"

---

### Post by uncaspi on 2010-11-19
Maybe you should have a look on this thread.

[http://ubuntuforums.org/showthread.php?t=31926](http://ubuntuforums.org/showthread.php?t=31926)

---

### Post by pdc on 2010-11-19
the driver for the 2870 is built in to the kernel; 

I suspect this is the correct path for you

[http://ubuntuforums.org/showthread.php?t=1342593](http://ubuntuforums.org/showthread.php?t=1342593)

the post advises blacklisting the 2800usb driver

but as you have installed ndiswrapper you will also need to blacklist that; 

I suspect the command is 

> sudo gedit /etc/modprobe.d/blacklist

and you add ndiswrapper as a line in that; however you may wish to check or have others comment

see post #18 here

[http://newyork.ubuntuforums.org/showthread.php?t=1095349&page=2](http://newyork.ubuntuforums.org/showthread.php?t=1095349&page=2)

---

### Post by doug_a on 2010-11-19
Thanks to you all!

I uninstalled ndiswrapper and blacklisted rt2800usb as indicated in the links.  Rebooted and the adapter found the Access Point and connected:

doug@ubuntu01:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     RTxx70 Wireless  ESSID:"107407"  Nickname:"RT3070STA"
          Mode:Managed  Frequency=2.452 GHz  Access Point: 68:7F:74:DD:DD:B9   
          Bit Rate=54 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=100/100  Signal level:-19 dBm  Noise level:-83 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

I disconnected the wired (eth0) connection, rebooted, and am now running completely on the wireless connection:

doug@ubuntu01:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0b:cd:00:90:6b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:40:36:3c:39:89  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:36ff:fe3c:3989/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9659 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2775 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4072871 (4.0 MB)  TX bytes:386960 (386.9 KB)

---

### Post by pdc on 2010-11-20
great work! Enjoy!

---

